---
title: "Dual boot Ubuntu Intrepid and Dreamlinux"
date: 2008-12-16
forum: Installation &amp; Upgrades
---

### Post by oatmealraisin on 2008-12-16
I'm not sure if this is the right place to ask but here it goes..

I've successfully installed Dreamlinux 3.5 RC4 (dual boot with Ubuntu 8.10) However, I am not able to login with the user that I just created. I get an error saying I have the incorrect user or password. I thought I would be able to rectify this by logging in as root in recovery mode and reset the password for the other user. When I boot my computer, GRUB only gives me options to boot Ubuntu (regular and recovery mode) and Dreamlinux. No options to boot Dreamlinux in recovery mode. Any ideas?

I've tried reinstalling at least 5 times, trying different passwords, even tried 123. Did not get any errors. Installation seemed to go smoothly but when logging in after the reboot (just after installation) the password does not work. Eventually I got so frustated and just deleted the partition and just allocated the whole disk to Ubuntu. I still am interested in trying out Dreamlinux. (dual boot by adding a new partition to my Ubuntu disk or by adding a second HDD). I'm quite new to linux and I like to learn. Would appreciate any input.

Thanks in advance.

---

### Post by lewisskinner on 2008-12-16
Can you not login to Ubuntu and manually edit your /boot/grub/menu.list to add the dreamlinux recovery mode?

---

