---
title: "cd/dvd drive  not mounting"
date: 2010-06-21
forum: Hardware
---

### Post by gillisb91 on 2010-06-21
here is the error: 
Error mounting: mount exited with exit code 1: helper failed with:
[mntent]: line 13 in /etc/fstab is bad
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab

i open fstab and i see this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ee38bedd-9df2-43df-89a2-137211023516 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=9e9515a5-9f91-47ea-bb28-6b54ab70e20b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0#usbfs for virtualbox
none /proc/bus/usb usbfs devgid=125,devmode=664 0 0

im running ubuntu 10.4 on dell latitude d610

thanks in advance :)

---

### Post by gillisb91 on 2010-06-22
anybody have any ideas?

---

### Post by efflandt on 2010-06-22
Is the drive connected with a DVD in it?  Since it is apparently USB, maybe there is no sr0 yet (and therefore no scd0) when it looks for it during boot.  When does dmesg or /var/log/messages show any sign of sr0?

---

### Post by gillisb91 on 2010-06-22
drive is connected, the error shows up anytime i put a cd in... and i have no idea what that last part about sr0 means... sorry, real beginner here

---

### Post by gillisb91 on 2010-06-22
anyone? i really would appreciate any help here :/

---

### Post by lifeSum on 2010-06-22
What happens when you try:
```
sudo mount /dev/sr0 /media/cdrom0
```

---

### Post by gillisb91 on 2010-06-23
mount: /dev/sr0: unknown device

i think i have a bad sector or 2 :/

in disk utility it says no medium found... 

do i have to get a new cd drive?

---

### Post by lifeSum on 2010-06-23
hmm. Odd. Does this output anything:

```
dmesg | grep sr0
```

---

### Post by gillisb91 on 2010-06-23
[    1.063953] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.064092] sr 1:0:0:0: Attached scsi CD-ROM sr0

---

### Post by lifeSum on 2010-06-23
I'm still learning about the Linux system, so I'm running out of ideas. I google'd the problem and a few people found rebooting fixed the problem. Give that a try if you haven't already. Worth a shot.

---

### Post by gillisb91 on 2010-06-23
when i boot up i get an error mounting fail. "press s to skip mounting or m for manual recovery." i think this may have something to do with it...

---

### Post by gillisb91 on 2010-06-24
anybody??? i would like to use my cd drive :P

---

