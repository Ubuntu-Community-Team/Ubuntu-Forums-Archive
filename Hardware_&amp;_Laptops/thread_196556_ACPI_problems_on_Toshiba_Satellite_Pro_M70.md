---
title: "ACPI problems on Toshiba Satellite Pro M70"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by jfilip on 2006-06-14
I just recently wiped my laptop's HDD to install Dapper.  It's been great so far except for the fact that unless I use the kernel 'acpi=off' option, I can't boot the system.  This makes the laptop sort of useless when it comes to being portable as I can't use battery detection or suspend/hibernate.

I was having problems installing from the live CD making the deafult filesystem and I saw two pieces of information, booting with 'acpi=off' and not making ext3 partitions.  They seemed to work but now I can't boot without turning off ACPI.

I tried using 'pci=noacpi' while booting into recovery mode but it still died around the time of checking/mounting the local filesystems.  The drive is an SATA drive so maybe there is a similar command to turn off acpi for the SCSI interface?  I'm not terribly sure about that.

Does anyone have any info that could help me out?  I'm really enjoying using Dapper so far but unless I can get ACPI working to enable hibernation and adjusting power usage when not running on AC, I won't be able to stick with it.

Thanks in advance to anyone who can help.

---

### Post by jfilip on 2006-06-15
I ended up fixing my own problem by stumbling upon a **really** old bug report about this problem that mentioned compiling kernel sources download from kernel.org fixed it.

Well, it did fix my problem.  ACPI works fine for me now.

So if anyone reads this and is also having ACPI problems on their laptop, try compiling a kernel from source.

---

### Post by ciorba on 2006-06-16
take a look at this thread:
[http://www.ubuntuforums.org/showthread.php?t=185879&page=2](http://www.ubuntuforums.org/showthread.php?t=185879&page=2)
and the bug reports mentioned there...you are not alone.

---

### Post by jfilip on 2006-06-20
Thanks for the heads up!

---

