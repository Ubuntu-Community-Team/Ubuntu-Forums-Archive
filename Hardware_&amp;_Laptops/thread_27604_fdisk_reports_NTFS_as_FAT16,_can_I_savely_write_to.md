---
title: "fdisk reports NTFS as FAT16, can I savely write tothe drive?"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by HJB on 2005-04-16
HI all, please help me as I am concerned that I might erase some data.

I typed:
**sudo fdisk -l**
and the following was reprted about my secondary drive:
[I]Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14593   117218241    6  FAT16[/I]

when I typed:
**sudo mount /dev/hdb1 /media/120GiG/ -t vfat -o umask=000**
I got:
[I]mount: wrong fs type, bad option, bad superblock on /dev/hdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/I]

when I then typed:
 **dmesg | tail**
I got:
[I]APIC error on CPU0: 02(02)
APIC error on CPU0: 02(02)
APIC error on CPU0: 02(01)
APIC error on CPU0: 01(02)
APIC error on CPU0: 02(08)
UDF-fs: No VRS found
ISO 9660 Extensions: Microsoft Joliet Level 1
ISOFS: changing to secondary root
FAT: bogus number of reserved sectors
VFS: Can't find a valid FAT filesystem on dev hdb1.[/I]

I the took a chance and typed:
**sudo mount /dev/hdb1 /media/120GiG/ -t ntfs -o umask=0222**

and it worked BUT  **dmesg | tail **reports:
*NTFS-fs error (device hdb1): ntfs_ucstonls(): Unicode name contains characters t hat cannot be converted to character set cp437.*

many times...
[COLOR=DarkOrange]
I can browse the drive but Im now concerned that if I write to this drive I might corrupt the data[/COLOR].

Please advice what I should / can do.
Thanks H :-)

---

### Post by cka on 2005-04-16
My advice: don't.  If your drive is formatted as NTFS, but you mount it as FAT and try to write a file it'll just cause chaos.  If you want to write to a NTFS drive, look into CaptiveNTFS (there's a thread somewhere on this forum about setting it up, fire up the ol' search engine to find it) or reformat the drive as FAT32.

---

