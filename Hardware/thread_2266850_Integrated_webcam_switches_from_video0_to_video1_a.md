---
title: "Integrated webcam switches from video0 to video1 and fails"
date: 2015-02-25
forum: Hardware
---

### Post by drakeway on 2015-02-25
Hi,

Dell Vostro 1720 running Ubuntu 14.04.

In previous versions (12.04, 13.04) my integrated webcam worked fine. Now it doesn't.

On a fresh boot, **ls -l /dev/video*** returns **video0**. Running guvcview will work fine for a while, up to a minute, then fail. The webcam will work, then freeze. typing **ls -l /dev/video*** will now return **video1**, not **video0**, and the webcam will refuse to work. Trying to run guvcview again returns the error "Unable to open device".

**lsusb** returns: Bus 006 Device 003: ID 0c45:63e0 Microdia Sonix Integrated Webcam

I have searched and searched for similar problems and possible solutions. I've ensured my user is added to the video group, but all to no avail.

Can anyone offer any help?

Thanks,

Adam

---

