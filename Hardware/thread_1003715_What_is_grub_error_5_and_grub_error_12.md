---
title: "What is grub error 5 and grub error 12?"
date: 2008-12-06
forum: Hardware
---

### Post by abcuser on 2008-12-06
Hi,
I have two disks on my PC. First disk is connected to IDE1 on motherboard and is set as master (no slave on IDE1), second disk is connected to IDE2 on board and is also set as master. On IDE2 is also CD-ROM drive which is set as slave.

On first disk is Windows XP and on second disk is Ubuntu 8.10. Computer is set as dual boot.

I get some very strange behavor. I power on computer and get "Grub is staring..." message and then "Error 5". I hard restart computer and get the same error. Restart again and get "Error 12". Restart again and grub loads OK and Ubuntu or Windows can be selected and normally started. Order of errors are totally unpredictable.

According to [grub error web page:](http://www.uruk.org/orig-grub/errors.html)
```

# 5 : "Disk geometry error"

This error is returned when a read is attempted at a linear block address beyond the end
 of the BIOS translated area. This generally happens if your disk is larger than the BIOS
 can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

# 12 : "Cannot mount selected partition"

This error is returned if the partition requested exists, but the filesystem type cannot
 be recognized by GRUB.

```

What are this grub error 5 and grub error 12? What is happening?

Regards

---

### Post by cdtech on 2008-12-06
I would first check to see if your GRUB is setup correctly:
```
sudo fdisk -l
```
to find the correct partition and boot order.

Then you could use the "grub" command to set the root device.

---

