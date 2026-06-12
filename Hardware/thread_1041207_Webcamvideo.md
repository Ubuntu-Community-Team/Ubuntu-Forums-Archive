---
title: "Webcam/video"
date: 2009-01-16
forum: Hardware
---

### Post by couissent on 2009-01-16
I've recently installed Ubuntu 8.10 on a Dell Inspiron 1525 laptop.  Mostly it's fine, but inbuilt webcam doesn't work.  Also, I have a problem with Google Earth - it loads up, but video is completely messed up, with flashing screen - unusable. Don't know whether the problems are related; all other video working fine.

Has anyone had this problem - any solutions?

couissent

---

### Post by emergingtechnologies on 2010-01-24
> **couissent said:**
> I've recently installed Ubuntu 8.10 on a Dell Inspiron 1525 laptop.  Mostly it's fine, but inbuilt webcam doesn't work.  Also, I have a problem with Google Earth - it loads up, but video is completely messed up, with flashing screen - unusable. Don't know whether the problems are related; all other video working fine.

Has anyone had this problem - any solutions?

couissent

I just solved this problem on my own Inspiron 1525 by using the following code:


Code:

sudo rmmod uvcvideo
sudo modprobe uvcvideo


Try it.

---

