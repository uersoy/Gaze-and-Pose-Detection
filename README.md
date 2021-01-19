# Gaze-and-Pose-Detection

Please refer to https://hub.docker.com/repository/docker/uersoy/combined_gaze_pose_image to pull the docker image.

This image combines Nvidia pose and gaze demo into a single image with both running simultaneously using one camera.

This image works seamlessly for Nvidia Jetson Xavier Nx (I haven't yet treid with other Jetson devices).

Ensure the below prerequisites are available on your system:

a) Jetson device running L4T r32.4.2 or

b) JetPack 4.4 Developer Preview (DP)

Instructions:

After pulling the image, run it on your device by mounting your camera devices similar to below:

sudo xhost +si:localuser:root

sudo docker run --runtime nvidia -it --network host -e DISPLAY=$DISPLAY --device=/dev/video1:/dev/video1 --device=/dev/video0:/dev/video0 -v /tmp/.X11-unix/:/tmp/.X11-unix uersoy/combined_gaze_pose_image:1

All the code is in the container under gaze directory (cd gaze)

To test the combined gaze / pose live demo with your camera, run the following at the command line:

python3 run_combined_sequential-cam.py

Or you can separately run gaze and pose live demo with your camera device using the following:

python3 run_gaze_sequential-cam.py

python3 run_pose_sequential-cam.py

Contact me if you have trouble running it. I would like to know what interesting projects you are working on :)


