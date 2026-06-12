---
title: "Samsung NP300 no boot"
date: 2012-04-06
forum: Hardware
---

### Post by d3rr1 on 2012-04-06
Hello,

I'm quite new to using Ubuntu.
I tried an install on windows using the wubi.exe and I really enjoyed using Linux.

Some time ago I decided to give Ubuntu more space and repartition the harddrive on my laptop.

I have a Samsung NP300V3A.

I've repartitioned laptops before with no problems. 
Now that I repartitioned the hdd for Ubuntu, making an ext4 disk, my laptop wont start anymore.

I removed the windows installation that came with the purchase, because I wanted a clean install for that as well.
(I got a windows installation disk as backup)
I was thinking: doesn't the BIOS read the ext4 disk? So it doesn't boot? Or do I need something as a bootloader (and how do I configure that?)

any help greatly appreciated.

---

### Post by Redblade20XX on 2012-04-06
During the Ubuntu installer, did you choose a location for the grub boot loader?

- Red

---

### Post by d3rr1 on 2012-04-06
is that that you have to select /boot in the dropdown menu?

I only gave the root a partion

---

### Post by Redblade20XX on 2012-04-06
Never mind. Your trying a dual boot? A fresh Ubuntu partition and fresh windows partition? 
Take a look at this if thats the case : [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

- Red

---

### Post by d3rr1 on 2012-04-06
Thanks for the quick replys and the information.

I'll read it through cause it looks very useful.

BUT I'm not trying to make a dual-boot. I want to make Ubuntu my PRIMARY OS and if I need windows for small things, I want to use a VirtualMachine.

-edit-
I have a feeling I'm trying to mix up dualboot properties instead of a cleaninstall.
I did everything according the dual-boot ways, but without a windows partition, because I deleted that partition. Perhaps this could be a reason for not booting?

I try reinstalling Ubuntu that it takes the whole disk.

---

### Post by Redblade20XX on 2012-04-06
My suggestion would be to use a ubuntu installation cd or bootable usb for the ubuntu install. Maybe something happened during the wubi install.
Start a fresh Ubuntu install and occupy all of the hdd (since you said that you'll vm windows and vm hdd is internal in the Ubuntu partition).

- Red

---

### Post by d3rr1 on 2012-04-06
Well I got it fixed. Deleting the partition and reformatting it wasn't something the boot liked.
Tnx for the help Red

---

