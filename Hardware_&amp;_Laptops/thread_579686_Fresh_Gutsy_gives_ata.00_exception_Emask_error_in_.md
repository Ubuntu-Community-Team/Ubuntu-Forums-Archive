---
title: "Fresh Gutsy gives ata.00: exception Emask error in background"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by CheeseEatingBulldog on 2007-10-18
I just installed gutsy on my vaio (specs in sig) and it keeps giving an error:

ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata1.00: (BMDMA stat 0x25)
ata1.00: cmd c8.......................... tag 0 cbd 0x0 data 4095 in

over and over again in any terminal I open. So what the is this?

---

### Post by porlavieja on 2007-10-18
Hi,I have the same proble. 

Please anyone help as.

---

### Post by frause on 2007-11-10
same same

---

### Post by wrad on 2007-11-10
Me too!

Had Grub error 17 during earlier versions due to the hard-drive being larger than the BIOS allowed.  Installed the drive with the tricky software from Seagate.  Had to add /boot partition.  Spin-Rite will also not run on it.  Maybe there is a connection?

---

### Post by willemmulder on 2007-11-27
I have the same...

However, If I boot Win XP with the ext2fs addon, I can still access the Partitions with no problem. 
In other words: the HD, the sectors and the parttions are still just fine!

I get these errors:
[http://willem-mulder.nl/ubuntu/IMG_6819_kl.jpg](http://willem-mulder.nl/ubuntu/IMG_6819_kl.jpg)

Then, after a while, it boots, but I get no X, and I can't do anything other than restart.

anybody any idea?

---

### Post by yaztromo on 2007-12-01
Is there a bug filed in lauchpad for this? I can't find one.

Running fiesty just fine a few hours ago, 100% sure HDD is in perfect condition. Just upgraded to gutsy and now getting these emask errors on all installed kernels. If anyone knows of something i can do just to boot into my system I'd be extremely grateful.

edit: Correction. I can boot into Gutsy fine using my old Fiety kernel 2.6.20-12. The problem is definitely with gutsy kernel 2.6.22-14

edit2: Bug [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164302](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/164302)

---

### Post by furyy on 2007-12-14
> **willemmulder said:**
> I have the same...

However, If I boot Win XP with the ext2fs addon, I can still access the Partitions with no problem. 
In other words: the HD, the sectors and the parttions are still just fine!

I get these errors:
[http://willem-mulder.nl/ubuntu/IMG_6819_kl.jpg](http://willem-mulder.nl/ubuntu/IMG_6819_kl.jpg)

Then, after a while, it boots, but I get no X, and I can't do anything other than restart.

anybody any idea?

getting the same 0x65 error from time to time, cpu usage goes 100% with IOwait for few secconds. Though nothing "lethal" this is getting so tiresome.

---

### Post by slayer^_^ on 2008-03-09
to me the solution was unplugging the SATA data and power cables, substituting the data ones and switching the power ones... maybe a simple contact mechanical error, due to the fact that this kinda cable are more fragile than the old ide ones...

---

