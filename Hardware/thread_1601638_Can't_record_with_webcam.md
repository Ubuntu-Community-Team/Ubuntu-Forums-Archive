---
title: "Can't record with webcam"
date: 2010-10-20
forum: Hardware
---

### Post by disgruntledminion on 2010-10-20
First off, sorry if this is in the wrong forum; first time posting. Anyway, I'm having a problem recording video from my internal webcam. I'm running Lucid Lynx on a Gateway NV53 laptop. I've tried both Cheese and wxCam and had no success with either.

In Cheese I am able to take snapshots just fine but when I swap over to try to record video, the screen goes black for a few seconds. When the video comes back to record, it's split into 4 sections kind of like a puzzle and freezes. I click Stop Video and eventually have to kill the process.

wxCam is actually working much better for me, just one little problem. When I try to record with xvid compression to get audio it reduces the video to under 1 sec in length. When playing the recording all I see is just a split second of movement and it's over.

I've tried changing settings on both programs to no avail. Has anyone else had and fixed these problems? Any help is greatly appreciated since I hate having to reboot to Winblows just to record video.

---

### Post by IcarusR on 2010-10-20
Running either from terminal will give info in terminal & may help debug this.

Check in the logs to see if there is anything relevant.

---

### Post by disgruntledminion on 2010-10-20
Here's what I get when running from terminal.

jd@ubuntu:~$ cheese
** Message: Error: Stream contains no data.
gsttypefindelement.c(939): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(939): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(939): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind:
Can't typefind empty stream

totem-video-thumbnailer couldn't open file 'file:///home/jd/Videos/Webcam/2010-10-20-142123.ogv'
Reason: Stream contains no data..
totem-video-thumbnailer couldn't open file 'file:///home/jd/Videos/Webcam/2010-10-20-141940.ogv'
Reason: Stream contains no data..
totem-video-thumbnailer couldn't open file 'file:///home/jd/Videos/Webcam/2010-10-20-144200.ogv'
Reason: Stream contains no data..

** (cheese:5176): WARNING **: could not generate thumbnail for /home/jd/Videos/Webcam/2010-10-20-142123.ogv (video/ogg)


** (cheese:5176): WARNING **: could not generate thumbnail for /home/jd/Videos/Webcam/2010-10-20-141940.ogv (video/ogg)


** (cheese:5176): WARNING **: could not generate thumbnail for /home/jd/Videos/Webcam/2010-10-20-144200.ogv (video/ogg)

** Message: Error: Stream contains no data.
gsttypefindelement.c(939): gst_type_find_element_activate (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstTypeFindElement:typefind:
Can't typefind empty stream

totem-video-thumbnailer couldn't open file 'file:///home/jd/Videos/Webcam/2010-10-20-140538.ogv'
Reason: Stream contains no data..

** (cheese:5176): WARNING **: could not generate thumbnail for /home/jd/Videos/Webcam/2010-10-20-140538.ogv (video/ogg)

Killed

jd@ubuntu:~$ wxcam
Determining video4linux API version...
Using video4linux 2 API
VIDIOC_ENUM_FRAMESIZES: Invalid argument
Determining pixel format...
pixel format: YUV 4:2:2 (YUYV)
Found V4L2_PIX_FMT_YUYV pixel format
/home/jd/Desktop/video-001.avi written: 640x480, 111773 bytes

Too much of a Linux noob to know exactly what this means and if the problem can be found in here.

---

