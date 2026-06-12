---
title: "webcam used to work. now it doesn't"
date: 2010-07-28
forum: Hardware
---

### Post by zizzdude on 2010-07-28
Hi,

I have a Dell Inspiron 1564, and the webcam used to work out of the box. Sometimes the webcam would not work until I just restart it and it works fine. Now it doesn't work on Cheese, Skype, Webcamstudio, etc.

How can I fix this?

---

### Post by kokonobs on 2010-07-28
Wow, I have the exact same machine and the exact same problem. It used to work until last week. Last time i remember using it properly before this happened was 16/06/2010.

---

### Post by zizzdude on 2010-07-28
> **kokonobs said:**
> Wow, I have the exact same machine and the exact same problem. It used to work until last week. Last time i remember using it properly before this happened was 16/06/2010.

well, it could be the update of the linux kernel that might be the problem. I updated not too long ago. Hopefully that helps move this forward.

---

### Post by kokonobs on 2010-08-02
Mine has started working again now. Not sure what did the trick. I'll just say all i did since my last post.

Installed camorama - Had cheese but it wasn't working. I only tried to launch camorama once, it did not work so i gave up.

I removed and then reinstalled skype by using the .deb from skype website. But it got updated the next day. Possibly to the version in the repos (dont know for sure tho).
When i came to use the webcam again, in a skype video call, i didn't think it wud work so i connected my usb camera and somehow the integrated one started to work and stayed working. Still is now. 

Sorry i dont know exactly what fixed it.

---

### Post by zizzdude on 2010-08-02
Well, I've done some looking around, saying recompiling the uvcvideo driver would help. [http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

In a way, it has fixed my webcam problems. It would not work from time to time. I was hoping to avoid little things like that. :p

---

### Post by kokonobs on 2010-08-04
I spoke too soon. The very day i posted my last message. It stopped working again. I'll try that link. Cheers.

---

### Post by kokonobs on 2010-08-13
Zizzdude,

I tried the link but i was still getting it working once a while.

I noticed something in the last few days. Whenever i start the computer i have to go to gstreamer-properties via the terminal and change the video input device from default to the Integrated Camera to have it consistently working. I noticed also the pipeline also chances as a result. Upon restart again it goes to the default and the camera does not respond until the device is manually selected from the gstreamer-properties. It appears i have to do this each time before i use skype for video calling.

I'm yet to test it in a video call.

---

### Post by kokonobs on 2011-07-02
For anyone still having issues with this.. I followed the instructions here

[http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/](http://stemp.wordpress.com/2009/11/03/karmic-get-the-latest-drivers-for-gspca-uvc-usbvideo-and-other/)

So far everything is working perfectly. I did not understand what it all does but all i know is that it works great. 

It might be necessary to repeat it when there is a kernel update (someone with more knowledge please confirm)

Thanks


UPDATE: This did not provide a lasting solution. It just remained as it was, working randomly every now and then. But alas the root of the problem has been found and its not software related. see dell support link below, post by medic29

[http://en.community.dell.com/support...px?PageIndex=1](http://en.community.dell.com/support...px?PageIndex=1)

---

