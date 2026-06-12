---
title: "Gparted will not run off LiveCD"
date: 2010-02-21
forum: Hardware
---

### Post by Redenbacher on 2010-02-21
I've recently run across an issue where a partition on my HDD has become unrecognized by Ubuntu, and will not allow me to boot in to the current installation.

I'm trying to restore/repair the faulty partition (my /home mount point) using a LiveCD of 9.10... problem is, Gparted doesn't want to start up. I receive the following error:

> error: libhal_acquire_global_interface_lock: org.freedesktop.Hal.Device.InterfaceAlreadyLocked: The interface org.freedesktop.Hal.Device.Storage is already exclusively locked either by someone else or it's already locked by yourself


I've googled around for quite a bit and found nothing of use. The only thing I could come up with was that gparted was already running. However 'sudo killall gparted' results in nothing.

Also, the Disk Utility reads the partition as Unrecognized.

So, how can I get Gparted to start up? Is the partition salvageable either way?

---

### Post by Redenbacher on 2010-02-22
bump

---

### Post by viper250 on 2010-02-22
try to get a copy of parted magic iso and boot it up It should run ok because it is not part of the ubuntu iso.
if this fails try the system resque iso.
if all else fails you may need to wipe the drive

---

### Post by dabl on 2010-02-22
A Parted Magic Live CD is a great tool to have (there's more than just disk partitioning on it):  [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

GParted Live CD is another way:  [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Redenbacher on 2010-02-22
Giving PartedMagic a try as we speak, the LiveCD is burning :)

Thanks for the help, I would have never considered those options otherwise!

---

### Post by Redenbacher on 2010-02-22
So I'm in this wonderful tool called PartedMagic (actually posting from it).

I ran a test on my HDD and it came back with a list of attributes citing surface disk failures etc. due to old age, and pre-failure. I'm assuming this means it's time to get a new hard drive? (This one is about 6-8 years old!)

I don't see a utility for possibly salvaging the data on the hard drive. Does anyone know if this is possible?

---

### Post by dabl on 2010-02-23
> **Redenbacher said:**
> 

Does anyone know if this is possible?

Not my expertise, but a google on "hard drive data recovery" indicates it is very possible, using your wallet.  :D

I dunno about "do it yourself" -- you can start here and test your skills:  [http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

---

