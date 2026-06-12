---
title: "hal blocks automount to ext disk except for local login"
date: 2008-08-10
forum: General Help
---

### Post by paul98765 on 2008-08-10
I have Hardy Heron PC running SAMBA sharing files on internal hard drive and on usb external storage device

If I start linux pc and log on at linux pc, samba access is fime

If I reboot linux pc with no local log on, then I have SAMBA problems.  I can view the files shared from the internal hard drive, but Windows Vista reports an error accessing the files on the usb external drive.

If I reboot linux pc and attempt remote log on using Xming (XDCMP) it refuses to mount the usb drive.  The error is:

Cannot Mount Volume

Error org.freedesktop.DBus.Error.AccessDenied

A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" member "Mount" error name "(unset)" destination "org.freedesktop.Hal")


If I do a local login to linux pc I can mount drive, and it is then visible via samba and XDCMP login

I have tried changing permissions under System/ControlCentre/Authorizations with no success so far.

I've also tried adding a line to fstab file, but I'm not sure that that is the root cause.

---

### Post by l3iggs on 2008-08-27
i have the same exact issue. are there any solutions out there?

---

### Post by rflight79 on 2008-08-29
I'm having the exact same problem. USB key, or iPod, if I login remotely (X over SSH), I get the error org.freedesktop.DBus.Error.AccessDenied, but if I login on the machine, then everything works fine. What is really annoying, this happened due to a recent upgrade. A few weeks ago, I did not have this problem. Still looking for solutions.

Interesting, if I have logged in locally before, it all works remotely later. But will not work remotely the first time. Really annoying on a headless box.

---

