---
title: "CD / DVD Drive Not Mounting."
date: 2009-04-17
forum: Hardware
---

### Post by Theyoweusaliving on 2009-04-17
Hello Everyone,

 I'm currently running Ubuntu 8.10 on a Dell Optiplex GX620 and the CD / DVD drive will not seem to mount at all. It seems to be recognized by the system as I can eject and close it from the command line but absolutley no CDs or DVDs will be read or mounted. Please see my information below. I apologize for posting my lscpi, lsmod, fstab and dmesg as an attachment but for some reason it wouldn't let me post this with them in there, I kept getting an error about having too many images and a tag that was too short. I have no idea why, but I couldn't get it to stop so I've attached them as a .txt in a zip file.

Thanks everyone,
Dillon

---

### Post by Yashiro on 2009-04-18
Put a # in front of the '/dev/scd0...' line at the bottom of your fstab and reboot.

> # /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

---

### Post by Theyoweusaliving on 2009-04-24
Fraid' I'm still not having any luck.  Anything else I could attempt?

---

### Post by Yashiro on 2009-04-24
Does it appear in the bios OK? If so get the latest Ubuntu LiveCD and try to boot from it.

You could also open the machine and check the wiring or perhaps replace the cable. The logs seem to recognize the device but it returns as frozen when accessed.

---

### Post by Theyoweusaliving on 2009-04-25
Hey Yashiro,

  Unfortunately I've tried all these steps, it still doesn't seem to be working.  It is seen in bios but will not boot from any form of CD media.  I feel that it most likely isn't hardware failure as it responds to eject commands and it was working up until very recently.  All seems correct in the tower and I can hear it spin up but it still just won't mount it.  This one is driving me crazy!

---

