---
title: "turn off webcam with command"
date: 2009-10-14
forum: Hardware
---

### Post by chaopoch on 2009-10-14
Is there any command to shutdown the integrated webcam? thanks.

---

### Post by Giblet5 on 2009-10-14
It depends on what software is turning it on in the first place.

Ubuntu doesn't install anything, by default, to enable an integrate webcam, so only you know what's installed and turning it on. Assuming that it is on... Is the webcam light on?

Usually, you turn off the 'cam by stopping the software that turned it on.

Example: install, then start, qcam and the webcam light turns on. Exit qcam and the webcam shuts off.

---

### Post by falconindy on 2009-10-14
If you know what driver module is controlling the webcam, you could disable the driver with `modprobe -r`

---

### Post by chaopoch on 2009-10-14
> **Giblet5 said:**
> It depends on what software is turning it on in the first place...

I use Cheese to capture pictures, however, the webcam light is still on when the Cheese is closed, the problem persists without any fix since Ubuntu 8.04.

> **falconindy said:**
> If you know what driver module is controlling the webcam, you could disable the driver with `modprobe -r`

This command `modprobe -r` will remove driver from kernel, doesn't it? I don't want to remove the driver, I just want to shutdown the webcam.

---

### Post by chaopoch on 2009-10-15
No one knows how to make it?

---

### Post by Tibuda on 2009-10-22
I also would like to turn it off, so BUMP.

EDIT:
> **chaopoch said:**
> This command `modprobe -r` will remove driver from kernel, doesn't it? I don't want to remove the driver, I just want to shutdown the webcam.
I tested it and no, it don't uninstall the driver, only disables it. You can enable it again with `modprobe` For my camera, I had to run
```
sudo modprobe -r gspca_m5602
```
to disable the camera and
```
sudo modprobe gspca_m5602
```
to enable it.

I would like a GUI/non-root way to this if someone knows.

---

### Post by Serious_Sally on 2011-12-05
Easiest way to disable the webcam at boot is:

sudo gedit /etc/modprobe.d/blacklist.conf

*At the bottom of the file add this line:

blacklist uvcvideo

Save the file and reboot. Your webcam is no longer functioning.

(But I always put a piece of electrical tape over the aperture anyway.)  :P

---

### Post by overdrank on 2011-12-05
Back to sleep thread .

---

