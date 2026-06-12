---
title: "System becomes unresponsive during file transfer"
date: 2009-05-17
forum: Hardware
---

### Post by job on 2009-05-17
During large file transfers, my system becomes very unresponsive (read: completely unusable): ie Konqueror takes around 5 seconds to start and even clicking on a link or button takes a couple of seconds to react.

The strange thing is: I get quite respectable speeds on my disks:

```

$ sudo hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   2096 MB in  2.00 seconds = 1047.80 MB/sec
 Timing buffered disk reads:  234 MB in  3.00 seconds =  77.99 MB/sec

$ sudo hdparm -tT /dev/sdb
/dev/sdb:
 Timing cached reads:   2094 MB in  2.00 seconds = 1047.36 MB/sec
 Timing buffered disk reads:  268 MB in  3.01 seconds =  89.17 MB/sec

```

I also tested all my partitions with bonnie++ and the results seemed ok too.

I'm running Kubuntu Jaunty, and here's some more info on my system:

```

$ uname -a
Linux squatpc 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

$ sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00031f81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3736    30009388+  83  Linux
/dev/sda2            4983       19457   116270437+  83  Linux
/dev/sda3            3737        4359     5004247+  83  Linux
/dev/sda4            4360        4982     5004247+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe24a8dcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

```

The slowdown seems to be most problematic when copying/moving between the two disks although it is noticeable with transfers on the same partition.

Does anybody have an idea on how to pinpoint the cause of this problem? I don't know if I gave all relevant information so please let me know if not.

Thanks in advance!
Job

---

### Post by moster on 2009-05-17
Maybe you should give us result of something like "sudo hdparm -I /dev/sda1"

There is maybe answer for problem...

---

### Post by job on 2009-05-17
I have attached the output of hdparm -I for both my drives since the output is a little too verbose to post:)

The most relevant part (I think) is the same for both:

DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6

So DMA seems to be working.

---

### Post by moster on 2009-05-17
Hm, everything seems fine. I guess we need some hacker to solve this one :)
Strange nobody reply yet...

---

### Post by khelben1979 on 2009-05-17
Have you tried experimenting with changing priority of your different programs?

```
man renice
```
for more information on how to use the command.

---

### Post by moster on 2009-05-17
Can you post exactly what hardware you have, chipset and stuff... post what say "lspci" too.

Hope you will not have to make sacrifice in blood to get this done :)

---

### Post by job on 2009-05-18
Thanks all for your replies!

```

$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
05:00.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
05:01.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
05:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)

```

Any other hardware info I have to give?

About renicing some processes: that seems more like a workaround than a solution. I gave Konqueror as an example of an unresponsive application but in fact, the whole desktop is unusable. So I think this would mean having to renice Plasma/KWin/X/$ALL_MY_APPS which doesn't sound like a good idea (correct me if I'm wrong).

What I was wondering: am I the only one experiencing this problem?

---

### Post by moster on 2009-05-18
It should work excellent but it doesn't.. hm.. You need help of highr force I guess :)

    You could post also "dmesg" and "lsmod" so if any hacker comes around he/she(?) will know exactly what you have in computer.

---

### Post by job on 2009-05-18
Hi moster, thanks for all your replies! I really appreciate it! But it's starting to look like you're right: I will need some higher force to fix this:)

Anyway, I've attached the output of lsmod and the output of dmesg can be found [here]("http://lei23.homelinux.org/~job/dmesg.txt") (too large to upload on this forum), let's hope somebody can find a problem here.

---

### Post by moster on 2009-05-24
I see that you are using "ata_piix" kernel SATA driver. If you can enable in BIOS "AHCI" then kernel will use different driver for disk and possible solve your problem. But there is catch, you cannot boot after that to linux or windows without reinstall (at least from my knowledge). But, you can boot to live ubuntu form USB stick and do some copying and see if something is different, then change back :)

Inspect before and after with "lspci -v". Here is part of my listing...

```
...
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 8179
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at ffa0 [size=16]
	Kernel driver in use: ata_piix
...

```

You see driver "ata_piix" in last line, after you change in BIOS there should be "ahci".

Before I was trying to do that for myself (because NCQ) but my motherboard is not so advanced, I cannot enable it for myself.
If you have time and will, it will be a honest try.

here is some link too..
[http://linux-ata.org/driver-status.html]("http://linux-ata.org/driver-status.html")

---

### Post by job on 2009-05-25
Hi moster. I enabled AHCI in my BIOS and it really made a big difference:) I still experience a slowdown during large transfers but my system is usable again.

A nice side note: I did not need to reinstall:)

Again, thanks a lot for your help!

---

### Post by moster on 2009-07-13
OMG, this is more serious bug then I thought.
[http://bugzilla.kernel.org/show_bug.cgi?id=12309]("http://bugzilla.kernel.org/show_bug.cgi?id=12309")

---

