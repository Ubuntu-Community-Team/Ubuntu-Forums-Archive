---
title: "Boot USB stick stops working after 2-4 minutes"
date: 2017-02-20
forum: Hardware
---

### Post by lammert-nijhof on 2017-02-20
I had the splendid idea to use my almost unused 80GB disk (only used 20GB for 17.04 and for swap) for two additional installations. Since I detected a Vista code sticker on my machine (HP Compaq dc 5850), I wanted to create a multi-boot USB stick with Windows Vista and Linux Mint 18.1. Just to remember the 'good' old times with my last Windows OS and to try out Mint. I'm lazy, so I thought first install Vista and afterwards Mint, because so I get Grub re-installed. The Linux version of Multiboot and Yumi both have dependency problems during installation, so I used Yumi on Windows XP, XP runs in Virtualbox. It was like clockwork. Created the USB, booted Vista and after a few minutes Vista setup informed me, that it could not copy a file and advised me to burn the DVD again. Then I tried to install Mint with the same effect, after a few minutes I received the same type of error message. 

So I was starting to suspect the USB stick (price $5)? To confirm my suspicion, I did run a testprogram CheckFlash for 1.5-2 hours on the 8GB stick and no errors! I also copied the content of the USB stick a couple of times to the disk without any error messages. 

My next suspect was of course Yumi. So I tried the same trick using Ubuntu's "Startup Disk Creator" for Mint. Same problem again! Mint boot-time-certify told me that it detected a problem in one file.  To be sure it were not two problems in two ISO images, I did the same with Ubuntu 16.04. I had used that USB stick and that Ubuntu ISO one week ago to re-install my laptop. No problem on my laptop, but same problem again on my desktop. 

So the ISO images are not the problem. The USB stick has been tested and no errors were detected. The programs are not the problem. The disk is not the problem SMART Test OK, one month ago that partition has been constantly used and both the Ext4 and NTFS partitions are involved. I'm clueless, probably it is the combination cheap USB stick with the USB ports reading at their max practical speed of 29 MBytes/sec (my 160GB USB HDD has the same reading speed. USB stick writing is done at 4 MBytes/sec). The testprogram did read somewhat slower dealing with the overhead of both XP and Ubuntu.

I see the following options:
[LIST=1]
[*]Try the back USB ports on the motherboard itself.
[*]Clean the desktop, especially the USB cable connection with the motherboard and the USB ports.
[*]Buy a better USB stick.
[/LIST]
I tried the first option one hour later, that did not work. So probably cleaning however useful is out too. Tomorrow I will try writing the USB stick on my laptop.

Any other ideas??

---

