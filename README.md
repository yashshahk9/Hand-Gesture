# Hand-Gesture
 Hand Gesture recognition is a type of perceptual computing user interface that allows computers to capture and interpret human gestures as commands. The general definition of gesture recognition is the ability of a computer to understand gestures and execute commands based on those gestures.
import handy
import cv2

cap = cv2.VideoCapture(0)
hist = handy.capture_histogram(source=0)

while True:
    ret, frame = cap.read()
    
    # detect the hand
    hand = handy.detect_hand(frame, hist)
    
    # plot the fingertips
    for fingertip in hand.fingertips:
        cv2.circle(hand.outline, fingertip, 5, (0, 0, 255), -1)

    cv2.imshow("Handy", hand.outline)
    
    k = cv2.waitKey(5)
    if k == ord('q'):
        break
