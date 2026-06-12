---
title: "Can i install ubuntu on DELL GX 260"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by wicky439 on 2009-03-18
Can i install ubuntu 8.10 at my system as
 Processor: 2.4 GHz (intel)
RAM: 512MB
VGA card: 64 MB
Branded DELL GX 260
:confused:

---

### Post by stek_87 on 2009-03-18
yes

---

### Post by wicky439 on 2009-03-18
> **stek_87 said:**
> yes

Thanks
But i want to install ubuntu by erasing windows from my system
Can you tell me how can i do this ?

---

### Post by LiamWilson on 2009-03-18
When installing from the CD, when you get the option to 'use all of HDA1' or similar, make sure this is checked.

BUT BEWARE, THIS WILL ERASE EVERYTHING ON YOUR HARD DRIVE. 

I think there is a Migration Wizard after this menu, but I'm not sure.

If you want to return to windows, you'll have to have a Windows CD at hand. Otherwise, you can try dual booting. What size is your hard drive?

---

### Post by wicky439 on 2009-03-18
> **LiamWilson said:**
> When installing from the CD, when you get the option to 'use all of HDA1' or similar, make sure this is checked.

BUT BEWARE, THIS WILL ERASE EVERYTHING ON YOUR HARD DRIVE. 

I think there is a Migration Wizard after this menu, but I'm not sure.

If you want to return to windows, you'll have to have a Windows CD at hand. Otherwise, you can try dual booting. What size is your hard drive?

40 GB and 4 drive every drive have 10 GB space

---

### Post by ugm6hr on 2009-03-18
There are plenty of guides on installing Ubuntu:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by LiamWilson on 2009-03-18
So it's a 40gb hard drive split into 4 partitons of 10gb each?

It should read each partiton, but if you want, you can delete all partions and just use one, or install Ubuntu on just one partiton.

---

### Post by slimx3m on 2009-03-18
> **wicky439 said:**
> Can i install ubuntu 8.10 at my system as
 Processor: 2.4 GHz (intel)
RAM: 512MB
VGA card: 64 MB
Branded DELL GX 260
:confused:

the easiest way to go is using "wubi".
web: [http://wubi-installer.org/]("http://wubi-installer.org/")
wiki: [http://en.wikipedia.org/wiki/Wubi_(Ubuntu)]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu)")

---

### Post by ugm6hr on 2009-03-18
> **slimx3m said:**
> the easiest way to go is using "wubi".
web: [http://wubi-installer.org/]("http://wubi-installer.org/")
wiki: [http://en.wikipedia.org/wiki/Wubi_(Ubuntu)]("http://en.wikipedia.org/wiki/Wubi_(Ubuntu)")

Although this is not the best option if you want to erase Windows.

---

### Post by wicky439 on 2009-03-19
> **ugm6hr said:**
> Although this is not the best option if you want to erase Windows.

Can i create new partations after deleting then WINDOWS partations in ubuntu?

---

### Post by ugm6hr on 2009-03-19
> **wicky439 said:**
> Can i create new partations after deleting then WINDOWS partations in ubuntu?

Best to use the Ubuntu LiveCD (System -> Admin -> Partition editor) to delete Windows and create partitions before installing Ubuntu.

As a minimum, you need an ext3 (or other Linux) partition for "/" (the main Ubuntu drive - at least 10GB), a smaller swap partition (about 1.5xRAM, max 800MB unless you use suspend to RAM).

If you know what you are doing, I would recommend creating the partitions manually, and then installing using the "Manual" option, mounting a separate "/home" partition with the remainder of your free space (i.e. 29GB).

Is there a reason you want to create partitions?  If you are not fussy, you could just use the default "Wipe entire HD" option.

---

### Post by abn91c on 2009-03-19
I have a Dell GX240 and also recommed the "use entire disk" option during the setup, just in case windows XP has any random viruses you are not aware of. Other than that Ubuntu will run fine in your PC

---

