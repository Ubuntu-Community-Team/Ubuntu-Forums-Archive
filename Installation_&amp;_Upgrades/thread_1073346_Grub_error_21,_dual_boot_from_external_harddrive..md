---
title: "Grub error 21, dual boot from external harddrive."
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by Jarige on 2009-02-18
Hey guys, posting about my second issue. The first issue was the installation: [http://ubuntuforums.org/showthread.php?t=1069951](http://ubuntuforums.org/showthread.php?t=1069951)

I installed Ubuntu on my USB harddrive from the LiveCD I'm currently booted on. No errors during installation.
It asked to restart, so I restarted. It started BIOS, and then it outputted

Grub loading, please wait
Error 21

Before that, there was something about Stage 1.5 (seemed important on other threads) I didn't see Stage 2 nor stage 1 on the output.

Ok, it seems weird to me, but when I unplug my USB harddrive, and boot, it gives 'Operating System not found'. Why? Vista is still there I hope!? I can't mount OS (Vista's partition) but I can mount HP_RECOVERY.

These are the labels of the partitions. I hope you can use those, so it will be more clear to me:
Partition     Label           Mountpoint
/dev/sda1     OS              
/dev/sda2     HP_RECOVERY     

/dev/sdb1     DATA

I made a screenshot of GParted showing my external harddrive:
[ [img]http://willhostforfood.com/users/J/Jarige/GParted_screen.png[/img]](http://willhostforfood.com/access.php?fileid=55335)
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2bda47a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18356   147444538+   7  HPFS/NTFS
/dev/sda2           18357       19457     8843782+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0adc4429

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe3414533

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       32386   260139840    7  HPFS/NTFS
/dev/sdc2           32387       33382     8000370   83  Linux
/dev/sdc3           33383       33631     2000092+  82  Linux swap / Solaris
/dev/sdc4           33632       38913    42427665    5  Extended
/dev/sdc5           33632       38913    42427633+  83  Linux

```

I hope someone can help me with this, cause this doesn't make Ubuntu's appreciation better to me.
But hey, I don't know how to uninstall Ubuntu and Grub, so I guess I'm stuck with it, and I don't want to be depended on Vista, so this is one of the only solutions :P

Help me:D

If you want any more information, just ask me. I'd be happy to help you helping me;)

---

### Post by Jarige on 2009-02-18
*solved* by this thread:

[http://ubuntuforums.org/showthread.php?t=1057506&highlight=grub+error+21](http://ubuntuforums.org/showthread.php?t=1057506&highlight=grub+error+21)

I'm so happy :D

---

### Post by caljohnsmith on 2009-02-18
Glad that thread worked for you; cheers and enjoy your Ubuntu install. :)

---

### Post by redroad55 on 2009-02-18
It's great news you found a solution to your problem .. I was away from my computer for awhile .. Thanks caljohnsmith for your help with this ..Best to you all

---

