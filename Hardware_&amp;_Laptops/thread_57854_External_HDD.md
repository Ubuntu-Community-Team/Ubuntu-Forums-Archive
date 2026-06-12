---
title: "External HDD"
date: 2005-08-18
forum: Hardware &amp; Laptops
---

### Post by art on 2005-08-18
Hi forum
I recently bought a Western Digital 80 Gb external HDD, and it works just fine. The only concern I have is that unplugging it seems to be confusing. When I plug it in, it mounts allright, but when I want to unmount it, I do umount /dev/sda1 and it unmounts, but whenI push the power button on the HDD, it starts blinking and doesn't power off, but powers on again. This does not happen when I am in Windows. 
Also when I do umount, and then fdisk -l, I see it being in the list.
Very confused ](*,) 
Thanks for any help

---

### Post by heimo on 2005-08-18
Hmm... I don't know if this will help, but I'd probably try to use hdparm with -Y flag to power down the device.
[http://www.die.net/doc/linux/man/man8/hdparm.8.html](http://www.die.net/doc/linux/man/man8/hdparm.8.html)

---

### Post by art on 2005-08-18
Thanks for reply
When I do the hdparm -Y /dev/sda1 it spits out the following
 
#hdparm -Y /dev/sda1

/dev/sda1:
 issuing sleep command
 HDIO_DRIVE_CMD(sleep) failed: Invalid argument

Any thoughts?

---

### Post by heimo on 2005-08-18
[QUOTE=art]Thanks for reply
When I do the hdparm -Y /dev/sda1 it spits out the following
 
#hdparm -Y /dev/sda1

/dev/sda1:
 issuing sleep command
 HDIO_DRIVE_CMD(sleep) failed: Invalid argument

Any thoughts?[/QUOTE]

If you enter: hdparm -Y /dev/sda (without 1), does it work? I actually tried this on my computer (I have sata disks), and it doesn't work - gives " HDIO_DRIVE_CMD(sleep) failed: Inappropriate ioctl for device" (EDIT: I have to try after I've installed correct chipset drivers. EDIT2: For records: No it didn't work. I know it works on my laptop HD.)

---

### Post by art on 2005-08-23
Well it didn't work either, so I think I'll just stick to what I used to do. 
Thanks a lot anyway.

---

