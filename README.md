#Vehicle Counting using YOLOv5
This project aims to count vehicles in a video using the YOLOv5 object detection model. The vehicles are counted as they cross a predefined line in the video frame.

Requirements:
OpenCV (cv2)
PyTorch (torch)
NumPy (numpy)
moviepy (VideoFileClip)
How it works:
Loading the YOLOv5 Model: The YOLOv5 model is loaded using PyTorch's hub. The model is used to detect vehicles in each frame of the video.

Processing the Video: The video is read frame by frame. For each frame:

Vehicles are detected using the YOLOv5 model.
The center of each detected vehicle is calculated.
The vehicle's center is matched with the previous frame's detections to track the vehicle.
A counting line is drawn on the frame. When a vehicle crosses this line, it is counted.
Saving the Processed Video: The processed video, with bounding boxes around detected vehicles, vehicle IDs, and the counting line, is saved to disk.

Displaying the Processed Video: The saved video is displayed using moviepy.

Usage:
Simply run the provided Python script. Ensure that the path to the input video is correctly specified in the cv2.VideoCapture function. The processed video will be saved to the specified path and then displayed.

Configuration:
line_position: The Y-coordinate of the counting line. Adjust this value based on where you want to count the vehicles in the video frame.
current_detections: A list that keeps track of the current frame's vehicle detections.
car_count: A counter for the number of cars detected.
car_ids: A list to keep track of the unique IDs of detected cars.
current_id: An ID counter to assign a unique ID to each detected car.
Note:
The class ID for cars is assumed to be 2. Adjust this if your model uses a different class ID for cars.
The threshold distance for matching vehicle detections between frames is set to 50. Adjust this value based on the video's resolution and the speed of vehicles.
