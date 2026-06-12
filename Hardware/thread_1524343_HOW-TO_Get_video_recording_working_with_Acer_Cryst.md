---
title: "HOW-TO: Get video recording working with Acer Crystal Eye Webcam on Ubuntu"
date: 2010-07-05
forum: Hardware
---

### Post by Stancel on 2010-07-05
[B]EDIT: this method may not work for you. Blame Ubuntu/Linux. I use Windows now.
[/B]
This is for everyone who owns an Acer laptop with this webcam. How long have you gone without being able to record video? Does YouTube's "Record from webcam" feature not even work for you? Taking pictures worked fine for me, but it always the video that was messed up.

I went through this for a year not having a clue how to fix it. If you don't know, Google it, right? Wrong. All the suggestions on how to fix it I found were useless and didn't help one bit. 

This simple solution should get your webcam working again. If it doesn't, I'll be surprised. 

Steps:

1. If you haven't installed Wine, you should. Search the Ubuntu Software Center in Applications for it and install it. 

2. Click [here]("http://gd.panam.acer.com/home/"). This is the section of the Acer website for driver downloads. All you need to do is make your way through the categories. For example, I have an Acer Aspire 7520 laptop. I clicked Notebook, then Aspire,  then Aspire 7520. You should see three camera drivers, Bison, Chicony and Suyin. Type lsusb in the Terminal to find out which one you need. 

3. Once you have downloaded the zip file, extract the folder.

4. Click on the folder and look for the Setup.exe file. Right-click that, click "Open with Wine Windows Program Loader". 

5. It should open up the Installation program, once you're done, test the webcam's video recording using Cheese or some other program, and see if it works. If it doesn't, reboot the computer and see if it works again.

---

### Post by fishymark27 on 2010-07-23
This didn't work for me with Acer aspire one (AAO110) the original one with the 8gb ssd. 

The webcam is:
064e:d101 Suyin Corp. Acer CrystalEye Webcam
Gstreamer-properties 
give the following errors:
```

gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline4/GstV4lSrc:v4lsrc1:
Error setting the channel/norm settings: Invalid argument]
libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1952): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline5/GstV4l2Src:v4l2src1:
system error: Input/output error]

```

Cheese gives a whirling star and then a black screen and this in when run in the terminal:

libv4l2: error turning on stream: Input/output error

Can anyone help? or suggest what to try next?

---

### Post by starredsteria on 2010-07-28
I have a similar issue running Ubuntu 10.04 Lucid Lynx. I've been trying to get my Acer Crystal Eye Webcam to work with skype (as I need it to work for meetings with my company) and I've tried every solution I could find with no luck. When I test via gstreamer-properties, the initial set up was Auto detect (which showed a blank window) so I changed this to 'X Window System (No Xv) and for Input, v4l1 doesn't work at all (error message 'Video for Linux (v4l): Could not get/set settings from/on resource'). I can't get it to work with v4l2, but it doesn't work in either skype or cheese. I've also ran LD_PRELOAD commands for both Cheese and Skype using both v4l and v4l2 with no luck.

root@ACER:/home/melissa# sudo gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(418): gst_v4l_set_chan_norm (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc1:
Error setting the channel/norm settings: Invalid argument]

root@ACER:/home/melissa# lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 062a:6301 Creative Labs 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 064e:d101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 003: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Any help here would be greatly appreciated... as I would really hate to have to go back to windows.

---

### Post by Stancel on 2010-07-31
Mine is SuYin too...but I used the Bison driver. SuYin didn't work right for some reason. Sorry for not saying that in the first post, but i didn't want to go out and say "Use only Bison" because I know my experience might not be the same as yours.

So...uninstall the SuYin driver and try Bison?

---

