---
title: "GRUB2 got wrong partition for XP"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by DaveRowell on 2009-11-01
Grub2 is configured to boot XP from hd(0,1) [the first partition] when it must be hd(0,2) [the second partition].

What is the "approved" way to change this?


Whine!  Whimper!  This isn't something new.  Grub could never figure this out now Grub2 can't either - there is no OS on Compaq's recovery partition, hd(0,1) they installed XP on the second partition.  I assume that there are millions of HP and Compaq PC's with exactly the same set-up and Grub SHOULD be able to tell whether there is an OS on a partition and move on if there isn't.

OK I had to do something and I got no advice so I edited grub.cfg ...

Grub menu (grub.cfg manually edited to comment out the Windows on sda1 entry and change the "ubuntu linux on sda2" entry title to read "Windows XP on sda2" - this is inelegant but it works!)

     <<< grub.cfg file snippet >>>
### BEGIN /etc/grub.d/30_os-prober ###
# menuentry "Windows NT/2000/XP (on /dev/sda1)" {
#	insmod fat
#	set root=(hd0,1)
#	search --no-floppy --fs-uuid --set 4452-51a8
#	drivemap -s (hd0) ${root}
#	chainloader +1
# }
menuentry "Windows XP (on /dev/sda2)" {
	insmod ntfs
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 3c78b47778b4318e
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
     From this I presume that os-prober is failing to do its job!

     <<< new grub menu display >>>
     Linux ...
     Linux recovery ...
     Memory test ...
     Memory test ...
     Windoze XP ...
     
Choosing the default Linux works - choosing Windows XP works. I haven't tried the other choices.

Now can anyone suggest a "better" solution?  PLEASE!

---

### Post by wilee-nilee on 2009-11-01
> **DaveRowell said:**
> Grub2 is configured to boot XP from hd(0,1) [the first partition] when it must be hd(0,2) [the second partition].

What is the &quot;approved&quot; way to change this?


Whine!  Whimper!  This isn't something new.  Grub could never figure this out now Grub2 can't either - there is no OS on Compaq's recovery partition, hd(0,1) they installed XP on the second partition.  I assume that there are millions of HP and Compaq PC's with exactly the same set-up and Grub SHOULD be able to tell whether there is an OS on a partition and move on if there isn't.

 Did you try sudo update-grub and if you did is this where you get the wrong location information from.

---

### Post by DaveRowell on 2009-11-02
No I didn't try anything except read and try to understand posts purporting to tell how to deal with grub2.  I can't understand any of them.

I get the wrong location by actually observing the result of trying to boot into XP.  I get exactly the same result as grub has given me over the last several years - it starts Compaq's recovery - not a good idea!

Under grub all I had to do was edit the configuration file changing 0 to 1 to get the right partition.  Progress seems to have dictated that having a score of configuration files is better than 1!

---

### Post by oldfred on 2009-11-02
Do you have the boot flag on the first partition and not on the second?

Print out the results of:

```
fdisk -l
```

---

### Post by DaveRowell on 2009-11-02
OK I tried sudo update-grub.  The results reflect the situation as it was - in other words - no change.  It insists that XP is on sda1 it also shows a ubuntu linux on sda2.

System->Administration->Disk Utility correctly identifies the XP partition as sda2, the recovery partition as sda1 and ubuntu / partition as sda3

Now, how can I change whatever file grub2 uses to determine these things to reflect reality?

<<< edit >>>
Just for giggles I restarted and chose grub's choice of "ubuntu linux" on sda2 - sure enough XP started up just as it should!

---

### Post by DaveRowell on 2009-11-02
No the boot flag is on the XP partition.  Here's fdisk -l output

Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x4f6e4f6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         617     4664488+   b  W95 FAT32
/dev/sda2   *         618        5372    35947800    7  HPFS/NTFS
/dev/sda3            5373        7269    14341320   83  Linux
/dev/sda4            7270       20671   101319120    f  W95 Ext'd (LBA)
/dev/sda5            7270        7404     1020568+  82  Linux swap / Solaris
/dev/sda6            7405       20671   100298488+  83  Linux

---

### Post by F_C on 2009-11-02
[[IMG]http://brainstorm.ubuntu.com/idea/22223/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/22223/)

---

### Post by DaveRowell on 2009-11-02
Thanks but that tool was for KDE and Grub.  I have Gnome and Grub2.

If grub was installed I'd have fixed this yesterday without bothering anyone.

---

