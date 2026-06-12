---
title: "Webcam not working in all programs"
date: 2009-09-30
forum: Hardware
---

### Post by dangerjunkie2002 on 2009-09-30
Hi,

I just had someone ask me to join them for a Skype video conference (their choice of platform, not mine). I've got an old Creative webcam which /var/log/messages says uses the OV511 driver and seems to be recognised without complaint.

When I try to open video in Skype it says I don't have a camera. Cheese and Camorama also maintain I don't have a camera. When I run XawTV I see a good picture from the camera.

Can someone please explain to me why my webcam works in one program but not the others and hopefully offer some suggestions as to what I need to do to make it work in all of them?

Thanks,
Paul.

---

### Post by realzippy on 2009-09-30
Maybe XAWTV loads modules like:

*videodev* or *ov511*


you could try to load the modules before starting your applications:

**sudo modprobe videodev**

**sudo modprobe ov511**

---

