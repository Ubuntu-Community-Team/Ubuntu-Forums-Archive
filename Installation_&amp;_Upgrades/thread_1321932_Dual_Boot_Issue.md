---
title: "Dual Boot Issue"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by BobTim777 on 2009-11-10
I am a newbie;

My issue is Grub 2 boot loader crashes trying to load Vista after about 30 seconds, an error screen flashes for a fraction of a second and the sytem reboots to GRUB 2.

How did I get to this point?
1. Vista was loaded on my machine.
2. I partioned C:\ using Ubuntu 9.1
3. Installed ubuntu to the new partition.
4. Went back and forth between Vista and Ubuntu several times, each worked well.
5. Shut down system, selected Ubuntu from GRUB menu updated drivers.
6. Shut down system, selected Vista from Grub menu and the boot loader started but crashed 30 seconds later.
7. Tried to recover Vista with install disck but the REPAIR option is not seeing the Vista install.

How do I save Vista? How do I dual boot corretly?

Regards;

BonTim

---

### Post by cariboo on 2009-11-10
Have you tried running:

```
sudo update-grub2
```

When you are in your Ubuntu install?

---

### Post by MichealH on 2009-11-10
Can you post your fdisk-l command (L not 1) and your /boot/grub/menu.lst file

Thanks!

---

### Post by oldfred on 2009-11-10
If it is grub2 you will not have a menu.lst - that is grub legacy only. Download and run this script to see your system configuration for booting.

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

