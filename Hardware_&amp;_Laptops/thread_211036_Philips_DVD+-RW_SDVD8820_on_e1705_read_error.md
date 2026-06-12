---
title: "Philips DVD+-RW SDVD8820 on e1705 read error"
date: 2006-07-07
forum: Hardware &amp; Laptops
---

### Post by transm on 2006-07-07
Updated to the 686 kernel, both cores work. Finally was able to get wireless working on the Broadcom chip. Everything works great but now I can't read data dvd's that were written on a Windows XP system using Sonic DLA. The discs were also "made compatible" with other devices/systems as per the option in the Sonic DLA dropdown after burning.

dmesg output:

[17238022.652000] Assertion failed! qc->n_elem > 0,drivers/scsi/libata-core.c,at a_fill_sg,line=2531
[17238023.268000] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'fiat sou rce 2/2&#7936;', timestamp 2006/07/05 21:13 (1f10)
[17238023.268000] udf: udf_read_inode(ino 513) failed !bh
[17238023.268000] UDF-fs: Error in udf_iget, block=1, partition=1
[17238239.752000] Unable to identify CD-ROM format.

gnome says:

mount:block device /dev/scd0 is write-protected, mounting read only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so

but disk manager says that all features are supported (except write DVD-RAM).  What's going on?

I'm something of a newbie here so you might have to lay out the commands for me in detail for whatever advice you can give.  Any thoughts are massively appreciated!

EDIT: I can burn DVDs using Gnomebaker and have them viewable in Windows Xp. I can also of course read CDRs written by XP. It seems like its only the DVDs that are burned from XP. Minor in the grand scheme of things, but I have a lot of media backed up from a Windows installation that I'd like to move over.

---

### Post by transm on 2006-07-08
So basically, does Ubuntu have problems mounting DVDs burned in windows?

---

### Post by clerik on 2006-09-23
Same trouble here. I have some DVDs that dosen't work under Xubuntu, DVD that have been burned under Windows XP with Nero 7 and a Plextor PX-716A DVD burner.

I've got similar error :

Warning: device /dev/hdc is already handled by /etc/fstab, supplied label is ignored
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
Error: could not execute pmount

And if i take a look to syslog and kern.log :

kernel: [17185857.652000] Unable to identify CD-ROM format.

Someone have an idea ?

---

