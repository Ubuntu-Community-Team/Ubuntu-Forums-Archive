---
title: "Install ubuntu and get blank screen with cursor on bootup - no grub"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by PhiJ on 2009-01-03
Hi, I've just installed intrepid ibex (alongside win XP) from the linux-format dvd on my parents computer.  I had to manually fiddle with my partitions, as ubuntu didn't seem to want to resize them, and the drive does have at least one bad sector.  So.  I reboot, and I get a black screen with a cursor in the top left.  Nothing else.

Setting the bootable flag back to the windows partition lets windows load fine.  I tried chrooting into the installed ubuntu from the live CD (which works fine), and running update-grub, but that didn't help at all.  

Any ideas on how to fix this

(oh, and in terms of technical know how, I'm completely new to ubuntu, but have had a gentoo system at home for half a year, so know quite a bit about specific things, and may get thrown by the differences between the distros.  Like menu.lst (where's my grub.conf!?))

[Edit]I've now tried to chroot in and install grub as per these instructions.  Didn't work, as I got an error 15: file not found when I looked for /boot/grub/stage1.  But just looking with ls confirms that /boot/grub/stage1 is there.  I'm now very confused.  I've tried checking the partition for errors with fsck, and didn't get anything out.

---

### Post by PhiJ on 2009-01-04
Okay, so the reason for an Error 15 is explained [here]("http://www.gnu.org/software/grub/grub-faq.html") (I needed to make symbolic link from /boot/boot to /boot), but following the instructions in the [grub guide]("http://ubuntuforums.org/showthread.php?t=224351") didn't seem to help at all.  

Anyone got any idea?

[Edit] I've fixed it.  In case anybody has the same problem, I first used a super grub disk to get grub on the MBR, but then it didn't know about menu.lst, and gave me a prompt on bootup, so I followed the normal install procedures (after making /boot/boot a symbolic link again) and it worked.  I think that it would have worked if I just copied /boot/grub/menu.lst to /boot/boot/grub/menu.lst [/Edit]

---

