---
title: "futex.c but in unqueue_me()?  Thoughts?"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by dannysauer on 2007-01-21
I have a mythtv box that is presently sitting with a load average of 2.something until it eventually crashes, and the process taking most of the CPU is klogd.  I looked at the output of dmesg, and it;s apparently spewing these four lines over and over:

```
[17352368.720000] BUG: warning at kernel/futex.c:616/unqueue_me()
[17352368.720000]  <c01397cc> unqueue_me+0x8c/0x90  <c013a493> do_futex+0x7b3/0x9d0
[17352368.720000]  <c0173160> blkdev_open+0x0/0x60  <c0172dfc> do_open+0x1cc/0x320
[17352368.720000]  <c011bde0> default_wake_function+0x0/0x10  <c013a738> sys_futex+0x88/0x100
[17352368.720000]  <c0102fbb> sysenter_past_esp+0x54/0x79
```

Different timestamps, but the same message.  It's averaging around 23 of them every .004 seconds, which as one might guess, is a little hard on the machine (which is still quite responsive, even though it's just a P3-800 w/ 256MB RAM).  I last rebooted 2 days ago, and I've got this in the ps output:

[FONT="Lucida Console"]```
 3607 ?        Ss   247:17 /sbin/syslogd
 3626 ?        Rs   1040:33 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 3628 ?        Rs   1109:48 /sbin/klogd -P /var/run/klogd/kmsg
```[/FONT]

My poor, unsuspecting CPU can't be happy about this. :)

Anyway, it happens after I reboot, too.  I'm currently running edgy, and had the same proble, with the 386 kernel (which the nvidia glx driver depends on), or with the generic kernel running now.  I rebuilt the nvidia kernel module for this kernel, using module-assistant and the Ubuntu source package.  The kernel error includes mention of a block device, so it's relevant to note that I'm using a Promise ATA-133 card for one ATA-100 hard drive, and I'm using the on-board IDE controller for the boot drive and CD ROM.  The motherboard is an Intel slot-1 server board (I forget the exact model), so one can pretty well rule out cheap-board flakiness there, but I wonder about the drives (one is a Western Digital POS) and that Promise board, since WD and Promise aren't exactly known for their consistent rock-solid reliability.

So, anyone have any idea what's going on here, or how to better track it down?  It doesn't happen immediately on boot, but pretty consistently does after "a while".

For entertainment value, here's some diagnostic output...

[FONT="Lucida Console"]```
sauer@stinky:~$ uname -a
Linux stinky 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

sauer@stinky:~$ mount -l
/dev/mapper/Ubuntu-root on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hdc1 on /boot type ext3 (rw) []
/dev/mapper/Ubuntu-movies on /opt/mythtv/movies type xfs (rw) [movies]
/dev/mapper/Ubuntu-recordings on /opt/mythtv/recordings type xfs (rw) [recordings]

sauer@stinky:~$ sudo pvs
  PV         VG     Fmt  Attr PSize   PFree
  /dev/hdc6  Ubuntu lvm2 a-     3.05G     0
  /dev/hde   Ubuntu lvm2 a-   186.31G 86.31G
sauer@stinky:~$ sudo vgs
  VG     #PV #LV #SN Attr   VSize   VFree
  Ubuntu   2   3   0 wz--n- 189.36G 86.31G
sauer@stinky:~$ sudo lvs
  LV         VG     Attr   LSize  Origin Snap%  Move Log Copy%
  movies     Ubuntu -wi-ao 50.00G
  recordings Ubuntu -wi-ao 50.00G
  root       Ubuntu -wi-ao  3.05G

sauer@stinky:~$ sudo hdparm -i /dev/hdc /dev/hde

/dev/hdc:

 Model=WDC AC34300L, FwRev=21.10N21, SerialNo=WD-WT4732943391
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=8896/15/63, TrkSize=57600, SectSize=600, ECCbytes=22
 BuffType=DualPortCache, BuffSize=256kB, MaxMultSect=16, MultSect=off
 CurCHS=8896/15/63, CurSects=8406720, LBA=yes, LBAsects=8406720
 IORDY=on/off, tPIO={min:160,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3

 * signifies the current active mode


/dev/hde:

 Model=ST3200827A, FwRev=3.AAH, SerialNo=4ND32H24
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=8192kB, MaxMultSect=16, MultSect=off
 CurCHS=65535/1/63, CurSects=4128705, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

sauer@stinky:~$ sudo smartctl -H /dev/hdc
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED
sauer@stinky:~$ sudo smartctl -H /dev/hde
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

sauer@stinky:~$ sudo smartctl -l selftest /dev/hde
smartctl version 5.36 [i686-pc-linux-gnu] Copyright (C) 2002-6 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      1446         -

```[/FONT]

---

