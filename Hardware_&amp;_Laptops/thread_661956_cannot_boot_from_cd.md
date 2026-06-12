---
title: "cannot boot from cd"
date: 2008-01-08
forum: Hardware &amp; Laptops
---

### Post by schnuser on 2008-01-08
Hi everyone

I have a dell Laptop Inspirion 8200. The cd drive didnt work proparly if it got too warm, so I changed it with one that worked well in a acer Laptop. 
Since then my Laptop does not recognize the cd drive. I can't even boot from cd. But I can hear sometimes the cd rotating inside the drive, so the hardware seems to work.
I am a linux newbe. Can u help me?

Ubuntu 7.10

---

### Post by chavanak on 2008-01-08
Check your connections once more.

Try to use another distro cd.

See if your windows disk work.
If your windows disk is recognised by the drive, then download the image file again & burn it onto a new disk.

---

### Post by schnuser on 2008-01-08
I tried to boot with windows and debian. In both cases it doesent boot properly, I only got a blinkin Led on the cd tray and a blinking curser on a black screen and when I press enter it boots fromm harddrive. But when I try to boot ubuntu CD (with which I already booted succesfully with the old cdrom) then it boots from harddisk at once. 
In bios boot order is cdrom prior to hd.

---

### Post by jespdj on 2008-01-08
This really sounds like there is something wrong with the hardware. Is the drive connected properly (interface cable and power cable)? If possible, try another CD drive. If that still doesn't work, then it's possible that there's something broken on the motherboard... :(

---

### Post by schnuser on 2008-01-09
Ok, I'll try another cd drive. I'll get back as soon as I installed it.

Thanks

---

### Post by schnuser on 2008-02-09
Im back

I bought e new cd/dvd drive and installed it. I could just plug the drive in the tray where the floppy drive was before. 
Unfortunately there is still the same problem, the system does not regognise the drive.
If I doubleclick the cd/dvd icon in gnome there is: 
> Unable to mount media
There is probably no media in drive 
But i have a data cd in the drive

the command  
> reto:~$ sudo mount -t iso9660 /dev/scd0 /media/cdrom/
[sudo] password for reto:
mount: No medium found
didnt help either.

This is my fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3f407556-1207-4e19-a6cf-792e49632bee /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d3d127e1-36db-437d-bc44-e5321d84adab none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Any idea what could be wrong?

---

