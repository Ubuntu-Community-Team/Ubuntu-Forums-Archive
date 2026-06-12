---
title: "From Dual-Boot to Triple-Boot with GRUB"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by B.Hat on 2009-03-13
I have a question about expanding an existing dual-boot Vista/Ubuntu setup to include a new XP installation.

I use both Vista and Ubuntu quite regularly and don't want to fool with either of their partitions or installs but instead just work with a new partition for XP and modifying GRUB to handle all three if at all possible. I originally installed Vista first then Ubuntu and have been using GRUB for boot management. 

I have a second hard drive that I just cut a fresh partition into (see image) and I was planning on booting from an XP cd and installing Windows XP onto that partition.

[IMG]http://i41.tinypic.com/24mc0nr.jpg[/IMG]

Is this a rational plan? Is this the best plan? Also, what will I need to do with GRUB in order to get all my operating systems ready to go?

---

### Post by B.Hat on 2009-03-14
Well, I got a bit eager and decided to give it a shot and ask questions when held up, and I'm held up.

Installed XP, but it, of course, took over the MBR and was booting itself on restart, no GRUB.

SO, I've booted using my Ubuntu Live CD, and opened a terminal where I've attempted the following with the result shown:

```

ubuntu@ubuntu:~$ sudo grub
grub>root (hd0,4)
root (hd0,4)
grub>setup (hd0)

Error 17: Cannot mount selected partition

```

Am I guessing right that I want to set as root my Linux partition, (is hd0,4 correct?) Any ideas?

If needed, here is the output of fdisk -l

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ff90d89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       56357   452680696    7  HPFS/NTFS
/dev/sda2           56358       60801    35696430    5  Extended
/dev/sda3           60553       60801     2000092+  82  Linux swap / Solaris
/dev/sda5           56358       60551    33688242   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5fbf1bac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       58252   467903484    7  HPFS/NTFS
/dev/sdb2           58252       60802    20480000    7  HPFS/NTFS
```

---

### Post by meierfra. on 2009-03-14
> /dev/sda1   *           1       56357   452680696    7  HPFS/NTFS
/[COLOR="Red"]dev/sda2           56358       60801    35696430    5  Extended
/dev/sda3           60553       60801     2000092+  82  Linux swap / Solaris[/COLOR]
/dev/sda5           56358       60551    33688242   83  Linux


You partition table got messed up. Any partition numbered 1-4 is supposed to be a primary partition (that is, not sit inside an extended partition). But /dev/sda3  sits inside the extended partition  /dev/sda2

If you boot from the LiveCD and post the output  of

```
sudo sfdisk -d /dev/sda
```

I will be able give you instruction how to fix the partition table.

---

### Post by B.Hat on 2009-03-14
Thanks a lot for taking a look at this. Would the windows install have screwed with the partition table? Not sure how it got goofed.

Here's the sfdisk -d output:

```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=905361392, Id= 7, bootable
/dev/sda2 : start=905375205, size= 71392860, Id= 5
/dev/sda3 : start=972767880, size=  4000185, Id=82
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start=905375331, size= 67376484, Id=83
```

---

### Post by meierfra. on 2009-03-14
> Would the windows install have screwed with the partition table
I'm not sure. But I think it's caused  by the fact that different partitioning programs use slightly different rules how partition tables are supposed to be written.


Boot from the LiveCD, download the attached file "pt.txt" to the Desktop, open a terminal and type.

```
sudo sfdisk -f --no-reread /dev/sda < pt.txt
```

**Reboot to the LiveCD** and  reinstall grub

```
sudo grub
root (hd0,4)
setup (hd0)
quit
```


Reboot and you should be able to boot into Ubuntu.

---

### Post by B.Hat on 2009-03-14
Hmm, seems like sfdisk doesn't like the term "sectors" in the second line.  Here's the conversation I had with the terminal when I gave it a go:

```
ubuntu@ubuntu:~/Desktop$ sudo sfdisk -f --no-reread /dev/sda < pt.txt

Disk /dev/sda: 60801 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1   *      0+  56356-  56357- 452680696    7  HPFS/NTFS
/dev/sda2      56357   60800    4444   35696430    5  Extended
/dev/sda3      60552   60800     249    2000092+  82  Linux swap / Solaris
/dev/sda4          0       -       0          0    0  Empty
/dev/sda5      56357+  60550    4194-  33688242   83  Linux

sfdisk: unrecognized input: sectors
```

---

### Post by SuperSonic4 on 2009-03-14
I'd install XP and edit your /boot/grub/menu.lst

```
# added by me for testing
title Windows XP
root (hd1,1)
chainloader +1
makeactive

```

Not sure how well it will work for you, I also thought XP had to be the first partition on a hard drive

---

### Post by B.Hat on 2009-03-14
> ```
title Windows XP
root (hd1,1)
chainloader +1
makeactive
```

Thanks, sounds like just what I'll need for the GRUB configuration. I was wondering about the "chainloader" and "makeactive" terms.

Now I just need to get GRUB back in control of the boot process and I'll be in business!

Oh and also, the XP install appears to work fine on the second partition of the second drive; it's actually what I'm using at this moment.

---

### Post by meierfra. on 2009-03-14
Sorry, I was in Vista when I uploaded the file the first time. So the file had the wrong kind of line breaks.  I uploaded a new version. So just download the file again and try again.

---

### Post by B.Hat on 2009-03-15
Amazing what something as simple as line breaks can do. Thanks again meierfra. 

The newly uploaded file worked just fine, and my partition table is now written in a sensible manner.

Grub was able re-take control of the MBR of hd0 and with a quick update to the grub menu.lst file and some shuffling of the Vista/bootmgr and XP/ntldr files and I now have a stable triple-booter with all OS's listed on the boot menu and all loading fine.

Thanks to all for your help with this matter.

---

### Post by SuperSonic4 on 2009-03-15
No problem, I know exactly how satisfying it is when it all goes right xD

---

### Post by meierfra. on 2009-03-15
> Amazing what something as simple as line breaks can do. 
Well, I wish sfdisk wouldn't  be so picky. But it's still a very powerful tool to edit partition tables. 

> I now have a stable triple-booter with all OS's listed on the boot menu and all loading fine

Great. Have fun with Ubuntu, XP and Vista.

---

### Post by munishvit on 2009-03-15
Sorry to mix-up my problem with this thread, but I too have problem with dual-boot and I want to install Windows XP on non-first primary partition. Please Check
[http://ubuntuforums.org/showthread.php?t=1095893](http://ubuntuforums.org/showthread.php?t=1095893)
aaanny help would be great. Thanks :D

---

