---
title: "Installing win 7 on existing Linux machine"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by celticbhoy on 2009-06-07
I have a partition table as shown in the attached screenshot.



sda2 contains my main Ubuntu install.
sda5 contains a Karmic testing install.
sda1 contains a Moblin2 testing install.

I would like to install Win 7 to sda6, but the installer says it cannot find or create a system partition. Can anyone help with this.

PS sda7 is redundant space.

---

### Post by celticbhoy on 2009-06-07
Just had a thought, the partition that I want to install to is a logical partition. Does windows have to be installed to a primary partition ??

---

### Post by merlinus on 2009-06-07
You bet.  No second-best for gates&co.

---

### Post by celticbhoy on 2009-06-07
Yip just re-arranged my hard disk & got it installed. Too early to tell yet, but I dont think it will take me away from Ubuntu!

---

### Post by kunks112 on 2009-06-07
First, you might want more disk space.
Win 7 (32) requires 16GB
Win 7 (64) requires 20 GB


I found that if you let grub be the primary boot loader and windows boot manager as secondary, whatever OS you are using will load 5- 10 seconds sooner.

However this may only apply to those booting more then one windows OS.

---

### Post by celticbhoy on 2009-06-08
When I changed my partitions around I gave it a bit more space & I am using GRUB as the main boot loader.

---

