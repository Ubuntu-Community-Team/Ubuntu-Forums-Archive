---
title: "Laptop Clicking"
date: 2010-05-13
forum: Hardware
---

### Post by supershort3 on 2010-05-13
Hey,

I am using Ubuntu 10.04 Remix on Asus eeePC 1000h. 

When copying files accross the network, if theres alot of files or large files the laptop starts making clicking noises inside it. I have reason to believe this is the harddisk. 

Is there any solution to this apart from the nearest river to throw the laptop downstream and hope it never comes back.

Thanks
Ben

---

### Post by SoftPops on 2010-05-13
Hi Ben. The clicking you are hearing is quite likely to be the hard disk. It can be that the disk is heading towards failure BUT this is not always the case. On my laptop I replaced its original disk for a pre-used larger capacity one, for a few weeks afterwards the disk clicked away to itself but after this it seems to have settled down and is now quite quiet (nearly 6 months now :)). For your own peace of mind, I would recommend that you keep backup copies of any important data you have. If the drive does fail, they are easy to replace and considerably cheaper than replacing the laptop.

---

### Post by supershort3 on 2010-05-13
This laptop is still under warranty. If this harddisk kicks the bucket it will be replaced for nothing? hopefully?

---

### Post by SoftPops on 2010-05-13
Certainly should be covered by the warranty, you could see how it's going closer to when the warranty period is getting close to ending and maybe see if you can get the disk swapped regardless of whether it has failed or not.

---

### Post by warfacegod on 2010-05-13
Depends on the Manufacturer. Say the word Linux to Toshiba and the Service Rep. will behave as though you have beheaded her only child. This is something of a gray area legally speaking. You have intentionally "modified" the product you bought by installing Ubuntu. In reality, we all know that installing Linux is really no different, as far as the HDD is concerned, than installing additional software in Windows. Several manufacturers don't see it that way and, with Linux installed, will tell you to kick wind.

---

### Post by supershort3 on 2010-05-13
i have  the recovery disk that came with it but not a bigger  enough flashdrive or usb dvd drive (its a netbook afterall) to put the xp installation back on it. (the recovery disk is a dvd)

At the moment the laptop is working well for what i need it for. Which is school work and office 2007. 

Do you think maybe i should buy a cheap 8GB flashdrive put XP back on it just in case?

The reason of moving to ubuntu was because the original xp installation crashed and  gave me the Blue screen of death (as Windows does)

---

### Post by warfacegod on 2010-05-13
No, I don't. Unless you are absolutely convinced that your HDD is going to fail. There are several ways to test the drive.

One is Palimpset, known as Disk Utility in the System> Admin. menu. It is notorious for throwing false positives. I suggest comparing its results with those of gsmartcontrol.

Open a Terminal and type:

```
sudo apt-get install gsmartcontrol
```

If both are saying that you have allot of bad sectors, call it 100 or more, then it is a damn good bet your drive is dying. Call the manufacturer and see what they'll for you.

---

