---
title: "mount cd drive"
date: 2023-01-07
forum: Hardware
---

### Post by gravjack on 2023-01-07
Just recently had ubuntu 22.04 installed.  Can't find my cd drive.  I suspect it needs to be mounted, but all my attempts have failed.  Some help would be appreciated.

---

### Post by TheFu on 2023-01-07
Does /dev/sr0 exist?

If so, try running 
```
sudo mount -o ro,unhide  /mnt/sd0 /mnt
```
then find all the files in /mnt.

When you are done using it, run:
```
sudo umount /mnt
```


Usually, there is an entry in the /etc/fstab to automatically mount optical drives to /cdrom.  Alas, none of my systems have that line, so I can't just copy it here for you to add.  It is dependent on the device name. That the name that the kernel creates when it finds the optical hardware during boot.  /dev/cdrom0, /dev/dvd0, /dev/sr-something are all commonly seen.  

Hummm.  thinking a little more, most of my systems don't have a DVD connected, which explains why there aren't any devices.  On the 1, older system with an optical drive, I see these files in /dev/:
sr0 cdrom  cdrw dvd    dvdrw
Any of those could be used as the  mount device.

BTW, this might not be obvious, but a data disc needs to be inside the drive and it needs to be closed to mount.

---

### Post by #&amp;thj^% on 2023-01-07
> **gravjack said:**
> Just recently had ubuntu 22.04 installed.  Can't find my cd drive.  I suspect it needs to be mounted, but all my attempts have failed.  Some help would be appreciated.
Along with what has been suggested,  see if this finds it:
```
inxi -d | grep Optical
  Optical-1: /dev/sr0 vendor: hp model: CDDVDW SN-208FB dev-links: cdrom

```

---

### Post by gravjack on 2023-01-07
/dev/sr0 does not exist.  Tried running the string anyway,  No dice.  I'm  really at a loss here.

---

### Post by TheFu on 2023-01-07
> **gravjack said:**
> /dev/sr0 does not exist.  Tried running the string anyway,  No dice.  I'm  really at a loss here.

Did you check for the other names or use the 'inxi -d' command as suggested?
If there isn't any device recognized, there's little to be done.  You can run all the commands you want. Nothing will change, until the required device is determined to be available by the kernel.  That is usually a missing driver, if a specific device is connected and works under some other OSes, but doesn't work under Linux.

---

