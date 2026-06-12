---
title: "webcam upside down"
date: 2008-11-16
forum: Hardware
---

### Post by ema on 2008-11-16
Hi I'm running Ubuntu 8.04
My webcam is upside down; as now I as patching the uvcvideo driver inverting the image, but this is tricky as seen as now everything will be moved into kernel.
Is there any software that can invert the image?
I'm using Skype basically...

Thanks,
Ema! ;-)

---

### Post by ema on 2008-11-16
No one knows anything?

Cheers,

---

### Post by ciscosurfer on 2008-11-16
Seems [you posted]("http://ubuntuforums.org/showpost.php?p=4139334&postcount=9") about this issue in [another thread]("http://ubuntuforums.org/showthread.php?t=561433") on 2008-01-15. Did you follow up with the suggested workarounds provided by arjos85 and Brazilio? This fix only worked for some people```
echo 1 >/sys/class/video4linux/video0/vflip
```arjos85 provided patches further on down in the thread--they may provide you with the answer you've been looking for. :-D

---

### Post by ema on 2008-11-17
> **ciscosurfer said:**
> Seems [you posted]("http://ubuntuforums.org/showpost.php?p=4139334&postcount=9") about this issue in [another thread]("http://ubuntuforums.org/showthread.php?t=561433") on 2008-01-15. Did you follow up with the suggested workarounds provided by arjos85 and Brazilio? This fix only worked for some people```
echo 1 >/sys/class/video4linux/video0/vflip
```arjos85 provided patches further on down in the thread--they may provide you with the answer you've been looking for. :-D

Hi thanks mate.
The first time I amended the UVC driver myself to flip down the image, but now with 8.10 incoming I would not like to touch the source code...
This is what I get:

ema@blademaster:~$ sudo echo 1 >/sys/class/video4linux/video0/vflip
bash: /sys/class/video4linux/video0/vflip: No such file or directory

What can I do?
Cheers,

---

### Post by ciscosurfer on 2008-11-17
Sorry, ema, the best I can offer you is to follow the other thread all the way through.  Some of the other suggestions might work for you.  

So, you *did *modify the source code and it works for you?  I'm confused. :confused:

---

### Post by ema on 2008-11-19
Yes I implemented my own code.
But now would like to use a more 'update comfortable' option like the vflip one.

Cheers,

---

### Post by Emanuele_Z on 2008-12-23
Hi guys, I'm still after this issue.
All I have is:
[i]
ema@blademaster:~$ ls -l /sys/class/video4linux/video0/
total 0
-r--r--r-- 1 root root 4096 2008-12-23 16:05 dev
lrwxrwxrwx 1 root root    0 2008-12-23 16:07 device -> ../../../3-2:1.0
-r--r--r-- 1 root root 4096 2008-12-23 16:07 index
-r--r--r-- 1 root root 4096 2008-12-23 16:07 name
drwxr-xr-x 2 root root    0 2008-12-23 16:07 power
lrwxrwxrwx 1 root root    0 2008-12-23 16:05 subsystem -> ../../../../../../../../class/video4linux
-rw-r--r-- 1 root root 4096 2008-12-23 16:05 uevent
[/i]
So I can't flip it. Can you recommend any other software layer to use to flip it?
Cheers,

---

### Post by Emanuele_Z on 2008-12-24
No one knows?
How could I create a virtual device that just will flip the image?

Cheers,

---

### Post by Lukasz Tarkowski on 2008-12-27
Same problem here

---

### Post by pjrodz on 2011-05-18
this worked for me!

[http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html]("http://techieboycdo.blogspot.com/2010/08/fix-upside-down-or-inverted-webcam-on.html")

---

