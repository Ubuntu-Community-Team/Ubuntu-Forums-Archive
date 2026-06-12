---
title: "How to enable integrated webcam?"
date: 2008-09-19
forum: Hardware
---

### Post by p1zzaface on 2008-09-19
I have an HP dv7000 notebook that came pre-installed with Vista. I am now running Ubuntu Hardy Heron on it (and loving it). The transition went by relatively smoothly, however, Ubuntu does not seem to be recognizing the integrated webcam. How does one go about remedying this issue? I'd like to be able to chat with my friends on Stickam again and take pictures with it.  

Thanks in advance (:

---

### Post by remu on 2008-09-19
Try running gstreamer-properties, go to the video tab, and under Output select v4l2, then see where it says Default, if there is a menu option for HP Webcam.

---

### Post by crazypenguin2008 on 2008-09-19
take note that the pidgin messenging platform doesnot support video chat.  

but skype and amsn does

---

### Post by p1zzaface on 2008-09-19
> **remu said:**
> Try running gstreamer-properties, go to the video tab, and under Output select v4l2, then see where it says Default, if there is a menu option for HP Webcam.

IT WORKS! Thank you kind sir, you are a gentleman and scholar. Much obliged.

---

### Post by Ripfox on 2008-09-19
Also, try Cheese it is very useful!

---

### Post by aquamammal on 2008-10-02
Hey, thanks for the suggestion, but how exactly do you run g streamer??

thanks.

---

### Post by remu on 2008-10-02
Alt+F2, or open a terminal, then the command is "gstreamer-properties". Remember, if you do this in the terminal, don't close it, or else it will close the new window.

---

### Post by ssofty on 2008-10-03
Hello, my husband has a durabook laptop and we have voice working but not the built-in webcam.  Does anyone know how to enable or install a built in webcam on a durabook laptop?

---

### Post by guardian93 on 2008-10-19
after setting gstreamer-properties, do i need to use a specific video capturing program? I ran streamer-properties, found Acer Crystal Eye webcam in the dropdown, tested Cheese but no dice.

---

### Post by dougmoffatt on 2012-09-11
I am running XP in Virtual box on Ubuntu 12.04.  Ubuntu recognises the integrated webcam but XP in vbox doesn't.  Are there some settings in vbox I should be aware of? or is it something else?  I am wanting the webcam to run Skype.

---

### Post by kkelly77 on 2012-09-23
I tried using the command gstreamer-properties which did bring up the settings window. However, when I tried to make the necessary changes I got the following error in the screenshot attached.

I also got the following code in Terminal when I type in the gstreamer command
```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Device "/dev/video0" does not exist. [v4l_calls.c(168): gst_v4l_open (): /GstPipeline:pipeline2/GstV4lSrc:v4lsrc1]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline5/GstV4l2Src:v4l2src2:
system error: No such file or directory]
```

Any ideas what's happening? I'm using a Targa Traveller 1534 laptop with built in webcam.

---

### Post by overdrank on 2012-09-24
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

