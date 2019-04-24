#Multi-Lane Detection Dataset with Ground Truth

##Data Description
This dataset is a multi-lane detection dataset, which can be used to test and evaluate multiple lane detection algorithms. It is collected by a road-facing traffic recorder in some sections of Jiqing (Jinan-Qingdao) expressway, China, and the lanes are annotated with a semi-manual method (described below). There are 40 video clips in the dataset, each of which lasts 3 minutes and has a frame rate of 30 fps, and the video resolution is 1920×1080. A total of 211,837 road images with different illumination intensity and different road conditions (upstream, downhill, tunnel, culvert, ramp, etc.) are included. 

In addition, we label the lanes in each frame and save the labeling results as a txt file. The key feature points coordinates (x,y) of different lanes are stored in different rows, and lane "x" (x = 0, 1, 2, 3,...) is used to represent the lane serial number.

![Fig.1.txt sample](https://i.imgur.com/yEzOYPS.png)

 The results of lane annotation are shown in Figure 1 below.

![Fig.2.Relults of lane annotation](https://i.imgur.com/nkoJRA0.jpg)

The dataset is constructed by integrating both automatic identification and manual annotation. The automatic identification module is implemented with C++ and opencv library. The flow chart of lane extraction is shown in Fig.3. The specific steps are as follows:

![Fig.3. Flow chart of lane extraction](https://i.imgur.com/Xgx6VNa.png)

1．	Load the video or image and mark the initial position of ROI manually for the initial frame.
 
2．	Apply Gauss smoothing to the image in ROI. According to the perspective relationship, the Gauss kernel decreases gradually from near to far. Therefore, the gray value of the edge of the lane line in the smoothed image is lower and the gray value of the center skeleton is higher.

3．	Perform non-maximum suppression on the smoothed image to extract the lane skeleton. 

4．	Use segmental least squares fitting for the pixel points of the lane skeleton. Cubic or quadratic fitting is used for the curve lane, and linear fitting is used for the straight line.

5．	If the fitting results are in agreement with the test results, the fitting results are stored by sampling in segments and served as the basis for determining the ROI of the next frame. Otherwise, the frame is re-labeled manually.

#Download
We have uploaded the lane data file and the original video to Google Drive and Baidu Cloud. The original video folder is Jiqing Expressway Video, and the annotation file is Lane_Parameters.zip, and the download link as follows. 

Google Drive:
https://drive.google.com/drive/folders/1iO6EUira1_irMHnEFjma3vc8LfYKHmQ4?usp=sharing

Baidu Cloud:
https://pan.baidu.com/s/1Q_ZDAm2byOmd6OUjq4JYZA
Extraction code: rwns 

#Annotation
For shaded or vehicle-occluded lanes, there is no marking or only a partial marking (only a few cases). In addition, the dataset only annotates the lane lines in the direction of road traffic, excluding the lanes in the reverse direction. In addition, the lane annotation for the ramp sections may not be perfect.

# Acknowledgement
The work for building this dataset is done by 
Shengjia Feng(fsj1377599668@gmail.com), 
Jie Wang(wjie5a16@163.com), 
Di Zhu(1727477104@qq.com),
Chang Yuan(yuanchang1220@163.com).
