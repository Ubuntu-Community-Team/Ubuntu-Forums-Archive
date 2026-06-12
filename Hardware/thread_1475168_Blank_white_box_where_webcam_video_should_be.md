---
title: "Blank white box where webcam video should be"
date: 2010-05-06
forum: Hardware
---

### Post by *Legion* on 2010-05-06
EDIT: You know what? This is pretty clearly a software issue. I think I will go repost this in the Multimedia/Video board, it's probably more applicable there.

I have a Sager NP5797 running Lucid with a BisonCam NB Pro (V4L2) webcam on /dev/video0

In Flash (like Chatroulette.com), everything works great. My video appears to both myself and others, and I see incoming video. (I am using the 10.1 RC libflashplugin.so, downloaded from Adobe's site)

But in applications like Cheese, Skype, etc., **I get a big blank white box where video should be**:

[IMG]http://img144.imageshack.us/img144/7251/cheese1.png[/IMG]

Cheese (as well as every other app I try) see the camera on /dev/video0:

[IMG]http://img571.imageshack.us/img571/5254/cheese2.png[/IMG]

In Skype, **the person I am calling sees my video perfectly fine**. So my camera is "working" and sending video. But I cannot see my video, **nor can I see *their* incoming video**. Taking the other person out of the equation, when I go to use the "test" in Skype, it's just a blank white box too. The video will not draw for me.

Again, I **do** see video in Flash-based web apps that use the webcam. And other people are seeing my video. But webcam video (both mine and the incoming stream) won't "draw" for me.

What makes V4L video not draw? I am using the binary NVIDIA driver for the GTX 280M chip in the laptop, and I am using Compiz. Though I tried turning Compiz off and Cheese still just showed the white box.

Any ideas?

---

### Post by *Legion* on 2010-05-06
Here's v4l2ucp and the attempt to use the Preview capability:

[IMG]http://img7.imageshack.us/img7/4366/cheese3.png[/IMG]

---

