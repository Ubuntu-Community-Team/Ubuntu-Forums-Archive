---
title: "Grub error 18 after install Ubuntu 8.04 on Laptop Compaq nc6220"
date: 2009-02-02
forum: Hardware
---

### Post by spiron on 2009-02-02
Grub error code 18 after I install Ubuntu 8.04 on Laptop Compaq nc6220, my harddisk size is 160GB. Need help for fix this problem.

---

### Post by cta16 on 2009-02-02
Is the laptop model very old? Some older motherboards can't read boot files past the 1024 cylinders or so. I had this problem too on my 8 year old desktop.

The way I fixed it was I created the Ubuntu partition in the first part of my hard drive.  You will have to reinstall ubuntu but if you are getting this error, then it's probably your first time booting into ubuntu anyways. If have used **less than half** of the space on your hard drive, then here's how you can move it.

1. [Restore MBR]("http://ubuntuforums.org/showthread.php?t=622828")
2. Boot into windows and Defragment your Hard drive at least once. Now your Windows partition is ready to be moved.
3. Use the live CD again and boot into Ubuntu. From there, start the program called Gparted. Since you have used less than half of your disk space, the there should be at least half of your hard disk space free (including your Ubuntu partition). Delete the ubuntu partition and create a new NFTS partition beside your current NFTS partition. This new partition should be slightly bigger than the original one.
4. Using Gparted, copy your original NFTS partition to the second one. Now that you have a copy, you can erase the original partition and install ubuntu on that partition. 
5.Now your Ubuntu is on the first part of your hard drive. 

Another way I found while googling the problem was to move the boot file to the first part of the hard drive. I don't know how to do this but I heard it works.

---

