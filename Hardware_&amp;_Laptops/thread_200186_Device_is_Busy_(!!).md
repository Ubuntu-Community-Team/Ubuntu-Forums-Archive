---
title: "Device is Busy (?!?!)"
date: 2006-06-19
forum: Hardware &amp; Laptops
---

### Post by keithjr on 2006-06-19
I'm sorry, but I can't be the only person who thinks it's rather silly that I often have to restart my computer in order to properly eject the CD.  I installed the automatix option for doing so with the CD button and that didn't seem to have any effect.  Attempt to eject or manually unmount with the umount command are met with: 

umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy

It's nice that it's telling me twice...

I tried looking through the processes using ps -A to find something that might be utilizing the disc (Mechwarrior 2 CD) and I can't begin to guess which it might be.
  
Seriously, it's the year 2006, the kernel's up to 2.6.16.  Let's get working on ejecting a CD.

---

### Post by gerbman on 2006-06-20
[QUOTE=keithjr]I'm sorry, but I can't be the only person who thinks it's rather silly that I often have to restart my computer in order to properly eject the CD.  I installed the automatix option for doing so with the CD button and that didn't seem to have any effect.  Attempt to eject or manually unmount with the umount command are met with: 

umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy

It's nice that it's telling me twice...

I tried looking through the processes using ps -A to find something that might be utilizing the disc (Mechwarrior 2 CD) and I can't begin to guess which it might be.
  
Seriously, it's the year 2006, the kernel's up to 2.6.16.  Let's get working on ejecting a CD.[/QUOTE]Try using```
fuser /media/cdrom0
```It should return a list of processing using the cdrom. To kill all processes using /media/cdrom0, do```
fuser -k /media/cdrom0
```You could also try```
sudo eject /dev/cdrom0
```though I'm not sure if the device has to be free before doing so.

---

### Post by keithjr on 2006-06-20
[QUOTE=gerbman]Try using```
fuser /media/cdrom0
```It should return a list of processing using the cdrom. To kill all processes using /media/cdrom0, do```
fuser -k /media/cdrom0
```You could also try```
sudo eject /dev/cdrom0
```though I'm not sure if the device has to be free before doing so.[/QUOTE]


Thanks!  That will certainly help.  The eject indeed would probably not work if the device is busy, but the fuser (never heard of that one) command should be the rosetta stone I needed.

---

