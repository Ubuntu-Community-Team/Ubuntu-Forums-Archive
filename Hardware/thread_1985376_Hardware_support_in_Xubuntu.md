---
title: "Hardware support in Xubuntu"
date: 2012-05-23
forum: Hardware
---

### Post by altella on 2012-05-23
Hello all;

I am just realizing tha HW support in Xubuntu is not the same as is in Ubuntu.
In Ubuntu 10.04 I had my WebCam and My photo Camera ( Fujifilm F300EXR) detected without problems.

Now, in Xubuntu, the webcam is not working and the camera is not detected when I connect it via USB cable.
If the core system is the same, only changing the desktop environment, why my HW is not working?
Any possible solution?

Thank you all in advance.

---

### Post by mastablasta on 2012-05-23
if Xubuntu you are talking about is also version 10.04 then yes, the kernel is the same. however if you are using new 12.04 Xubuntu then kernel is very different. support might be dropped or needs to be enabled.

---

### Post by altella on 2012-05-23
yes, but in Ubuntu 12.04, it was working while in Xubuntu 12.04, the webcam does not work. The same occurs with the photo camera....

---

### Post by Jose Catre-Vandis on 2012-05-23
Check your Thunar settings for the camera (sometimes helps to have Thunar running before you plug it in)

What is your webcam not doing, how are you using it / trying to use it. Have you tried Cheese?

output from lsusb would help to identify the problem with camera and webcam (they need to be plugged in)

---

### Post by altella on 2012-05-23
Thunar? What should I check ? I do not really understand...

I have tested the cam with the "Cheese" program and with Skype (installed from the 10.04 Ubuntu package available from Skype website)
The web cam does not work in either of them. Running in the console "lsusb" command I obtain the following output:
 
alberto@alberto-desktop:~$ lsusb 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 002: ID 041e:4036 Creative Technology, Ltd Webcam Live!/Live! Pro 
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305 
alberto@alberto-desktop:~$ 

How could I make my camera to work?
 Thank you in advance.
Regards,

---

### Post by Jose Catre-Vandis on 2012-05-23
Your web cam has been in the kernel for sometime so not sure why you can't get it to work.

Try this command with it plugged in (as the only video device)

```
ls /dev | grep video
```

If you get something back, e.g. video0, then it is being recognised and you could try (if you have mplayer installed)
```
mplayer -cache 128 -tv driver=v4l2:width=640:height=480:device=/dev/video1 -vo xv tv://
``` to see if you get playback.

Did you have your camera plugged in as well when you ran the lsusb command, or only the webcam?

---

### Post by mörgæs on 2012-05-23
> **mastablasta said:**
> ... if you are using new 12.04 Xubuntu then kernel is very different. support might be dropped or needs to be enabled.

No, it's a rare event that support for some hardware is dropped from the kernel (that's one of the reasons for the kernel growing in size). You can almost always trust that a new kernel has better hardware support than an old.

---

### Post by altella on 2012-05-23
Ok fine !!
My WebCam is detected as "Video0", and it works with mplayer. I can see de video.
But with Cheese and Skype it does not even appear.
All the buttons in Cheese appear dimmed as no web cam existed
In Skype, the testing section for video is just a black screen.

Thanks to you I am making progress, but the webcam still does not work with these applications.
Any other clue?

Thank you very much in advance

---

### Post by Jose Catre-Vandis on 2012-05-23
Deleted

---

### Post by mörgæs on 2012-05-23
Now I'm losing track. Which Buntu version are you using - still 10.04?

---

### Post by mastablasta on 2012-05-24
i think we are now on xubuntu 12.04.
 
run gstreamer-properties from terminal and see what driver can make it run (v4l or v4l2 )
 
> open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 or v4l2
click the bottom test button for each 
 
if it is detected and you can record it means that maybe it is not set propperly in skype.
 
in skype settings if you can then select it you might need to use this to load it later on:
```
 
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

```

---

### Post by Jose Catre-Vandis on 2012-05-24
I was going to suggest this:
> LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype but noticed I don't have it on my system?

---

### Post by altella on 2012-05-24
Sorry, for those losing track :-)
 Always with the new version, Xubuntu 12.04

---

### Post by altella on 2012-05-24
This LD_PRELOAD, where do I have to change it?
Sorry for the questions but I am not very experienced in system parameter configuration.
Mplayer, why it worked?
How I can configure Cheese as well?

THank you for all your help..

---

### Post by Rodney9 on 2012-05-24
Webcam help - [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

Xubuntu help - [http://xubuntu.org/news/faq-1204-precise/](http://xubuntu.org/news/faq-1204-precise/)

[https://plus.google.com/u/1/112064450121097287690/posts](https://plus.google.com/u/1/112064450121097287690/posts)

[http://sites.google.com/site/easylinuxtipsproject/xubuntu](http://sites.google.com/site/easylinuxtipsproject/xubuntu)

[http://wiki.xfce.org/recommendedapps](http://wiki.xfce.org/recommendedapps)

[http://www.dedoimedo.com/computers/xubuntu-pangolin.html](http://www.dedoimedo.com/computers/xubuntu-pangolin.html)

Rodney

---

