---
title: "Acer HD Crystal Eye webcam (064e:a117 Suyin Corp.) and Ubuntu 9.04 problems"
date: 2009-09-18
forum: Hardware
---

### Post by andy80 on 2009-09-18
Hi all,

I've an Acer Aspire 5930G notebook, with this webcam: Acer HD Crystal Eye webcam (064e:a117 Suyin Corp.)
I'm using Ubuntu 9.04 (32 bit) and I've this problem.

While my webcam is well recognized by the system (I've the /dev/video0 device, I can see my self in Cheese preview, I can see myself in Skype option panel ecc....), I've problems when I start recording something, for example:

- when I click on "Record" button of Cheese
- when I start a video call on Skype
- when I try to stream something with Flash plugin on web

all three situations have the same problem: the framerate is very
low... something like 1-2 frame every 5 or 6 seconds.
In Skype people tell me "I see you moving very very slow... I see the image changing every 5 or 6 seconds..."
This happens in all three situations I talked about before...

This is the complete lsusb -v output: [http://pastebin.com/m7e9e94d7](http://pastebin.com/m7e9e94d7)

and this is the kern.log output when I try to record on Cheese:
[http://pastebin.com/m79c906ae](http://pastebin.com/m79c906ae)

Any idea how to fix this?

p.s: I've tried this tips I've found in Cheese documentation:

5.1.&#8195;The video is sluggish/has a slow response. What can I do?

     You may have set "ximagesink" (X Window System (No Xv)) as video-output. This means, that your cpu is doing all the work. Change it to "xvimagesink" (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.

     To change the settings, run gstreamer-properties,
     click the Video tab
     and change the appropriate settings.

but it doesn't work anyway....

---

### Post by ctbrock on 2009-11-21
AOA-150 Acer Aspire One with the same webcam, having identical problem.

Windows XP
Ubuntu Netbook Remix
Linux Mint 7

All of the above worked with this webcam, Linux with Cheese.

I now have Linux Mint (Built on Jaunty) and I have the same problem.  aMsn, Skype, Cheese, and flash games that utilize the webcam.  Preview is fine, photos are fine, video capture blacks out breiefly, then captures about 1 frams every 5 - 6 seconds as you mentioned.

I tried luvcview, and it does work when recording (around 15fps), however I have been unable to find where it saves the avi it clames to be recording.

I hope there is a solution to this problem somewhere.

---

### Post by john1066 on 2009-12-12
Hi Andy80,

I have an Aspire 6930G and Skype gives no video and doesn't accept sound input from the webcam mike. Audacity also does not accept sound from the built in mike. Do you have a solution and could you bring me up to speed on what you mean by
1 - (I've the /dev/video0 device,
2 - the complete lsusb -v output is

As you can see I'm still finding my way around Ubuntu.

Thanks,
John

---

