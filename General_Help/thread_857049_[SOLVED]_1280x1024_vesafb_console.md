---
title: "[SOLVED] 1280x1024 vesafb console"
date: 2008-07-12
forum: General Help
---

### Post by centyx on 2008-07-12
I have two workstations: Home and Work. Both are very similar Dell Dimensions with the same motherboard and integrated Intel 82865G graphics controller. 

Yesterday I installed a minimal Ubuntu 8.04.1 install ( using debootstrap ) onto Work, manually adding desired software via apt-get. 

I decided to try out vesafb on the console ( I have previously failed repeatedly at getting 1280x1024 to work in Ubuntu on both machines). So I did the following:

- added vesafb to /etc/initramfs-tools/modules 
- ran update-initramfs -u
- added vga=795 to GRUB's kernel boot parameters
- rebooted

Much to my glee ( and somewhat surprise ), this worked.

So I went home and decided to try the same thing on Home.

Home is running 8.0.4.1, but was installed via cd, and has been upgraded since, I think, 5.10. 

I've repeated the same process on Home that I performed on Work, but get an error like:

31b: undefined mode   etc.

Once the system boots up, I can see that the vesafb module is loaded, but /proc/fb is empty and /dev/fb0 does not exist ( unlike Work ).

The main two differences that I see between the machines are:

Monitor - both have 17" LCD, but different manufacturer/model
OS - this is questionable. 

The kernel, 2.6.24-19-generic, is the same. The version of grub is the same.

I would write it off as a hardware issue with Home if I had not experienced the same trouble getting this to work with Work prior to yesterday's install.

Could anyone shed some light on this for me?


Thanks!

---

### Post by centyx on 2008-07-14
Turns out it was the BIOS afterall. A BIOS update from Dell resolved the issue on Home.

---

