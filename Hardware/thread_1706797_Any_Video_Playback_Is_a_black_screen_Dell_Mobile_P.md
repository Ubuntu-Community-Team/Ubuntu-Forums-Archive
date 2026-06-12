---
title: "Any Video Playback Is a black screen Dell Mobile Precision M4500"
date: 2011-03-14
forum: Hardware
---

### Post by Harokey on 2011-03-14
I've recently purchased a Dell Precision M4500 Laptop. 

I am unable to watch videos on my system, running Ubuntu 10.04. 

I have all the appropriate codecs installed, and it appears that the video is "playing back" correctly, but is not showing up on my display. I've tried several video players and test videos, including mplayer, totem, vlc. 

I've installed the latest Nvidia Drivers using a ppa guide I found. [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

This unfortunately did not help.  When I start a video, the entire screen seems to blink black. I haven't been able to find other people with the same problem, but hopefully somebody knows how to fix this.

Also, I should say, that I can run glxgears just fine while watching a video.

Edit2: I found this: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/461958](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/461958) and when I change the VLC output to OpenGL it will display the video.

---

### Post by Harokey on 2011-03-14
Like I said before, it works when I use opengl as the output device. 

To change totem and whatever gstreamer program to work, run "gstreamer-properties" from the command line, select the video, under Plugin: select "Custom" and in pipeline type "ximagesink" without the quotes. 

This doesn't solve the problem, per-se, but it is probably a "good enough" workaround. I've posted it here incase someone else is having a similar problem.

---

