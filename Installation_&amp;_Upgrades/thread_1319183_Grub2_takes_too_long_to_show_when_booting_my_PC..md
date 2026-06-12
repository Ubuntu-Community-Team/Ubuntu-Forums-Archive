---
title: "Grub2 takes too long to show when booting my PC."
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by glore2002 on 2009-11-08
Hello!

I've installed Ubuntu 9.10. Ext4 partitions and Grub2 as the bootloader. My computer has: winxp, Debian Lenny and, now, Ubuntu.

I've installed Ubuntu on my second HD and I have chosen Grub2 to be installed on mbr disk #1. 

Problem: When booting my computer, Grub2 takes around 35 seconds to show! How can I solve this? What happens if I install my old Grub (from Debian) again? Will it be able to boot Ubuntu from its ext4 partition?

Until now, I've found (Googling) Grub2 has some bugs related to systems with multiple partitions. 

Any help will be very welcome. Thanks in advance,

---

### Post by ssican on 2009-11-08
There are 2 Informations on this webpage:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

1)- Upgrading to GRUB 2

Upgrading to GRUB 2 from GRUB (legacy) in Ubuntu 9.10 or earlier versions is relatively easy. Importantly, the upgrade offers a process to ensure GRUB 2 will work on your machine before the user commits to a full conversion. _N[U]ote however that the developers made a decision to not use an automatic update to GRUB 2 as the default on upgrade installs. Users who upgrade to Ubuntu 9.10 may continue to use GRUB if desired._[/U]

2)- Uninstalling GRUB 2

[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

---

### Post by old_salt on 2009-11-08
Grub2    **IS A DOG** that the Devs should have left well alone until it matured. I am encountering boot times at least double their reports. It actually takes about 22 seconds just to show the first Grub2 item at top of screen, another 15 seconds to get to the boot menu and once you select something; it's another 30 seconds before the OS loader screen even shows before another 18 seconds to the login screen.


Less that 30 second boot times?   YOUR DEAD WRONG UBUNTU DEVS

Kubuntu 9.04 HAD that but 9.10 you screwed the pooch on.:mad:

---

### Post by glore2002 on 2009-11-08
Thanks for your replies!

What I did (not the best solution but one that worked for me) was to install grub on my second HD (the one with ubuntu) and then change the HDs boot order in BIOS. So sdb becomes the booting disk. That way, Grub appears  with almost no delay.

I've read this somewhere and tried it an it worked. It has to do with a bug in Grub2.

I hope this info is useful for someone else.


Thanks for your help!

---

