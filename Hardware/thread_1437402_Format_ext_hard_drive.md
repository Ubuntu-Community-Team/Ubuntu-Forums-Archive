---
title: "Format ext hard drive"
date: 2010-03-23
forum: Hardware
---

### Post by witeshark17 on 2010-03-23
What would be the right way to format a WD Passport ext HD given:

> > Filesystem            Size  Used Avail Use% Mounted on
> > /dev/sda3             222G   12G  199G   6% /
> > udev                  1.5G  328K  1.5G   1% /dev
> > none                  1.5G  252K  1.5G   1% /dev/shm
> > none                  1.5G  104K  1.5G   1% /var/run
> > none                  1.5G     0  1.5G   0% /var/lock
> > none                  1.5G     0  1.5G   0% /lib/init/rw
> > /dev/sr1              644M  644M     0 100% /media/WD SmartWare
> > /dev/sdc1             233G   72M  233G   1% /media/My Passport

the smartware is firmware driven and cannot be removed

---

### Post by byStanderone on 2010-03-23
...have you tried gparted?

---

### Post by oleink on 2010-03-23
Well what do you wannna do with it?

---

### Post by oleink on 2010-03-23
You may wanna check out "universal usb installer" google it

---

### Post by oleink on 2010-03-23
If you dont wanna load a distro than definately try gparted if u havent

---

### Post by witeshark17 on 2010-03-24
> **byStanderone said:**
> ...have you tried gparted? I have explored that; the firmware issue rules that out AFAIK so far. My intent is to use this drive to rsync back up my Ubuntu laptop. Thanks everyone, I'll keep looking! :popcorn:

---

### Post by witeshark17 on 2010-03-24
With help from my bro:

Be careful! this can be risky. In the end, the firmware (smartware) is still there, but not wasting all that much space.

check the device

```
df -h
``````
fdisk /dev/sxx
``````
sudo mke2fs -j /dev/sxx
```the intenal backup file:

```
mkdir /volumes/usb/yourfilename
```now backup can be done by:

```
rsync -av /home/yourhomefolder/ /volumes/usb/yourfilename
```:D

---

### Post by oleink on 2010-03-25
Awesome glad it worked out!!!:popcorn:

---

