---
title: "System is unable to boot right after the first restart. Detailed description."
date: 2006-04-23
forum: Hardware &amp; Laptops
---

### Post by NSD on 2006-04-23
Hey guys. Sadly my first post here is related to a problem. Maybe after I solve this one I can talk about happier stuff :mrgreen: 
I've tried my luck with two distros so far (Arch 0.7.1 and Kubuntu 5.10), and experienced strange issues.
I'm running an Opteron 170 on an Asus A8N32-Sli with the latest BIOS version and 2GB of RAM.
So, I've got 3 HDDs (**none** of which are SATA):
WD 120GB Primary Master with Win XP on it
Seagate 300GB Primary Slave for storage and
Maxtor 80 GB Secondary Master, supposedly with Linux on it.
They're set up in the following way:
[[IMG]http://img116.imageshack.us/img116/9449/partisuns2it.th.jpg[/IMG]](http://img116.imageshack.us/my.php?image=partisuns2it.jpg)
So basically what I wanted to do is to use the whole 80 GB for the nix system. Thus, in both Arch and Kubuntu I let the installer do the partitioning for me.
For Arch, I chose to use Grub and install it in the MBR. All seems to go well, but after the reboot when I try to select it from the list I get GRUB error #17 (Cannot mount selected partition. This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.). Interesting. Then I decide to go through the install process again, and this time to put the loader in /hdc. Since I have an Asus motherboard, during boot-up if I press F8 I get a menu with all the devices that I can boot off. I pick the Maxtor and again, GRUB error #17. What's going on ? I decide to try a couple of different loaders - one from Acronis and one that's bundled with a  partitioning spfdisk.exe utility. Same result.
Time to move on to another distro. I download Kubuntu 5.10, burn it and proceed to install it. Again, I get it use the whole 80 GB for the install. All seems to go well, and near the end of the installation it says the computer needs to be rebooted in order to install more packages. After that, I get the same dreaded error #17 again.
What am I missing ? I think I've pretty much tried everything - tried all possible loader locations, updated the BIOS, disabled all HDDs except the Maxtor.
Here's a relevant part from /boot/grub/menu.lst

title Ubuntu, kernel 2.6.12-9-386
root (hd2,0)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot
Seems right to me.


Later edit:
Moved the hdd to one of my other systems, installed Kubuntu, booted up. Everything worked fine. Edited /boot/grub/menu.lst, brought it back. Tried to boot up - Error #17 again.
Noob issue ? I really can't figure it out.
Thanks for taking the time to read this, guys.

---

### Post by NSD on 2006-04-24
Anybody ? I've tried my luck in many different places, and nobody knows anything :(

---

### Post by NSD on 2006-04-25
I give up. Thanks for reading this regardless.
Mods feel free to lock it up. Thanks ;)

---

### Post by Sef on 2006-04-27
Oh ye of little faith,  here's how one person solved his GRUB 17 error.

[http://www.linuxquestions.org/questions/showthread.php?t=398659]("http://www.linuxquestions.org/questions/showthread.php?t=398659")

---

