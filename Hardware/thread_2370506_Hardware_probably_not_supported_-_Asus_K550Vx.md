---
title: "Hardware probably not supported - Asus K550Vx"
date: 2017-09-04
forum: Hardware
---

### Post by wael.karman on 2017-09-04
Hey guys last month i buyed a new laptop a week later decided to use ubuntu, really i use ubuntu from version 9.0 and on my old pc i have no problem but with this new pc at the installation it appear ubuntu logo and then it came in deadlock. The same things happens with others linux distribution fedora work fine for 5 minutes and then some problem appear, elementary os (deadlock), ubuntu gnome (deadlock), Open Suse works but not well and i have some problem with wifi and other problem.. so i wonder if can i use linux with the next update or not.. i need to change pc ?

PC: Asus K550Vx 
CPU: Intel Core i7 6700HQ 
GPU: Nvidia GeForce GTX 950m + Intel HD 530
If need other specs can i post it.. 

Thanks

---

### Post by ajgreeny on 2017-09-04
When you boot the live OS to install the system you possibly need to use the nomodeset boot option in order that the nvidia card can work.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) 

The above link is for BIOS systems. If the computer boots in UEFI you will need to hit E when you see the grub menu appear at boot time and then add **nomodeset** to the **quiet splash** options you see in the boot stanza, then  hit F10 to boot.

---

### Post by oldfred on 2017-09-04
If new computer it will be UEFI.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
See also link below in my signature on more UEFI info.


Some similar Asus models and they also needed another boot parameter or hard drive fills with log file processing something as an error.

 ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3)
[https://ubuntuforums.org/showthread.php?t=2327570](https://ubuntuforums.org/showthread.php?t=2327570)

---

