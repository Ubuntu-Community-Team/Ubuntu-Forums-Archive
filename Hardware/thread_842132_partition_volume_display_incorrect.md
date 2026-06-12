---
title: "partition volume display incorrect?"
date: 2008-06-27
forum: Hardware
---

### Post by DragonView on 2008-06-27
Hi everyone:
I think my 8.04 is showing my windows partition volume incorrectly.
Under my windows, my partition volumes are shown 12.0/12.1G but under my 8.04, they are 13.0/13.1G. I known the reason is caused by dividing the byte size of my partition by (1000*1000) instead of (1024*1024). (Hope you can understand what I am saying)
And I just want to know what configuration do i need to change to make my system show the volume by dividing 1024*1024?

PS: if there is any misunderstanding, please see my example and help me out:
My HDD volume is 80G claimed by the manufacture and we know its actual size is 80G/(1024*1024)*(1000*1000) which is shown 76.3G in windows. And my 8.04 is actually showing 80G which leads to incorrect display for each partition.

^_^ I think you at last understood me. Thanks in advance in any help.

---

### Post by ukripper on 2008-06-27
> **DragonView said:**
> Hi everyone:
I think my 8.04 is showing my windows partition volume incorrectly.
Under my windows, my partition volumes are shown 12.0/12.1G but under my 8.04, they are 13.0/13.1G. I known the reason is caused by dividing the byte size of my partition by (1000*1000) instead of (1024*1024). (Hope you can understand what I am saying)
And I just want to know what configuration do i need to change to make my system show the volume by dividing 1024*1024?

PS: if there is any misunderstanding, please see my example and help me out:
My HDD volume is 80G claimed by the manufacture and we know its actual size is 80G/(1024*1024)*(1000*1000) which is shown 76.3G in windows. And my 8.04 is actually showing 80G which leads to incorrect display for each partition.

^_^ I think you at last understood me. Thanks in advance in any helping.

Can you post output of the following commands:
```
sudo fdisk -l
```
```
sudo mount
```

---

### Post by wdaniels on 2008-06-27
As far as I know, there is no global setting for this and it does vary between programs, but most programs in Linux use the binary form 1024^3 the same as Windows does, which is 'officially' called a Gibibyte (GiB). Both Linux and Windows are technically wrong where they use the notation GB to refer to a Gibibyte. Exactly which program in Linux is it that you find is using the decimal Gigabyte 1000^3 (GB) or some other variation?

The trouble with all this is that it's difficult to say which way is correct since most of the relevant standards bodies are at odds with 99% of computer users on this matter. That is why there is no consistency. I'm a little curious to know whether you have a genuine reason for wanting it shown one way or another, or is it just that you thought there was only one 'correct' way?

---

### Post by DragonView on 2008-06-27
My fdisk -l result as an new reply



Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83d683d6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1575    12647848+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1575        9729    65500281+   f  W95 Ext'd (LBA)
/dev/sda5            1575        3163    12753688+   7  HPFS/NTFS
/dev/sda6            3163        5524    18968008+   7  HPFS/NTFS
/dev/sda7            5524        7898    19066288+   7  HPFS/NTFS
/dev/sda8            7899        9604    13703413+  83  Linux
/dev/sda9            9605        9729     1004031   82  Linux swap / Solaris


To wdaniels:
Exactly, I should say I got the incorrect display from Nautilus. And the reason I want to change is because I got used to the 1024 manner.  :P

---

