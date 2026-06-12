---
title: "Not picking up hard disk"
date: 2008-05-18
forum: Hardware
---

### Post by Pord on 2008-05-18
So on my main PC atm I have opensuse on there and was thinking of changing it over to the new hardy heron. I run the live cd and it doesnt pick up the hard disks at all in the computer.

I have SATA hard disks only in the pc with multiple paritions as i dual boot (some using NTFS).

I was wondering why open suse picks them up and ubuntu doesnt.

The motherboard is: Abit IP35 PRO
Hard disks are: Maxtor 200GB, Maxtor 160GB and Maxtor 250GB.

Ive tried with my external hard disks plugged in (which shows them) and with them unplugged both times the sata hard disks are not picked up.

Any1 got any ideas why its not picking them up?

---

### Post by Rahl on 2008-05-22
I have had this effect on Toshiba Tecra S3 laptop since Feisty. To blame was the well known problem between kernel modules ahci and ata_piix. 

 Both drivers claim the SATA controller, but ata_piix does not 'see' the discs, it only serves the optical drive. On the other side, ahci drives the disc, but does not claim the controller for the optical drive. This in fact means that both drivers must be loaded, but ahci must come first. 

Ubuntu live CD loaded ata_piix first, so it didn't see the disc up to Hardy. In Hardy, it loaded ahci first and installed successfully, but the installed system loaded ata_piix first, an act which left it unbootable.

The solution was to use the alternate install CD and install in text mode, blacklisting ata_piix. For this, the boot option "ata_piix.blacklist=yes" must be passed to the kernel. It will manage to boot and start the installer, probably using BIOS calls to access the CD. Once installer starts, it will complain that it cannot find a CD drive. To solve that, open the shell from the installer and do a "modprobe ata_piix", close the shell and tell the installer to continue. The installation then succeeds and the installed system is bootable. 

After booting the installed system, ata_piix must be added to /etc/modules to make the optical drive functional.

---

### Post by Pord on 2008-05-22
Found a quick and easy way to fix it was to go into the BIOS and set the SATA to AHCI and it picks it up fine then. With having it set to IDE it doesnt recongnise it.

So its solved now :D

---

### Post by Rahl on 2008-05-23
I'm glad it works for you. As for me, I'll have to go the long way as my laptop does not have such option in BIOS.

---

### Post by beyboo on 2008-05-25
I came in to search for support of my Abit IP35-E mobo. Since Gutsy I've had problems installing the OS. The mobo has 6 SATA ports on the mobo out of which # 1,2,5,6 are enabled. 3 and 4 are disabled as part of the mobo hardware spec. I have Seagate and WD disks installed on ports 2,5 and 6. For some reason whenever I boot from the live CD, I always get the ATA4 {DRDY} error when I boot. 

In Gutsy I managed to install the OS after removing the disks in ports 1 and 2. AFter that I installed the latest Kernel back then 2.4.26 from kernel.org and it worked. However it boots only 50% of the time. Most other times it just hangs at "Waiting for Root File System" and has to be reset a couple of times. USually entering the bios screen and saving (no changes made) works and the system boots ok. 

I havent been able to boot the Hardy disk as well on this machine. Any idea if what you say here is connected ?

Edit : Forgot to mention though that adding irqpoll as  kernel boot parameter  solves it.

---

### Post by mfernand on 2008-06-01
I have a Dell Vostro 400 with two drives 160 and 320. I have three vmlinuz kernels (I believe they're kernels) 2.6.22-14 generic which boots 50% of time. I also have 2.6.24-16 and 17. Both do not boot. They do not see drives. I don't know how to capture boot text. 2.6.24.16 and 17 use (looks like) ata_piix driver to find hard drives. I was in a previous thread that was supposedly marked "solved". I tried suggested options for vmlinuz command line and all did not work, including irqpoll. I figure I'll post in this thread and see what developes. Thanks.

---

### Post by mfernand on 2008-06-04
Like I said, I have a Dell Vostro 400. Apparently the fix blow works for them as well as inspiron 530, because I did it and now I boot on all kernels.

[http://linux.dell.com/wiki/index.php...on_causes_hang](http://linux.dell.com/wiki/index.php...on_causes_hang)
Credit goes to user jjf who had link in his post....
Thanks...
:)

---

### Post by Jive Turkey on 2008-06-06
I just bought an Abit IP35 Pro board (it will come today I hope.  I read on the comments at NewEgg someone wrote that their SATA drives were not being detected until they moved them to SATA ports 5 and 6.  ports 1-4 wouldn't work for some reason.

---

