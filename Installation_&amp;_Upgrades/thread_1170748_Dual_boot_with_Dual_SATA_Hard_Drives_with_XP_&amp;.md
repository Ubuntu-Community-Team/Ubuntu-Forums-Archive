---
title: "Dual boot with Dual SATA Hard Drives with XP &amp; Jaunty"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by BorisPlankton on 2009-05-26
Hello,
I am just about to install a new SATA Drive to my PC and already have Ubuntu 9.04 Jaunty installed on existing SATA drive.
I am going to install Windows XP onto the new drive. I can see 3 options: 1) Should I just install drive and insert XP disk and then wait for everything to turn out ok. I am assuming Windows will find the Jaunty drive and allow me to set up dual boot to it?

2) Should I disconnect the 'Jaunty' Hard Drive install the new Drive and then install Windows. And follow the advice here 
[http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives]("http://ubuntu-georgia.org/installing_ubuntu_and_windows_xp_on_separate_drives")

3) Install Windows on current 'Jaunty' Drive and then reinstall Jaunty on the new drive.

3) is my least favourite - after all I am only putting windows on for the teenagers school needs.......

I would want Ubuntu as the default boot.

Any advice gratefully received before I start lashing this up...... I am a firm newbie for Linux.

Kind Regards,
Paul

---

### Post by Mark Phelps on 2009-05-27
My advice is to do what I have done:
1) Install each OS to its own drive
2) Disconnect the other drive when doing an install
3) Set the machine to boot from the Ubuntu drive
4) Manually edit the /boot/grub/menu.lst file in Ubuntu to add a stanza for booting Windows.

---

