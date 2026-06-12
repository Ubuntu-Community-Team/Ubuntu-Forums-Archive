---
title: "Power loss during distupgrade 9.04 (+SW Raid)"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by Grandon on 2009-04-24
Hello community,

I would like to share my expirience with the Ubuntu dist upgrade to 9.04 (from 8.10) during a incident with the power cable, thanks to my colleague :P

It happened during the dist-upgrade in the installation phase (~50% completed).

I have set up a software raid (1) with 2x SATA hdds.

After I powered on the machine again ubuntu couldn't boot up to the login screen, but initramfs was initialized, indicating that** /dev/md0** can't be found.

In the device list I had only **/dev/sda** & **/dev/sdb**

This solution helped me:


[LIST=1]
[*]Reboot again
[*]In GRUB edit the kernel path (press 'e' to start editing) to boot ('b') from the first HDD
[LIST=1]
[*]/boot/vmlinuz-2.6.28-11-generic root=/dev/md0 ro quiet splash
[*]TO
[*]/boot/vmlinuz-2.6.28-11-generic root=/dev/sda ro quiet splash
[/LIST]
 
[*]The system comes up
[*]sudo aptitude clean
[*]sudo aptitude update
[*]After this I rebooted the machine once again, /dev/md0 was found and the dist-upgrade wen't fine, expect that the package **nscd** wasn't correctly installed. This helped:
[LIST=1]
[*]sudo aptitude remove nscd
[*]sudo aptitude install nscd
[/LIST]
[*]The second disk resynced after this process again, you can verify the process with the following command:
[LIST=1]
[*]cat /proc/mdstat
[/LIST]
 
[/LIST]

Thanks to Ubuntu I was able to manage this somehow ;)

Greetz,
GND

---

