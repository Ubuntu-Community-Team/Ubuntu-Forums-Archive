---
title: "Nvidia AGP Status missing?"
date: 2015-08-12
forum: Hardware
---

### Post by CitadelUniversal on 2015-08-12
Hello, 

 After several attempts to get nvidia's agp status to work it just comes up with an error message stating this:

cat /proc/driver/nvidia/agp/status
cat: /proc/driver/nvidia/agp/status: No such file or directory

How do I get this working on Ubuntu, my graphics card is a Nvidia GeForce GTX 750 Ti - any help would be appreciated. The OS which I'm using is Ubuntu 14.04 LTS.

---

### Post by dino99 on 2015-08-12
i myself use a gtx750, so its quite the same as yours; and indeed i get the same command output.
i says 'indeed' as it is a pci card not that ancient 'agp' slot. Anyway nothing support agp nowadays (if i'm not mistaking)
so i suppose you does not get troubles with that graphic card; that 'message' is confusing and should be silenced (like these other found ancient scsi messages)

---

### Post by SeijiSensei on 2015-08-12
I cannot get this card to awaken when I haven't used the machine for a few hours.  I have to unplug and replug the HDMI cable to get the picture to appear on the screen (an LG 55" HDTV).  I tried [some fixes]("http://ubuntuforums.org/showthread.php?t=2287674") that I've seen on the Net, but none of them worked.  Have either of you had this problem, and if you fixed it, how did you do so?

I'm using the proprietary driver, of course, in my case 352 from xorg-edgers.

For the time being, I'm running Win7 with Kubuntu 14.04 in a VirtualBox just to avoid this problem.

---

