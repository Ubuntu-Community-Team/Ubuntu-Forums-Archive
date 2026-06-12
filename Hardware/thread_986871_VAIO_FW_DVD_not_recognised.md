---
title: "VAIO FW DVD not recognised"
date: 2008-11-19
forum: Hardware
---

### Post by pinegreen on 2008-11-19
HI,

I installed ubunuto on my VAIO fw and after kenel upgrade (I think), it stopped being recognised. If I boot from CD, everything is fine, so I compared dmesg outputs when booting from CD or hard drive. The only significat differences are:

A) LINUX VERSION (note ubuntu10 vs ubuntu11)

 < Linux version 2.6.27-7-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:06 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
< Command line: root=UUID=191e5789-fddd-4167-9b7c-0cff8df867c6 ro quiet splash 
---
> Linux version 2.6.27-7-generic (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:40:41 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
> Command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --

B)

ata2.00: ATAPI: PIONEER DVD-RW  DVRTD08, 1.00, max UDMA/33
ata2.00: qc timeout (cmd 0xef)
ata2.00: failed to set xfermode (err_mask=0x4)
ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
ata2.00: qc timeout (cmd 0xef)
ata2.00: failed to set xfermode (err_mask=0x4)
ata2: limiting SATA link speed to 1.5 Gbps
ata2.00: limiting speed to UDMA/33:PIO3
ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
ata2.00: qc timeout (cmd 0xef)
ata2.00: failed to set xfermode (err_mask=0x4)
ata2.00: disabled

vs 

ata2.00: ATAPI: PIONEER DVD-RW  DVRTD08, 1.00, max UDMA/33
ata2.00: configured for UDMA/33



Any ideas? As far as I can tell, nothing ide related has changed from ubuntu10 to ubuntu11. Moreover, none of the irqpoll, acpi=off, etc tricks seemed to work. Any ideas?

---

### Post by pinegreen on 2008-11-19
Just downgraded to ubuntu10 - doesn't help, so it is not the kernel version. Then I am really lost as dmesgs are really quite identical modulo different calib values and different ordering of USB devices being detected... Boooo.

---

### Post by mike_me on 2008-11-21
hi,

I have the same problem with a vaio vgn-ns11s. I installed intrepid from a xubuntu-alternate iso. After a reboot the CD was not recognised. I searched hours at google - nothing helped. I tried vanilla kernels 2.6.27.7 and 2.6.28.rc6 same effect. Some minutes ago I tried to boot with a data CD in the drive and ! the drive was recognised!!! I tried also a blank CD and the drive was also recognised!

xubuntu-8.10-alternate: Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
 kernel: [ 3.720097] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
 kernel: [ 3.721752] ata2.00: ATAPI: PIONEER DVD-RW DVRTD08, 1.00, max UDMA/33
 kernel: [ 3.723836] ata2.00: configured for UDMA/33

installed inrepid:Linux version 2.6.27-7-generic (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Tue Nov 4 19:33:20 UTC 2008 (Ubuntu 2.6.27-7.16-generic)
 [ 4.172095] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
 [ 4.183732] ata2.00: ATAPI: PIONEER DVD-RW DVRTD08, 1.00, max UDMA/33
 [ 9.180085] ata2.00: qc timeout (cmd 0xef) [ 9.180094] ata2.00: failed to set xfermode (err_mask=0x4)
 [ 9.500111] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
 [ 19.512102] ata2.00: qc timeout (cmd 0xef) [ 19.512110] ata2.00: failed to set xfermode (err_mask=0x4)
 [ 19.512115] ata2: limiting SATA link speed to 1.5 Gbps
 [ 19.512117] ata2.00: limiting speed to UDMA/33:PIO3
 [ 19.832094] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
 [ 29.844087] ata2.00: qc timeout (cmd 0xef) [ 29.844096] ata2.00: failed to set xfermode (err_mask=0x4)
 [ 29.844150] ata2.00: disabled [ 29.860100] ata2: hard resetting link
 [ 30.180109] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
 [ 30.180114] ata2: EH complete

---

### Post by pinegreen on 2008-11-22
This indeed works! Thanks!
(how come didn't I think of this?!)

---

### Post by mike_me on 2008-11-24
After a restart I got the same timeout error.
A poweroff and poweron function well.

---

### Post by sonyVaioVGN-NS11S on 2008-12-21
See also:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/299865](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/299865)
[http://ubuntuforums.org/showthread.php?p=6410330#post6410330](http://ubuntuforums.org/showthread.php?p=6410330#post6410330)

No solution there either. (I don't think having to boot with a CD in the drive is a solution).

---

### Post by sonyVaioVGN-NS11S on 2008-12-21
I have made some progress on this bug (though no solution yet).
When the drive works (after booting with an inserted cd)

sudo lsmod | grep cd

gives

cdrom                  43168  1 sr_mod

whereas it has nothing of the kind when no cd was in the drive.

Therefore, I added 
cdrom
sr_mod
to /etc/modules

When, I now boot without CD in the drive I get the following error
ata2.0 failed to set xfermode (err_mask=0x4)
which seems to be a rather widespread error


The drive still is not working. I am going to try to add 'irqpoll' as a boot option, which is reported to fix the xfermode error.

---

### Post by sonyVaioVGN-NS11S on 2008-12-21
irqpoll did not help, cdrom still gets disabled when there is no cd in the drive at boot time. Here is the output of dmesg | grep ata2 for both cases.

Without disc:
```
$ dmesg | grep ata2
[    3.715535] ata2: SATA max UDMA/133 abar m2048@0xd3e04000 port 0xd3e04180 irq 218
[    4.368166] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.380063] ata2.00: ATAPI: PIONEER DVD-RW  DVRTD08, 1.00, max UDMA/33
[    9.380102] ata2.00: qc timeout (cmd 0xef)
[    9.380112] ata2.00: failed to set xfermode (err_mask=0x4)
[    9.700093] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   19.712097] ata2.00: qc timeout (cmd 0xef)
[   19.712105] ata2.00: failed to set xfermode (err_mask=0x4)
[   19.712158] ata2: limiting SATA link speed to 1.5 Gbps
[   19.712160] ata2.00: limiting speed to UDMA/33:PIO3
[   20.032106] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   30.040084] ata2.00: qc timeout (cmd 0xef)
[   30.040091] ata2.00: failed to set xfermode (err_mask=0x4)
[   30.040144] ata2.00: disabled
[   30.056102] ata2: hard resetting link
[   30.376108] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   30.376114] ata2: EH complete
```

With disc:
```
[    3.804304] ata2: SATA max UDMA/133 irq_stat 0x00000040, cirq 219
[    5.268599] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.270213] ata2.00: ATAPI: PIONEER DVD-RW  DVRTD08, 1.00, max UDMA/33
[    5.272217] ata2.00: configured for UDMA/33

```

---

### Post by sonyVaioVGN-NS11S on 2008-12-21
Tried boot option all_generic_ide, and it did not help.
Here's another thread about the same issue (in German):

[http://forum.ubuntuusers.de/topic/brenner-wird-nicht-richtig-erkannt/](http://forum.ubuntuusers.de/topic/brenner-wird-nicht-richtig-erkannt/)

---

### Post by sonyVaioVGN-NS11S on 2008-12-29
There's a (preliminary) patch for this problem in the linux-ide mailing-list

Thread:
[http://thread.gmane.org/gmane.linux.ide/36790/focus=36819](http://thread.gmane.org/gmane.linux.ide/36790/focus=36819)

Post with Patch:
[http://article.gmane.org/gmane.linux.ide/36833](http://article.gmane.org/gmane.linux.ide/36833)

---

### Post by thunk77 on 2009-03-24
bump?

Any progress on the subject? The issue persists in jaunty alpha 6.

---

### Post by sonyVaioVGN-NS11S on 2009-03-25
Hi thunk77,
I tried to get the libata people to do something about this. The last post on the subject that I know of is [http://article.gmane.org/gmane.linux.ide/37388](http://article.gmane.org/gmane.linux.ide/37388). Maybe it would be helpful if you sent another email to the linux-ide mailing list just to make it clear that it's not just me who's still waiting for a fix.

---

### Post by thunk77 on 2009-03-26
Will do.

For now, here's a solution!

Just yesterday while playing around trying to get the damn thing to work, I upgraded a Hardy installation via network to Intrepid with a data cd in the drive. Guess what? The DVD drive is now fully functional!

Can't say what happened, haven't looked at logs or anything yet.

Can you confirm that this works?

---

### Post by Ro86 on 2009-05-09
I upgraded from Intrepid to Jaunty with a data disc in the dvd drive but it didn't resolve this issue. Neither did a fresh install of Jaunty.

However at startup there is now the following error if I don't have a disc in my dvd drive:
"Ata2.00 failed to set xfermod (err_mask=0x4)"

---

