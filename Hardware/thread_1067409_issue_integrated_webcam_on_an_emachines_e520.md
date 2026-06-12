---
title: "issue: integrated webcam on an emachines e520"
date: 2009-02-11
forum: Hardware
---

### Post by sgfish on 2009-02-11
Can't find the driver, can't find anything that says webcam or camera or integrated or any combination of those on this thing. I'm very new to Ubuntu, so I'm nigh positive I'm just missing something simple.

I thank you in advance, and so does the cat. All the hollering startles her.

---

### Post by AllRadioisDead on 2009-02-11
Hi, I'm not sure if this helps, but check out this thread:
[http://ubuntuforums.org/showthread.php?t=715366](http://ubuntuforums.org/showthread.php?t=715366)

My regards to the cat :)

---

### Post by sgfish on 2009-02-12
That cat says hello.

---

### Post by squidx on 2009-02-21
I've got the emachines E520 and that tip worked great! Woot!

A quick summary -- remove and reload the video driver kernel module with "quirks=2"

It turned out the Ubuntu did recognize the camera and load the module, but without the "quirks=2" parameter. 

I noticed that I couldn't remove the module right away because I had loaded a few video applications and some of them were still vying for the driver in the background. They don't seem to play together that well. I was able to find and kill them all using top. If you don't know how to do that, then restarting may be the easier way. 

Howto:

sudo modprobe -r uvcvideo
[it will either report a fatal failure or just give back your prompt]

then, 

sudo modprobe uvcvideo quirks=2

again, no report, but then try Ekiga or Cheese. They both work for me now!

If that works for you, you'll want to add it to your boot configuration. I do. When I figure out how, I'll add it here, too.

---

