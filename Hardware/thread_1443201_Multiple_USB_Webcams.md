---
title: "Multiple USB Webcams"
date: 2010-03-30
forum: Hardware
---

### Post by jbeazell on 2010-03-30
Hello all,

I have an annoying little problem that google hasn't been able to help me with.  I have an Ubuntu 9.10 system with 4 different *working* USB webcams.  I use them for various webcam streaming around the house.  They all work flawlessly, but the problem is that each time I reboot, they attach themselves to different video* devices.  This then translates into a bunch of work for me to figure out which cam is on what device, and then adjust my motion and mjpeg-stream config files so that the right cam is doing the right thing.  

For instance: Right now I have something similar to this:

USB Webcam A >> /dev/video0
USB Webcam B >> /dev/video1
USB Webcam C >> /dev/video2
USB Webcam D >> /dev/video3

If I reboot, it might change to:

USB Webcam A >> /dev/video2
USB Webcam B >> /dev/video0
USB Webcam C >> /dev/video3
USB Webcam D >> /dev/video1

I would like to know if there is some way I could map the USB ID's to a specific video device upon each boot.

thanks!!

---

### Post by jbeazell on 2010-03-31
40 views, no replies :)  Is that a 'no'?

---

### Post by IcarusR on 2010-03-31
Maybe udev rules will help here.

Found this post which may help explain...

[http://ubuntuforums.org/showthread.php?t=168221]("http://ubuntuforums.org/showthread.php?t=168221")

And 

[http://reactivated.net/writing_udev_rules.html]("http://reactivated.net/writing_udev_rules.html")

---

### Post by jbeazell on 2010-03-31
That looks REALLY promising! Thanks!

I'll let you know how it goes tonight.

---

