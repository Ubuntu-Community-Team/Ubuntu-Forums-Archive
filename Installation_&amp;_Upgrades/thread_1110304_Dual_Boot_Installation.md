---
title: "Dual Boot Installation"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by DigitalNoise on 2009-03-29
I'm pretty sure this topic has been covered in other posts, so I apologize if I'm repeating someone else's questions - however I can't seem to find something that answers the specific situation I find myself in.

I'm currently running Windows XP SP2 on my PC, and wish to install Ubuntu 8.10 as a dual-boot OS.  The problem I'm finding myself in, when I get to the partitioning manager, is that Ubuntu's installer wants to use all of the available HDD space on my secondary HDD - and I'm not sure how much it actually needs; this is my HDD setup and current free space:

HDD1 - 250GB; 69.6GB free (this is the main drive with Windows and all my programs)
HDD2 - 640GB; 470GB free (this is intended to be a storage drive for all my media, etc.).

Ubuntu wants to take HDD2 and re-size the partition down to use only what it's currently using, and dedicate the rest to Ubuntu - which would be fine, if I didn't need the space for future media needs.

Can anyone give me an idea of how much space it actually needs?  I really don't want to have to buy a 3rd drive (though they are cheap; I just don't have the $$) and I really want to dual-boot.

---

### Post by DigitalNoise on 2009-03-29
Nevermind, I figured it out.

---

### Post by merquis on 2009-03-29
i see that you figured it out, but i thought id mention that its a good idea to have a clean and de-fragmented partition/drive for ubuntu.

---

### Post by DigitalNoise on 2009-03-29
> **merquis said:**
> i see that you figured it out, but i thought id mention that its a good idea to have a clean and de-fragmented partition/drive for ubuntu.

Umm...ok.  Not entirely sure what you were getting at; the drive I installed it on was used for Data Storage - I'm not going to wipe an entire HDD or buy another simply to dual-boot OS's; seeing as resizing partions are designed to handle that.

---

### Post by merquis on 2009-03-29
> **DigitalNoise said:**
> Umm...ok.  Not entirely sure what you were getting at; the drive I installed it on was used for Data Storage - I'm not going to wipe an entire HDD or buy another simply to dual-boot OS's; seeing as resizing partions are designed to handle that.

sorry:(, i wasn't implying you delete the data, just suggesting that the partition you use should be formatted and defragmented:)

---

### Post by gregor171 on 2009-03-29
HDD2 - 640GB is a lot for ubuntu
go to manual (or something) when installer sets up a partition an set a few partitions:
ext3, /,  bootable format- for system (I read somewhere that 4GB should be enough, but I do here some 30-40GB)
swap - double size of computer ram
ext3 /home  - if you'd reinstall system you won't lose your home (size for your home folder - it's your choice)

the rest you can leave or use as data storage
* for server installation I make a separate partition for /var

---

