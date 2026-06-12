---
title: "XP/Ubuntu Dual Boot partitions"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by mostafa178 on 2009-08-13
I am going to dual boot between XP and Ubuntu. My hard drive size is 40GB, and I was planning on making 3 partitions (XP, Ubuntu, and Data). **_What would the recommended sizes be for XP and Ubuntu?_**

I plan on installing VMware Workstation on Ubuntu to play around with virtual machines. I'm only doing this so that I can learn more about Ubuntu and Linux. I'll try to mainly use Ubuntu, but may switch to XP occasionally. Basically, I'm trying to adapt to the Ubuntu environment and do all my normal work on Ubuntu. This will be my first "real" attempt at going from Windows to Linux. I have tried before, but have not been successful because there was always some feature I missed. But after learning about VMware Workstation, I've reconsidered and am going to try this again.

---

### Post by Psicolonia on 2009-08-13
40Gb...
I would do 4 partitions:
Swap - size of your ram
xp - 10Gb minimum (xp is crazy...office, etc...)
ubuntu - 10 Gb (you could do well with 5Gb though, my full system with A LOT of stuff fills 4.7)
data - 10 gb (ort whatever remains)

Also take a look at VirtualBox
It's a bad idea to load another instalation of XP on such a small harddrive. The image of the VMware will be itself around 4 to 5 Gb.

---

### Post by mostafa178 on 2009-08-13
Is the swap partition necessary? I'm not too familiar with it. Whenever I installed a Linux distro I just used the "Use Entire Disk" option.

---

### Post by Psicolonia on 2009-08-13
swap goes for when your computer runs out of ram or when you hibernate it. It's not necessary you can omit it but you won't be able to hibernate the computer.

---

### Post by mostafa178 on 2009-08-13
Oh okay. I don't use hibernation on my computer so that shouldn't be a problem.

EDIT: Should I do all the partitioning from the XP disk or the Ubuntu disk? Also can I format the shared data partition as NTFS?

---

### Post by ohmman on 2009-08-13
The swap file is also used when you have more programs open that can fit in your ram memory.  In Windows it is called "virtual memory".  Your previous Linux "use the whole disk" installations probably had at least 3 partitions created; Root, Home, and Swap.  I recommend creating a Swap partition.  I also would recommend a larger hard drive.  If not, I would install XP first and use it to make two partitions, one 8 - 10Gb for XP (NTFS), and the rest of the disk format it for FAT32.  Next I would install Ubuntu and use it to install Grub, and to create a 8 - 10Gb partition for Ubuntu, and a Swap partition proportional to your system ram.  Leave the rest of the drive for your data partition.  You should have no problem with both Linux and XP using the FAT32 partition to share data.

---

### Post by mostafa178 on 2009-08-13
Thank you. Also, this is off topic but, will my machine be able to run the Compiz-Fusion effects? It has an integrated Intel GMA 900 with 64 MB shared memory.

---

