---
title: "HP R707 Camera not mounting in Drive mode"
date: 2008-02-08
forum: Hardware &amp; Laptops
---

### Post by bugler on 2008-02-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/180472](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/180472) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello all,

My setup:
Hp DV6113US dual boot WinXP and ubuntu 7.10 fully updated to-date.  All hardware working.

I am having problems with my HP R707 camera mounting as usb drive.  I change the setting in my camera from camera to digital drive. 
Gnome does not automount USB drive.  I don't see it in /media or fstab.  dmesg | greb usb reports error reads and usb disconnect.
If I change camera to camera mode and load gthumb, Gthumb finds the camera and can import.

I did find a message linux-usb that there was a problem with the camera reporting 1 more sector of space then actually is there causing the system to shutdown the usb.  Link is [here]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/180472").

Seems to refer to kernel 2.6.22-14-general.  According to what I can read (It's almost Greek to me) this has been submitted to kernel devs for inclusion in 2.6.23 kernel.  I think they placed a patch up, but I have know idea how to fix this with the patch.  

BTW, Feisty worked perfectly with this camera.  Problem is just Gutsy I guess.

Any ubuntians can decipher the info in the link?  I would love to get my usb camera working as drive again.

Thanks.

---

