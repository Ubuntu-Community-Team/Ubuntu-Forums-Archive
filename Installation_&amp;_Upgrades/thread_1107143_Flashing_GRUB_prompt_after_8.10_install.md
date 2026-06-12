---
title: "Flashing GRUB prompt after 8.10 install"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by hkb11001 on 2009-03-26
I installed 8.10 onto my system:

I have WinXP on a PATA drive as master on IDE1.

I have three other SCSI drives attached via an adapter in one of the PCI slots

(I used to have Ubuntu 7.03 installed on this system)


I did a fresh install of 8.10: the intaller recognizes the three SCSI drives as sda, sdb, and sdc, while is sees the PATA drive (what used to be referred to as hda) as sdd.

I mapped /boot and / on sda and /home on sdc (not using of sdb at this time -- I'll wait for btrfs for that). 

At the last step of installation, I clicked on the "Advanced" button to see what it was about, and noticed it had to do with where GRUB was to be installed; I noted it's default selection was hd0, which I interpreted to mean it would install in the MBR of hd0 (sdd in this case), which looked good --what I wanted.

When the installation was done, and it rebooted, the system hung with a GRUB prompt. 

What next? Please help?

I've studied some of the similar postings, but can't quite decipher what I need to do.

Thanks.

---

### Post by cariboo on 2009-03-26
HAve a look at this [thread=224351]howto[/thread]. is should help you fix your problem.

Jim

---

### Post by hkb11001 on 2009-03-27
Thanks, Jim.
The problem is solved, but in an unexpected way. I'll shortly create a post/thread to further explain my situation and what happened: to see if I can get any insights into the situation.

Thanks again.
hkb

---

