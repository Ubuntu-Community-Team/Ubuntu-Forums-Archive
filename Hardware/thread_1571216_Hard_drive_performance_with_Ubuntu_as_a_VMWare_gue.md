---
title: "Hard drive performance with Ubuntu as a VMWare guest"
date: 2010-09-09
forum: Hardware
---

### Post by jonathanhaddock on 2010-09-09
Hello,

I have a webserver running Apache2, MySQL and PHP base on Ubutnu Server Lucid 64bit:

Linux vlewww 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux

This runs in a VMWare (ESXi 4.0) VM on a dual Xeon, 14Gb RAM host connected to an HP SAN but the disk performance in Ubuntu is dreadful:

```

technician@vlewww:~$ sudo hdparm -t /dev/sdb
[sudo] password for technician:

/dev/sdb:
 Timing buffered disk reads:   22 MB in  3.22 seconds =   6.84 MB/sec
technician@vlewww:~$ sudo hdparm -t /dev/sda

/dev/sda:
 Timing buffered disk reads:   38 MB in  3.35 seconds =  11.34 MB/sec


```

(As a rough guide, my Gentoo based linux box at home gives me " Timing buffered disk reads:  356 MB in  3.00 seconds = 118.67 MB/sec")

When I try to do hdparm -iI /dev/sda I get errors:
```

technician@vlewww:~$ sudo hdparm -iI /dev/sda

/dev/sda:
 HDIO_DRIVE_CMD(identify) failed: Invalid exchange
 HDIO_GET_IDENTITY failed: Invalid argument

```

Any ideas?  I think it's disk access in the linux environment that is slowing down the use of our websites (Moodle runs on this server, as does a home written website - nothing else).

Thanks in advance,

Jonathan

---

### Post by jonathanhaddock on 2010-09-09
Forgot to add, I'm seeing this in /var/log/kern.log:

```

Sep  9 12:19:04 vlewww kernel: [159343.384852] BUG: soft lockup - CPU#0 stuck for 65s! [jbd2/sda1-8:286] Sep  9 12:19:04 vlewww kernel: [159384.289969] Modules linked in: fbcon tileblit font bitblit ppdev softcursor parport_pc psmouse intel_agp vga16fb shpchp lp vgastate i2c_piix4 serio_raw parport mptspi pcnet32 mptscsih mii mptbase floppy Sep  9 12:19:04 vlewww kernel: [159384.289969] CPU 0:
Sep  9 12:19:04 vlewww kernel: [159384.289969] Modules linked in: fbcon tileblit font bitblit ppdev softcursor parport_pc psmouse intel_agp vga16fb shpchp lp vgastate i2c_piix4 serio_raw parport mptspi pcnet32 mptscsih mii mptbase floppy Sep  9 12:19:04 vlewww kernel: [159384.289969] Pid: 286, comm: jbd2/sda1-8 Not tainted 2.6.32-21-

```

---

