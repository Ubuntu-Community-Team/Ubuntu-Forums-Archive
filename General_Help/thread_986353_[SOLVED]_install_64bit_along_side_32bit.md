---
title: "[SOLVED] install 64bit along side 32bit"
date: 2008-11-18
forum: General Help
---

### Post by BDNiner on 2008-11-18
Is there anyway to install Ubuntu 64bit on a computer running ubuntu 32bit and select which version to run using grub or something. I am hoping that I can install only the kernel but the more i think about it the more i see that i will also need 64 bit apps.

Mainly i don't want to wipe my computer clean and start over but i may have to. i really just want start testing 64 bit Flash but not in a virtual machine. but i do not want lose my existing installation in case i run into problems.

---

### Post by Yellow Pasque on 2008-11-18
Yes, you can run both at the same time and use GRUB to select what partiton and kernel you want. Of course, you'll probably need to resize your partition(s) with gparted to make room for the 64-bit install. You'll need to do manual partitoning during the install so as not to wipe out your existing 32-bit system.

It would also be helpful to have your /home folder on a different partition, so that both 32-bit and 64-bit installs can use it and you can keep your preferences, bookmarks, etc. across each OS.

---

### Post by BDNiner on 2008-11-18
You know that is a good idea. I have a spare 80GB hard drive that i can install and move my home partition too. in fact i have to properly plan how i do this since i want to keep both on the computer for the next 3 months or so before moving to 64bit version. 

Is it worth running 64bit OS if you have less than 4GB of RAM? I know this question has been beaten to death on these boards but since i only have 2GB on the PC and I don't think i can run with 4GB, i only have 2 slots. I guess i need to check the documentation on the mother board to see if 2GB in each slot are supported.

Can grub be setup to run OSes from 2 different hard disks?

---

### Post by Yellow Pasque on 2008-11-18
> Can grub be setup to run OSes from 2 different hard disks?
Probably, because each grub entry has a "hd(x,y)" parameter with x=disk #, y=partition #. I've never personally done it that way, because when I install OS's to different disks, I just select the device to boot in my BIOS. (Actually, my Biostar 780G mobo is sweet and I don't even have to go into the BIOS and change the boot order; I can just hit F9 and get a menu of devices to boot :P )

It's worth running 64-bit if you do video encoding, photoshop, run virtual machines/OS's, rip DVD's, etc. Basically, those are the tasks that benefit from 64-bit.

---

### Post by dcstar on 2008-11-19
> **BDNiner said:**
> Is there anyway to install Ubuntu 64bit on a computer running ubuntu 32bit and select which version to run using grub or something. I am hoping that I can install only the kernel but the more i think about it the more i see that i will also need 64 bit apps.

Mainly i don't want to wipe my computer clean and start over but i may have to. i really just want start testing 64 bit Flash but not in a virtual machine. but i do not want lose my existing installation in case i run into problems.

Create a separate /home partition, make room for the other O/S and install it using the /home partition.

As long as the O/S versions are the same you should be able to boot either 32 or 64 bit without too much trouble.

I used to do this but 32 bit does nothing that 64 bit can do these days so I now exclusively use 64 bit.

---

