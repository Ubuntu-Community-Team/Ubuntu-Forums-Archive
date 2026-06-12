---
title: "Ubuntu 8.04 does not boot after install"
date: 2008-09-09
forum: General Help
---

### Post by zaveloff on 2008-09-09
I downloaded Ubuntu 8.04.1 and burned a CD from the iso. Ubuntu runs from the CD on my Dell Inspiron 530 with an Intel core 2 quad processor and 3 GB of RAM and I tried to install it using 150 GB of free space on my hard drive that I had left for this. The installation seemed to go OK and upon restarting I get the boot menu. I selected Ubuntu and I got the splash screen and the progress bar for a few minutes but then I keep getting "(initramfs)[idles for a while then a number xxx.xxxx] ata2.00 revalidation failed(errno=-5)" and then a repeat of the same error messages ("[a number: xxx.xxxxx]ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen; [xxx.xxxxxx] ata3.00:cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in; [xxx.xxxxxxx] ata3.00: status: { DRDY }"). This goes on for a while and then the system reboots and the whole process starts all over. I tried the recovery mode but I just get a screen full of error messages.

---

### Post by cdtech on 2008-09-09
Be sure you have your BIOS set correctly; SATA hard drive instead of an IDE hard drive (also called a PATA, or parallel ATA, hard drive).

Just a thought....

---

### Post by zaveloff on 2008-09-09
All my BIOS settings are correct.

---

