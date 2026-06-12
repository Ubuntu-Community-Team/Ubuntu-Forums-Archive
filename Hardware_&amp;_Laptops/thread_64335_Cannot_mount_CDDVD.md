---
title: "Cannot mount CD/DVD"
date: 2005-09-10
forum: Hardware &amp; Laptops
---

### Post by onik67 on 2005-09-10
Cannot mount CD/DVD

Used the command:

sudo mount /media/cdrom0/ -o unhide

Error message:

mount: special device /dev/hda does not exist

I did install from the DVD drive & it worked fine. 
It's an LG GSA-4163 DVD +/- R/RW/RAM.
After Ubuntu started running, I think it cannot detect it. 

Does anybody have any suggestions?

Thanks.

---

### Post by mlomker on 2005-09-10
Try **cat /etc/fstab** from a terminal prompt.  One of the entries will be your CD.

Mine is actually called /dev/hdc.

---

### Post by onik67 on 2005-09-10
This is what I get from 

cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Once I try to mount, the same error shows.

mount: special device /dev/hda does not exist.

What is going wrong here?

---

### Post by onik67 on 2005-09-10
I tried dmesg & saw the following thing failed:

ide0: Wait for ready failed before probe  !

Probing IDE interface ide1...
Probing IDE interface ide1...
Probing IDE interface ide2...
Probing IDE interface ide3...
Probing IDE interface ide4...
Probing IDE interface ide5...
Stopping tasks: ==|

From another forum, saw that this causes the DVD+RW drive to not load & as a result the drive is not detected. Forgot to mention that the DVD+RW is connected as the primary master.

Can anybody suggest what I should do? 

Thank you.

---

### Post by mlomker on 2005-09-11
Is the drive being recognized from your machine's BIOS (or does it work in another operating system)?  It doesn't sound like it is, to me.  

dmesg should give you something like this:

```

mlomker@mlomkernote:~$ dmesg | grep CD
hdc: Slimtype DVDRW SOSW-852S, ATAPI CD/DVD-ROM drive
Uniform CD-ROM driver Revision: 3.20
hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache

```

You could try manually loading the kernel driver with **modprobe ide_cd** but hotplug should automatically take care of that when the driver detects the drive...

---

### Post by serzz on 2005-09-23
I have almost the same issue with breezy and kernel 2.6.12-9. I can mount CDs without any problems, but when I try same thing with DVDs myt terminal window just hangs up and I can't even eject DVD.

Have googled for all day, nothing yet found.

---

### Post by mlomker on 2005-09-23
> Have googled for all day, nothing yet found.

If it worked for you on Hoary then you should post a note on the Breezy forum...could be a bug.  I can mount them.

---

