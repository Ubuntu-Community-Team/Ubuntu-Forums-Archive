---
title: "Installing on Acer s7-392"
date: 2013-10-18
forum: Hardware
---

### Post by histind on 2013-10-18
I would like to put Ubuntu on my new laptop, but after contacting Acer I'm a little discouraged.  They mentioned something about a hidden partition in RAID0 that would be problematic for setting up a dual boot, are they talking about the RAID0 metadata?  Has anyone successfully installed Ubuntu on this or a similar machine, and if so, could you give a summary of the process?

---

### Post by giovanni-lion on 2013-12-14
I finally managed to install Ubuntu 13.10 on my Aspire S7. Here's how I did it:

0) Create recovery USB in Windows for saftey and delete the recovery partition
1) Press fn+2 (F2) at boot to enter UEFI. Set boot order to boot from USB drive. Leave everything else!
2) Boot the ubuntu image from usb. Select "try ubuntu before installing", press "e", edit the line that starts with "linux" to include the option acpi_backlight=vendor
3) When prompted with partitioning choose "something else". Then go find those 16GB of free space and create a swap and a root partition (or whatever you want). Select the main /dev/mapper/ device for boot (the first one of the list, the one without a number).
4) Once installation is done you will reboot to windows. Go back in to UEFI firmware setup and you should see another bootable device pop up below windows boot loader. Fix the boot order to your convenience. You can also enable F12 for boot selection.
5) Press ESC while ubuntu is booting and repeat step 2 to prevent blank screen.

The real issue for me was the acpi_backlight=vendor. I never really touched the raid0 setting and everything seems ok for now.

Hope this helps!

---

### Post by sguibor on 2014-03-09
Hi, thanks for your help!

I did almost the same thing.  I deleted the recovery partition (after copying it on an external USB key), shrunk my Windows partition and had lots of space for Linux.  I did what you recommended, and chose "something else" when prompted and then chose partitions according to my needs.  I chose the first device for boot /dev/mapper/***HDD_0 or something like that.  However, I got a weird error "??????" box and then had to return to the partition screen, where my new partitions appeared as "unknown" types.  I tried again and this error persisted.  At some point, I restarted and went directly to installing ubuntu, and repeated the partitioning process and it worked.  The installation proceeded with no issues and I now have both windows 8.1 and Ubuntu on my machine.

In summary (what I wrote was not extremely clear).  What giovanni-lion worked, but I had to try to partition a few times until it did.  In case someone else has this problem.

---

### Post by James_Stanley on 2014-03-29
Hello, I tried doing this method and I got the same problem as sguibor. Once I set up my partitions and hit install a box pops up with "??? ???". I've tried this multiple times and I'm really not sure what to do at this point. Are you sure there wasn't something else you did sguibor to make this work besides going directly to Install?


UPDATE: I was able to get past the error message by disabling RAID and then proceeding with the installation. However, neither  Windows nor Ubuntu would boot after restarting, so I reenabled RAID. After this, Windows would boot but not Ubuntu. I was able to successfully boot into Ubuntu after disabling Secure Boot. Hope this helps someone else.

---

### Post by Daniel_Edin on 2014-09-01
> **James_Stanley said:**
> Hello, I tried doing this method and I got the same problem as sguibor. Once I set up my partitions and hit install a box pops up with "??? ???". I've tried this multiple times and I'm really not sure what to do at this point. Are you sure there wasn't something else you did sguibor to make this work besides going directly to Install?


UPDATE: I was able to get past the error message by disabling RAID and then proceeding with the installation. However, neither Windows nor Ubuntu would boot after restarting, so I reenabled RAID. After this, Windows would boot but not Ubuntu. I was able to successfully boot into Ubuntu after disabling Secure Boot. Hope this helps someone else.I'm trying to dual boot Ubuntu on my Acer s7 392 but I am experiencing difficulties. 


I have also like mentioned earlier stored the recovery partition to a USB-drive. And after assigning a root ext4 partition along with a swap area I also get the ??? error pushing me back to the partitioning screen and failing the install.

I have tried different boot loader devices but they all give the same error.

I do not know how to solve this, and some help would be much appreciated!

I tried updating the bios but it did not change anything. Also tried disabling RAID in bios but I still get this ??? error..

[IMG]https://lh6.googleusercontent.com/D6OUqr4ESA_Vk6kkS9UOnMZWJ8DkcLBzS8mBjU3i2Cctr0ydP5SE5sePEVs9sEeyHp_XND9ZWPE=w1896-h936[/IMG]

---

### Post by colo3 on 2014-10-06
Did any of you find the final solution to dual boot on the Acer S7?

---

