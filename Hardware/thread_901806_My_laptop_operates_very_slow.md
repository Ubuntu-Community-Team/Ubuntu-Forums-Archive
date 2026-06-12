---
title: "My laptop operates very slow"
date: 2008-08-26
forum: Hardware
---

### Post by alSee on 2008-08-26
I have Sony Vaio SRX3 with Celeron 650 MHz, 256 Mb RAM (not upgradable), 40 Gb IDE HDD. Since it has quite low performance I've installed Xubuntu Hardy 8.04.1 (specially designed for slow computers). There was Windows XP before.
Now I have very slow laptop even comparing to Windows.
Let's look at comparison table where 1st column is for WinXP and 2nd one is or Xubuntu:

boot up            45s   3m30s
turn to standby    15s    1m
wake up             3s    4-5m

How to ix it?

---

### Post by Crafty Kisses on 2008-08-26
Post the results of this command > top

---

### Post by alSee on 2008-08-29
Okay, here it is
```

top - 03:33:39 up 8 min,  2 users,  load average: 0.17, 0.48, 0.37
Tasks: 102 total,   1 running, 101 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.3%us,  0.7%sy,  0.0%ni, 94.7%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    254140k total,   248576k used,     5564k free,     1920k buffers
Swap:  1052248k total,    38096k used,  1014152k free,    65892k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                           
 4809 root      20   0  109m  21m 8600 S  5.3  8.8   0:19.76 Xorg                                                                              
 5586 alsee     20   0 28424  13m 6976 S  2.0  5.3   0:09.32 xfce4-mixer-plu                                                                   
 5581 alsee     20   0 17416 8884 6072 S  0.7  3.5   0:03.46 xfce4-cpugraph-                                                                   
 5692 alsee     20   0 60388  17m 9908 S  0.7  7.1   0:01.06 roxterm                                                                           
 5828 alsee     20   0  2304 1104  852 R  0.7  0.4   0:00.14 top                                                                               
    1 root      20   0  2844 1688  544 S  0.0  0.7   0:02.62 init                                                                              
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                          
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                       
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0                                                                       
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                        
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 events/0                                                                          
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                                                           
   41 root      15  -5     0    0    0 S  0.0  0.0   0:00.04 kblockd/0                                                                         
   44 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                                            
   45 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                      
  116 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                                           
  147 root      20   0     0    0    0 S  0.0  0.0   0:00.02 pdflush                                                                           
  148 root      20   0     0    0    0 S  0.0  0.0   0:00.02 pdflush                                                                           
  149 root      15  -5     0    0    0 S  0.0  0.0   0:00.18 kswapd0                                                                           
  192 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                             
 1357 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                     
 1360 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                             
 1387 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0                                                                             
 1390 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                           
 1406 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                         
 1410 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_1                                                                         
 1440 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                          
 1484 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                       
 2203 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_2                                                                         
 2205 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 usb-storage                                                                       
 2339 root      15  -5     0    0    0 S  0.0  0.0   0:00.02 kjournald                                                                         
 2541 root      16  -4  2220  716  380 S  0.0  0.3   0:01.72 udevd                                                                             
 2840 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 sony-laptop                                                                       
 2874 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd                                                                           
 2883 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd                                                                           
 2886 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                         
 3761 root      18  -2  3876  884  612 S  0.0  0.3   0:00.04 wpa_supplicant                                                                    
 3978 root      20   0  3808  932  552 S  0.0  0.4   0:00.00 mount.ntfs-3g                                                                     
 4053 dhcp      18  -2  2440  552  228 S  0.0  0.2   0:00.00 dhclient3                                                                         
 4183 daemon    20   0  1832  524  428 S  0.0  0.2   0:00.00 portmap                                                                          
```

---

### Post by nicedude on 2008-08-29
These aren't speed figures they are boot times and suspend resume times so that says nothing about XP being anything except faster to boot or wake up not that it is faster in operation in any way. You could try installing bootchart to see what is taking so long to bootup and then correct it. For starters you should look at some guides on turning off services in Xubuntu that you don't need as there are probably several you could ditch with no ill effects and increased boot speed and running speed.

Here is the command to install bootchart

sudo apt-get install bootchart

Once it is installed read its manual with the following command to see how it works as it automatically makes nice charts at boot time and then you can look at them, the directory they are deposited in will be in the manual

command to open the manual

man bootchart

Also your specs are pretty weak so you might want to look at fluxbox which you could install and use instead of XFCE which is the default Xubuntu desktop environment and instead use the fluxbox one ( it  is wicked fast ). But it does take some learning to config ure it the way you want but there is info on the fluxbox webpage on how to do everything.
 
Hope that helps you figure out what is going on and learn some stuff in the process.

---

### Post by alSee on 2008-08-31
> **nicedude said:**
> Also your specs are pretty weak so you might want to look at fluxbox which you could install and use instead of XFCE which is the default Xubuntu desktop environment and instead use the fluxbox one ( it  is wicked fast )
It is a great surprise for me! When I installed Mandrake several years ago I've read something like "Linux with X demands only 64 Mb RAM instead of Windows XP that is recomended 128 Mb minimum". And what now? 256 Mb is quite enough for XP and "pretty weak" for XFCE under Linux!
Otherwise my Nokia N800 (with 256 Mb RAM and 400 MHz ARMel) runs Debian with XFCE quite usable.
I think my problem is not weak configuration fault.
Thanks, **nicedude**, for advices, I'll try to find out the cause of problem.

---

### Post by HotCupOfJava on 2008-08-31
Your results seem strange to me.....I have Xubuntu on a 10-year-old E-Machine 500 MHZ Celeron 256M RAM. It was running Windows 98 before and Xubuntu Hardy is WAY a better performer on it......I'm not saying you're lying, because I don't think you are, but I wonder what the difference is......

---

### Post by nicedude on 2008-08-31
I didn't mean they wouldn't work or even work well and 256MB of RAM is plenty but the celeron 650mhz is probably no firecracker of performance. I just meant that fluxbox is even faster desktop than XFCE and if your laptop does not run that fast with XFCE then you could at least try it and see if it is not more to your expectations. You wouldn't even have to reinstall or anything as fluxbox is in the repositories and you would just need to install it and then choose it for your default desktop session. That would let you see the difference without having to do more than 2 minutes work :-)

---

### Post by IntuitiveNipple on 2008-08-31
I've run Ubuntu (Gnome version) fine on Sony Vaio SRX41 (256MB) and SRX51 (384MB). It sounds as if there's something causing prolonged time-outs which is making many actions take so long.

Can you attach a copy of the most recent **/var/log/kern.log**? You'll need to compress it to attach it:
```

cd ~
copy /var/log/kern.log .
gzip kern.log
ls kern*

 kern.log.gz

```
Now attach that file so we can look for clues.

---

### Post by alSee on 2008-09-02
Here is my log.
It is strange but last 2 times my note has booted quite fast.
But for example see the log at Aug 19 19:32:54 till Aug 19 19:37:32 - it is almost 5 minutes of booting!
> It sounds as if there's something causing prolonged time-outs which is making many actions take so long.
You're right. During boot sometimes everything stops for some seconds and then continues.

I guess if my problem is related to [laptop harddrive Load_Cycle_Count issue]("http://ubuntuforums.org/showthread.php?t=805570")?

---

### Post by Whiffle on 2008-09-02
I'd check your hard drive speeds, I wouldn't be at all surprised to learn that DMA isn't enabled due to some controller issue.

Try:

sudo hdparm -Tt /dev/sda

and post up the results.

---

### Post by alSee on 2008-09-02
> **Whiffle said:**
> I'd check your hard drive speeds, I wouldn't be at all surprised to learn that DMA isn't enabled due to some controller issue.


It also surprises me, especially that "hdparm -d1" doesn't work.
This is what you've asked:
```
$ sudo hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   188 MB in  2.00 seconds =  93.98 MB/sec
 Timing buffered disk reads:   28 MB in  3.05 seconds =   9.19 MB/sec

```

When I had PIO-mode only problem on my work PC it had 2 Mb/s. The laptop is faster but not so much it's supposed to be.

---

### Post by Whiffle on 2008-09-02
What error do you get when you do 

sudo hdparm -d1 /dev/sda


I'm not real up on my "average speeds", but that might be as good as you're going to get on hard drive speed.

---

### Post by alSee on 2008-09-02
> **Whiffle said:**
> What error do you get when you do 

```
$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

---

### Post by Whiffle on 2008-09-02
Ahh thats juicy.  I've gotten that before but I don't remember when.  Post up

sudo lspci -v

---

### Post by alSee on 2008-09-02
```
$ sudo lspci -v
[sudo] password for alsee: 
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
	Subsystem: Sony Corporation Unknown device 80f2
	Flags: bus master, fast devsel, latency 0
	Capabilities: [88] Vendor Specific Information

00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11) (prog-if 00 [VGA controller])
	Subsystem: Sony Corporation Unknown device 80f2
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 9
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Memory at f4000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [dc] Power Management version 2

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=09, sec-latency=64
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: f4100000-f41fffff

00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
	Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03) (prog-if 80 [Master])
	Subsystem: Sony Corporation Unknown device 80f2
	Flags: bus master, medium devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at 1800 [size=16]

00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 80f2
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1820 [size=32]

00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 80f2
	Flags: medium devsel, IRQ 9
	I/O ports at 1810 [size=16]

00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Sony Corporation Unknown device 80f2
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 2400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
	Subsystem: Sony Corporation Unknown device 80f2
	Flags: bus master, medium devsel, latency 0, IRQ 9
	I/O ports at 1c00 [size=256]
	I/O ports at 1840 [size=64]

00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03) (prog-if 00 [Generic])
	Subsystem: Sony Corporation Unknown device 80f2
	Flags: medium devsel, IRQ 9
	I/O ports at 2000 [size=256]
	I/O ports at 1880 [size=128]

01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02) (prog-if 10 [OHCI])
	Subsystem: Sony Corporation Unknown device 80f2
	Flags: bus master, medium devsel, latency 64, IRQ 9
	Memory at f4101000 (32-bit, non-prefetchable) [size=2K]
	Memory at f4104000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2

01:02.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
	Subsystem: Sony Corporation Unknown device 80f2
	Flags: bus master, medium devsel, latency 168, IRQ 9
	Memory at f4102000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=02, subordinate=05, sec-latency=176
	Memory window 0: 20000000-23fff000 (prefetchable)
	Memory window 1: 24000000-27fff000
	I/O window 0: 00003400-000034ff
	I/O window 1: 00003800-000038ff
	16-bit legacy interface ports at 0001

01:05.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
	Subsystem: Lucent Technologies Unknown device ab01
	Flags: bus master, medium devsel, latency 168, IRQ 9
	Memory at f4103000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=01, secondary=06, subordinate=09, sec-latency=176
	Memory window 0: 28000000-2bfff000 (prefetchable)
	Memory window 1: 2c000000-2ffff000
	I/O window 0: 00003c00-00003cff
	I/O window 1: 00001400-000014ff
	16-bit legacy interface ports at 0001

01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
	Subsystem: Intel Corporation EtherExpress PRO/100 VE
	Flags: bus master, medium devsel, latency 66, IRQ 9
	Memory at f4100000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 3000 [size=64]
	Capabilities: [dc] Power Management version 2

```

---

### Post by IntuitiveNipple on 2008-09-02
I've looked at the kern.log file, and it raises a question. Does this slow-down occur after starting from cold, or only after resuming from suspend?

The initial start-up looks good:
```

[   20.403862] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1800 irq 14
[   20.403873] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1808 irq 15
[   20.565030] ata1.00: ATA-5: IC25N040ATCS04-0, CA4OA71A, max UDMA/100
[   20.565045] ata1.00: 78140160 sectors, multi 16: LBA 
[   20.580999] ata1.00: configured for UDMA/100
[   20.581094] ata2: port disabled. ignoring.
[   20.581448] scsi 0:0:0:0: Direct-Access     ATA      IC25N040ATCS04-0 CA4O PQ: 0 ANSI: 5

```

---

### Post by in-dust-rial on 2008-09-02
once windows XP was very slow on my (back then) 3 years old LapTop.
just moved the insatllation to a nother partition, that worked.
issue was that some part of the HD had very bad transfere rates! (found out later in linux) less than 0.25mb/s or something!

so maybe you should try a second install in a nother place, if noone can help you here.

good luck

---

### Post by IntuitiveNipple on 2008-09-02
I just noticed this:
```

[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"

```
Looking through the interrupt assignments more closely it looks like there could be some interrupt-sharing that might cause this.

Try adding "lapic" to the kernel command-line during boot, from the GrUB menu. If that helps then add it permanently to /boot/grub/menu.lst entries, and to the default entry so it is added to kernel entries when the file is updated.

---

### Post by IntuitiveNipple on 2008-09-02
> **alSee said:**
> ```
$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device

```

Don't be concerned about this. The report is generated since all fixed disks are now handled through the SCSI layer and so hdparm cannot find the IDE-specific I/O Control functions for handling DMA on the device.

---

### Post by alSee on 2008-09-03
> **IntuitiveNipple said:**
> Try adding "lapic" to the kernel command-line during boot, from the GrUB menu. If that helps then add it permanently to /boot/grub/menu.lst entries, and to the default entry so it is added to kernel entries when the file is updated.

I've added "lapic" option and it seems nothing changed. Slow boot occurs while either cold starting up or resuming from suspend.
Installing fluxbox doesn't help: the laptop starts slow even before logon screen appeared. Also applications start for a long time.
And HDD operates strange: about 0.5s of transferring then 0.5s of waiting and so on.

Maybe it is related to [laptop harddrive Load_Cycle_Count issue]("http://ubuntuforums.org/showthread.php?t=805570")?

---

