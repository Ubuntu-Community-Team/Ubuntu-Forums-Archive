---
title: "Installing Kubuntu on a Primary Slave"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by XP105 on 2009-01-01
I'm quite new to the world of Linux. Last year I installed Kubuntu on my PC, by partitioning my hard-drive, and had no problems (other than with Partition Magic, but that was easy enough to solve). Then, a couple of months later, by no fault of Linux (it was my horrible attempt at overclocking) my PC broke and I was forced to format it. I never found the time to reinstall Linux. Now, I would like to install Kubuntu once again, only now I have an 8GB slave which I would like to install it to. My first question is, is this possible/safe to do without disconnecting my Windows harddrive? My second question is, where do I install GRUB (if I need to install that at all)? I've heard I could just use F11 at the boot screen and either choose to boot from slave (Kubuntu) or leave it to boot master (XP). My final question, which I suppose goes without saying is, how would I do this? Just stick the live CD in and look around? If I do install GRUB, I've heard I need to change the menu.lst file (I've done this before when I move Windows to the top of the list so Windows would be automatically if nothing was chosen). I heard this from google, but could find no definitive instructions of what to change it to/how to install Kubuntu on the slave, etc.
Thanks in advance for the help,
XP105
EDIT: Another question. What format should my slave be? NTFS or FAT?

---

### Post by felker2 on 2009-01-01
Just boot from the Ubuntu live CD and in most cases choose default. One thing where you MUST not choose default, is the disk partitioning: there you should choose the primary slave drive by choosing the manual partition.

Partition type, GRUB installation and menu.lst will then be OK.

HTH

---

### Post by XP105 on 2009-01-01
Thanks for the help. So it's basically the same appart from choosing the partition to be a drive? Does GRUB get installed on the slave then? Once again, thanks.

---

### Post by felker2 on 2009-01-01
> **XP105 said:**
> Thanks for the help. So it's basically the same appart from choosing the partition to be a drive? Does GRUB get installed on the slave then? Once again, thanks.

Yes (choose the correct disk) and No (Grub goes onto the MBR of the first disk, AFAIK).

---

