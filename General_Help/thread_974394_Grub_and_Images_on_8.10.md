---
title: "Grub and Images on 8.10"
date: 2008-11-07
forum: General Help
---

### Post by dpeteual on 2008-11-07
I have a dual boot XP and Linux PC. I have been using CloneZilla to make images of the Linux partitions. This has worked fine for Linux 7.10. I then install Linux 8.10. Everything appears to work fine, however when I re image the Linux boot partition and restart, the XP MBR can&#8217;t find a good grub. I know how to reset the XP MBR to point to grub on the Linux boot partition but I still can&#8217;t launch the grub menu.

I reinstalled Linux 7.10 and experimented. I could use the XP recovery consol to change the MBR so that XP booted without a grub menu. I could then use the grub setup procedure to change the XP MBR to point to grub. I then got my grub boot menu back and could boot into either XP or Linux.

I then make a CloneZilla image of the Linux boot partition, formatted the Linux boot partition and re imaged it from the CloneZilla image. Everything was perfect. I immediately got my grub menu back and could boot either system.

I then repeated this exact procedure with Linux 8.10. There was no way to get the grub menu.

I then reinstalled Linux 8.10 and copied the grub folder to another drive. I reinstalled the image and could not get to the grub menu to boot either system.

I booted from the live Ubuntu CD and deleted the grub folder on the 8.10 boot partition and copied the one I had copied to a backup drive to the 8.10 boot partition. 
When I restarted I got a good grub menu and could boot either system.

I just tried 8.04. CloneZilla works fine. Looks like another 8.10 bug.

---

