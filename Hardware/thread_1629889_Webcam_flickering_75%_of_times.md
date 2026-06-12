---
title: "Webcam flickering 75% of times"
date: 2010-11-24
forum: Hardware
---

### Post by Arminho on 2010-11-24
Hi all!

I've recently upgraded from Ubuntu Lucid to Maverick on my ASUS K50AF laptop. I'm mostly satisfied with the upgrade, but there are some issues.
One of these issues concerns the integrated USB-webcam (recognized as 13d3:5130 IMC Networks) which worked fine before the upgrade (besides the well known "upside-down" issue, which is fixed) but is pretty unstable after upgrading. 
In (estimated) 75% of the sessions the webcam picture is flickering, framerate is very low (1 pic every second) and the picture looks like a mosaik of small squares in some frames.
In the remaining 25% of sessions the webcam works just fine.
The problem can be in Cheese, Skype and Google Talk. In Cheese the webcam picture sometimes (about 50%) remains just black, although I can see a flickering image in Google Talk in the same session.

Everytime the image flickers, i can find a lot of lines ```
uvcvideo: Failed to resubmit video URB (-27).
``` with ```
dmesg | grep "uvc"
```

In sessions when the webcam is working, ```
dmesg | grep "uvc"
``` remains clean.

I already spent some days trying to resolve this issue without success...```
sudo modprobe -r uvcvideo
sudo modprobe uvcvideo
``` has no effect, resating the X-Server doesn't help, I need to restart the computer and hope for my 25%-chance to work with my webcam ;)
Does anybody have an idea what the reason for this problem might be and how to fix it? 
Thanks in Advance!

---

### Post by IcarusR on 2010-11-24
From here

[https://bugzilla.redhat.com/show_bug.cgi?id=600998#c4]("https://bugzilla.redhat.com/show_bug.cgi?id=600998#c4")

It would seem to be related to kernel usb module.
Mabe try downgrading your kernel to Lucid kernel if it worked ok in Lucid

---

### Post by Arminho on 2010-11-27
> **IcarusR said:**
> From here

[https://bugzilla.redhat.com/show_bug.cgi?id=600998#c4]("https://bugzilla.redhat.com/show_bug.cgi?id=600998#c4")

It would seem to be related to kernel usb module.
Mabe try downgrading your kernel to Lucid kernel if it worked ok in Lucid

Thanks for this hint, IcarusR!

Downgrading to Lucid would be my last option, since it would mean to loose all improvements of the new kernel. 
I think the clean fix would be to solve the problem in the current kernel.
Therefore i filed a [problem report in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/682128").

Any other ideas?

---

