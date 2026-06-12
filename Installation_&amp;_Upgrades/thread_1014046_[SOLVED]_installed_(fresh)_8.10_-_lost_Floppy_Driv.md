---
title: "[SOLVED] installed (fresh) 8.10 - lost Floppy Drive"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by rated727 on 2008-12-17
Monday 12/15, I installed 8.10 onto a freshly formatted system.  (Pentium III system)
(too many peculiar tweeks and customizations to get a stable upgrade over 8.04, I tried)

Today Wednsday 12/17, I needed to format a floppy disk (to save config information on another system).

I found that I now have no floppy drive on this system.  Floppy Formatter returns the error:
Cannot initialize device
unable to open any device, formatting cannot continue.

FD0 (or Floppy) is not listed in /etc/fstab /etc/mtab  /media /mnt (the places where I expect to find)

I shut down and booted Zool5 (a single floppy disk Linux) which confirmed that the drive is configured in BIOS and in correct working order.

Is there a convenient way for me to add (previously undetected or unconfigured or newly installed) hardware?  
Is there an inconvenient way ... ?

---

### Post by Partyboi2 on 2008-12-18
Have you tried to manually mount the floppy?
```
sudo mount -t vfat /dev/fd0 /media/floppy
``` If it mounts ok and works you can add it to your /etc/fstab
```
sudo cp /etc/fstab /etc/fstab.bak
```
```
gksu gedit /etc/fstab
```
add
```
/dev/fd0 /media/floppy vfat noauto,users,exec,rw 0 0
```
Then save and reboot and try floppy.

---

### Post by wpshooter on 2008-12-18
> **Partyboi2 said:**
> Have you tried to manually mount the floppy?
```
sudo mount -t vfat /dev/fd0 /media/floppy
``` If it mounts ok and works you can add it to your /etc/fstab
```
sudo cp /etc/fstab /etc/fstab.bak
```
```
gksu gedit /etc/fstab
```
add
```
/dev/fd0 /media/floppy vfat noauto,users,exec,rw 0 0
```
Then save and reboot and try floppy.

I really don't think you should have to do all of the above.  I don't.

Have you tried another floppy disk ?  

Also, take the floppy that you are working with to another machine that is running either windows or a good installation of Linux and try doing a COMPLETE format and the disk and then bring it back to the trouble machine and is if it mounts properly.

---

### Post by rated727 on 2008-12-18
Partyboi2 --- it may not have been clear in my original post, but there is no mention of fd0 or floppy in /etc/fstab or in /etc/mtab
/media/floppy does not exist /media/fd0 does not exist
mnt/floppy does not exist /mnt/fd0 does not exist

the command that you suggested:
sudo mount -t vfat /dev/fd0 /mount/floppy

--- returns the error:
mount: mount point /media/floppy does not exist

wpshooter --- agreed, it shouldn't be this difficult, but sometimes things just don't work the way we expect.
The floppy disk (the plastic 'cartridge') is not the problem.  The Linux system has failed to see and set up for the floppy disk drive.


Thanks to both of you for your reply, but I'll have to repeat my question;
How does one add previously undetected (but functional) or new hardware to an installed Linux system?

---

### Post by sdb2028 on 2008-12-18
try this thread, worked for me.
[http://ubuntuforums.org/showthread.php?t=1014347&highlight=mount+floppy](http://ubuntuforums.org/showthread.php?t=1014347&highlight=mount+floppy)

---

### Post by rated727 on 2008-12-18
Intrepid supports USB floppy drive --- even if it doesn't support hard-installed floppy

Thanks for all, but I am not getting the BIOS interfaced (hard-installed) floppy to work as it should.

But then, I have actually found an acceeptable "work-around".  I plugged in a USB interface floppy drive (borrowed from my laptop) and it worked, immediately, without even requiring a reboot.

For the time being, the USB floppy will "do the deed" for Toshiba laptop , the Compaq, and the Ubuntu/Dell (on those very rare occasions when I need one).  Thank the computer "gods" for hot-swap USB devices.

---

### Post by 73ckn797 on 2008-12-27
Intrepid 8.10 64bit:

I am trying to mount an internal floppy drive and cannot get it to allow access.

I have followed all tips in this thread and from other thread links. The system recognizes the drive under Computer. No device shows up under "lshw". When I try to access the drive I do not have permission.

Any suggestions?

EDIT: Nevermind! I believe that using a USB Floppy drive will work better based upon comments made in this post (or one of the links). It will be more practical for the use I have which will be for updating BIOS. Seems that the BIOS requires a floppy drive to get data from. This will work for all the other computers in my house also.

---

