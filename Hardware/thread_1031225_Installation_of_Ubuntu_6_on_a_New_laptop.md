---
title: "Installation of Ubuntu 6 on a New laptop"
date: 2009-01-05
forum: Hardware
---

### Post by snehith_a on 2009-01-05
Hi Gurus, 
I have just bought a HP Pavilion dv4 1131tx laptop, which comes pre loaded with windows vista OS. My system right now has two drives, C: with 220GB and D: for recovery with 10GB. I want to install Ubuntu on my laptop. I would like to know how can we partition the 220GB drive so as to create free space for installing Ubuntu.


Kindly help me regarding this.

Thanks a lot
Snehith

:D

---

### Post by sandman652001 on 2009-01-05
For starters you want to install at least version 8.4 possibly 8.10 for better hardware detection.
Second if you boot off a live Ubuntu disc the installer will resize the windows partition for you, obviously, before installing, back up your PC and make sure that you have the manufacturers restore disk should anything go wrong.
Hope it helps

---

### Post by ex-para on 2009-01-05
My wife has just got a brand new laptop with Vista and she wants Ubuntu like I have (8.04) but there was no Vista disc with it to back up in case it goes wrong.

---

### Post by oilchangeguy on 2009-01-05
> **ex-para said:**
> My wife has just got a brand new laptop with Vista and she wants Ubuntu like I have (8.04) but there was no Vista disc with it to back up in case it goes wrong.

first, please don't hijack threads. second, the computer should have a restore partition on the hard drive. DO NOT delete it.

---

### Post by sandman652001 on 2009-01-05
Yes if there is no disk with the laptop you probably have a restore partition there probably is also a way to back it up on CD/DVD the producers manual should say something about it

---

### Post by Captain_tux on 2009-01-05
> **ex-para said:**
> My wife has just got a brand new laptop with Vista and she wants Ubuntu like I have (8.04) but there was no Vista disc with it to back up in case it goes wrong.

If you call the manufacturer of your laptop, they'll provide you with a set of Recovery Disks for Vista... they'll *probably* tell you that there's a charge for having them shipped to you, but if you bought some sort of protection package for it, they shouldn't charge you.

You can, however, create your own set of Recovery Disks (either CDs or DVDs).

---

### Post by starcannon on 2009-01-05
> **snehith_a said:**
> Hi Gurus, 
I have just bought a HP Pavilion dv4 1131tx laptop, which comes pre loaded with windows vista OS. My system right now has two drives, C: with 220GB and D: for recovery with 10GB. I want to install Ubuntu on my laptop. I would like to know how can we partition the 220GB drive so as to create free space for installing Ubuntu.


Kindly help me regarding this.

Thanks a lot
Snehith

:D

My wifes dv2600 worked best with Ubuntu 8.10, indeed everything worked out of the box. The only thing I had to "tweak" was the video drivers; for most its a simple matter of using the drivers in System>Administration>Hardware Drivers. In 8.10 even the troublesome camera is fully functional with no driver compiling required. 

Anyway, for me, 8.04 on my desktops, 8.10 on my laptops, this has been an excellent way to do things on my various equipment.
Laptops: Averatec 3150p, HP dv2600, Asus Eee 4g, 8g, Everex Cloudbook(yep 8.10 makes it useful), Dell inspiron 5150, Dell Mini 9
Desktops: my desktops are all built by me. AMD cpu's, Nvidia based motherboards, Nvidia GPU's 6 and 7 series, kingston ram, western digital hard disk drives. el cheapo optical drives.

---

### Post by starcannon on 2009-01-06
> **snehith_a said:**
> Hi Gurus, 
I have just bought a HP Pavilion dv4 1131tx laptop, which comes pre loaded with windows vista OS. My system right now has two drives, C: with 220GB and D: for recovery with 10GB. I want to install Ubuntu on my laptop. I would like to know how can we partition the 220GB drive so as to create free space for installing Ubuntu.


Kindly help me regarding this.

Thanks a lot
Snehith

:D
Oh sorry I didn't answer your question correctly, I would first suggest doing a Wubi install; just download an Ubuntu iso, burn it to a CD, open and close the CD drive, let it auto-run, and choose the Wubi install. This will allow you to uninstall Ubuntu as though it were a windows program(using Windows Add Remove utilitity), and it will let you do a dual boot setup. If you decide that Ubuntu is right for you, and would like to do a real partition instead of a virtual drive that Wubi does, then we can move on from there. Give Ubuntu 30gb to start with during the Wubi install, if you love it, then when you chop the hard drive up for real you can allocate more space.

GL and have fun

---

