---
title: "Very Slow  (1mb/s) USB transfer speeds"
date: 2011-10-08
forum: Hardware
---

### Post by davethewave83 on 2011-10-08
A couple weeks ago my external 500GB western digital USB drive started acting sickly, making noises and clicking, not accessing fast or mounting fast at all (on any OS) so I RMA'd it and they sent me another drive, the drive the sent me was working great! 28-30Mb/s transfer but then after a couple days it suddenly was transferring at 1mb/s

I format
repartitioned
tried different file tables
used spinrite until I lost patience (it was accessing extremely slow but no errors) 
read the smart data (no problems) 
benchmarked it in windows in between all of this and the benchmark shows that it acccesses at a very erratic speed. 

I can't imagine it's a bad drive already, after a couple days of use, the last drive that gave out lasted way longer. 

any ideas on how to fix this? 

I'm using USB 2.0 with USB 2.0 drivers, it should be faster than this shouldn't it? 

There are no read errors, no bad blocks, just slow. 


I contacted Western Digital and they usually reply fast, but this time they seem to be taking their time ;) 

[IMG]http://www.mediafire.com/imgbnc.php/294ffe52eb2ce0a8927cf0e8a53869a897f67f2a0aa57d152ca1bd4cb93a568d5g.jpg[/IMG]

I'm using Teracopy on my Windows box to transfer a 135GB file. It says it will take 2 days to complete and is going 500kb/s, up to 1.5MB/s and back down again. It's been transferring already for about 12 hours.

---

### Post by diasf on 2011-10-08
Same behaviour on another pc?
What about another drive on the same pc?

---

### Post by matt_symes on 2011-10-08
Hi

If you can't check it in another computer then check the discs SMART status. You can use disc utility for this or from the command line use

```
smartctl
```Check the man pages for usage instructions. Perform an extended test.

To install it

```
sudo apt-get install smartmontools
```You have it connected to a USB2 port ?

Plug the device in, open a terminal and type

```
dmesg | tail -n25
```Post the results back here between code tags. This will tell us how the system is viewing the device when plugged in.

Kind regards

---

### Post by davethewave83 on 2011-10-08
> **diasf said:**
> Same behaviour on another pc?
What about another drive on the same pc?

I don't have another drive the same type, but my USB Flash 2Gb drive is speedy.
[IMG]http://www.mediafire.com/imgbnc.php/95e0ff55fd664ad2a7edd4ed20de0a4b2a945951b6fc3e54de79b59072a4badc5g.jpg[/IMG]


The only ports my computers have are USB 2.0, I've uninstalled the drivers and let them re-install, no difference.

I just reflashed the firmware from the WD download site. I thought maybe it'd help but it didn't. same erratic behavior.

---

### Post by davethewave83 on 2011-10-08
I wrote WD and they said to do a full disk check on it. The problem with that is it's not bad sector related. They said if there's no issues then the drive isn't at fault. but what would it be then? I don't understand.

---

### Post by matt_symes on 2011-10-09
Hi

Plug the device in, open a terminal and type
```
dmesg | tail -n25
``` Copy and paste the results back here between code tags. This will tell us how the system is viewing the device when plugged in.

Kind regards

---

### Post by davethewave83 on 2011-10-09
> **matt_symes said:**
> Hi

Plug the device in, open a terminal and type
```
dmesg | tail -n15
``` Copy and paste the results back here between code tags. This will tell us how the system is viewing the device when plugged in.

Kind regards

alright it'll have to wait 60hours at least though. WesternDigital wanted me to do the extended test on the drive and it says 60hours remaining, 5hours elapsed. 

once that's done I'll take it to my ubuntu box and do the dmesg command. I'm pretty sure Western Digital is just wasting time with this test, it'll come back clean I'm thinking because it has nothing to do with bad sectors, just how it's operating for some reason it's slow.

if any of you have a brand you could suggest that you stand by and like let me know in a pm if you could :)

---

### Post by matt_symes on 2011-10-09
Hi

No problem. 60 hours ? Ouch!

Post the results when it's finished.

Kind regards

---

### Post by davethewave83 on 2011-10-10
> **matt_symes said:**
> Hi

No problem. 60 hours ? Ouch!

Post the results when it's finished.

Kind regards

well, looking at the benchmark chart it makes sense, it's slower at the start of the drive, once it got past 24hrs it sped up a bit and completed sooner than 60 hours. What are we looking for here?

here's the results:

```
[   83.209537] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   83.209546] HDA Intel 0000:00:14.2: power state changed by ACPI to D0
[   83.209557] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   83.761546] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   83.761552] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   83.761556] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   83.794153] hda_codec: ALC268: BIOS auto-probing.
[   83.968126] input: HDA ATI SB Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   94.132575] lp: driver loaded but no devices found
[   94.657178] ppdev: user-space parallel port driver
[  159.863067] UDF-fs: Partition marked readonly; forcing readonly mount
[  159.863563] UDF-fs INFO UDF: Mounting volume 'WD Unlocker', timestamp 2010/09/10 17:58 (1000)
[  244.891786] sky2 0000:02:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[  244.892885] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  255.464040] eth0: no IPv6 routers present
[  878.961962] sd 0:0:0:0: [sdb] No Caching mode page present
[  878.961978] sd 0:0:0:0: [sdb] Assuming drive cache: write through
[  878.963235]  sdb:

```

I'm running a live cd right now, so ignore the wireless issues. I plugged in the ethernet and all was good to go. The last three messages appeared only after I started to write to the drive, so I appended them above.

what's funny also, benchmarking using the Linux Disk Utility won't even work, it says 
```
Error benchmarking: helper exited with exit code 1: Device /dev/sdb is too slow to benchmark
```

all the smart self tests passed. a bit further up in the dmesg there's this 

```

    3.142295] scsi 0:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
[    3.144408] scsi 0:0:0:1: CD-ROM            WD       Virtual CD 071A  2019 PQ: 0 ANSI: 4
[    3.146408] scsi 0:0:0:2: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
[    3.147138] sd 0:0:0:0: Attached scsi generic sg2 type 0
[    3.149150] sd 0:0:0:0: [sdb] 976717824 512-byte logical blocks: (500 GB/465 GiB)
[    3.151398] sd 0:0:0:0: [sdb] Write Protect is off
[    3.151405] sd 0:0:0:0: [sdb] Mode Sense: 2b 00 10 08

```

---

### Post by matt_symes on 2011-10-10
Hi

I was hoping for more information from dmesg than given. Did you have the drive plugged in when booting up the LiveCD ? 

Try these steps

1. Umount/unplug the external drive.
2. Plug the drive back in. Wait for 5 seconds.
3. Type 
```
dmesg | tail -n20
```
4. Post that back here.

That should give us all the messages about the drive when it is discovered.

Kind regards

---

### Post by davethewave83 on 2011-10-10
> **matt_symes said:**
> Hi

I was hoping for more information from dmesg than given. Did you have the drive plugged in when booting up the LiveCD ? 

Try these steps

1. Umount/unplug the external drive.
2. Plug the drive back in. Wait for 5 seconds.
3. Type 
```
dmesg | tail -n20
```
4. Post that back here.

That should give us all the messages about the drive when it is discovered.

Kind regards

```
[ 4236.015116] scsi 7:0:0:0: Direct-Access     WD       My Passport 071A 2019 PQ: 0 ANSI: 4
[ 4236.017430] scsi 7:0:0:1: CD-ROM            WD       Virtual CD 071A  2019 PQ: 0 ANSI: 4
[ 4236.019633] scsi 7:0:0:2: Enclosure         WD       SES Device       2019 PQ: 0 ANSI: 4
[ 4236.021951] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 4236.028463] sd 7:0:0:0: [sdb] 976717824 512-byte logical blocks: (500 GB/465 GiB)
[ 4236.030655] sd 7:0:0:0: [sdb] Write Protect is off
[ 4236.030673] sd 7:0:0:0: [sdb] Mode Sense: 2b 00 10 08
[ 4236.034892] sd 7:0:0:0: [sdb] No Caching mode page present
[ 4236.034908] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4236.037033] sr1: scsi3-mmc drive: 51x/51x caddy
[ 4236.037555] sr 7:0:0:1: Attached scsi CD-ROM sr1
[ 4236.037848] sr 7:0:0:1: Attached scsi generic sg3 type 5
[ 4236.038100] ses 7:0:0:2: Attached Enclosure device
[ 4236.038277] ses 7:0:0:2: Attached scsi generic sg4 type 13
[ 4236.048413] sd 7:0:0:0: [sdb] No Caching mode page present
[ 4236.048427] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4236.084423]  sdb: sdb1
[ 4236.102315] sd 7:0:0:0: [sdb] No Caching mode page present
[ 4236.102330] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 4236.102341] sd 7:0:0:0: [sdb] Attached SCSI disk

```

yeah I had it plugged in during boot, the same messages were in the previous just further up, i had to do a dmesg for 200 lines and I saw the same stuff. 

there's all this too if you need it, probably not but here it is anyways, from hdparm

```

[CODE]
/dev/sdb:
 readahead     = 256 (on)
/dev/sdb:
 look-ahead    =  1 (on)
/dev/sdb:
 geometry      = 60797/255/63, sectors = 976717824, start = 0
DCO Revision: 0x0002
The following features can be selectively disabled via DCO:
	Transfer modes:
		 udma0 udma1 udma2 udma3 udma4 udma5 udma6
	Real max sectors: 976773168
	ATA command/feature sets:
		 security AAM HPA
	SATA command/feature sets:
		 NCQ interface_power_management SSP
--------------------------------
--------------------------------

/dev/sdb:

ATA device, with non-removable media
	Model Number:       WDC WD5000BMVV-11GNWS0                  
	Firmware Revision:  01.01A01
	Transport:          Serial, SATA 1.0a, SATA II Extensions, SATA Rev 2.5, SATA Rev 2.6
Standards:
	Supported: 8 7 6 5 
	Likely used: 8
Configuration:
	Logical		max	current
	cylinders	16383	16383
	heads		16	16
	sectors/track	63	63
	--
	CHS current addressable sectors:   16514064
	LBA    user addressable sectors:  268435455
	LBA48  user addressable sectors:  976773168
	Logical  Sector size:                   512 bytes
	Physical Sector size:                  4096 bytes
	Logical Sector-0 offset:                  0 bytes
	device size with M = 1024*1024:      476940 MBytes
	device size with M = 1000*1000:      500107 MBytes (500 GB)
	cache/buffer size  = 8192 KBytes
	Nominal Media Rotation Rate: 5400
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, with device specific minimum
	R/W multiple sector transfer: Max = 16	Current = 0
	Advanced power management level: 128
	Recommended acoustic management value: 128, current value: 254
	DMA: *mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 udma6 
	     Cycle time: min=120ns recommended=120ns
	PIO: pio0 pio1 pio2 pio3 pio4 
	     Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
	Enabled	Supported:
	   *	SMART feature set
	    	Security Mode feature set
	   *	Power Management feature set
	   *	Write cache
	   *	Look-ahead
	   *	Host Protected Area feature set
	   *	WRITE_BUFFER command
	   *	READ_BUFFER command
	   *	NOP cmd
	   *	DOWNLOAD_MICROCODE
	   *	Advanced Power Management feature set
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	64-bit World wide name
	   *	IDLE_IMMEDIATE with UNLOAD
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Host-initiated interface power management
	   *	Phy event counters
	   *	Idle-Unload when NCQ is active
	   *	NCQ priority information
	    	DMA Setup Auto-Activate optimization
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
	    	unknown 206[13] (vendor specific)
	    	unknown 206[14] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	138min for SECURITY ERASE UNIT. 138min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 50014ee6ab1da18a
	NAA		: 5
	IEEE OUI	: 0014ee
	Unique ID	: 6ab1da18a
Checksum: correct


```[/CODE]

---

### Post by WasMeHere on 2011-10-10
> **diasf said:**
> Same behaviour on another pc?
What about another drive on the same pc?
+1

Just to make sure that it is not related to the pc: You wrote about a windows box and an ubuntu box, please try if it behaves slowly also on the other pc!

---

### Post by davethewave83 on 2011-10-10
> **Olle Wiklund said:**
> +1

Just to make sure that it is not related to the pc: You wrote about a windows box and an ubuntu box, please try if it behaves slowly also on the other pc!

yeah it does, I've tried to get it working right on both the PC and my notebook, I found something interesting though. 

initial read test using hdparm at 37GB offset

hdparm -t --offset 37 /dev/sdb
/dev/sdb:
 Timing buffered disk reads (offset 37 GB):   6 MB in  4.98 seconds =   1.21 MB/

/dev/sdb:
 Timing buffered disk reads (offset 37 GB):   2 MB in  3.65 seconds = 561.03 kB/sec
----------------------------------------------


Test while performing a SMART self test in the Linux Disk Utility

/dev/sdb:
 Timing buffered disk reads (offset 37 GB):  80 MB in  3.05 seconds =  26.26 MB/sec
/dev/sdb:
 Timing buffered disk reads (offset 37 GB):  80 MB in  3.02 seconds =  26.45 MB/sec
----------------------------------------------

after smart self test finishes 
/dev/sdb:
 Timing buffered disk reads (offset 37 GB):   6 MB in  3.90 seconds =   1.54 MB/sec


so while the Disk Utility is doing the smart test, speeds are normal and once it's done, speeds drop. I've tested it via file transfer also instead of just the hdparm and file transfers go fast during the Smart self check, but once smart is finished checking or canceled speeds drop to 1.5MB/s

----------------------------------------------

I've actually been doing that a bit and it's not consistent. It's very erratic, it's as if something in the drive is switching from USB 1.1 to 2.0 or something.

---

### Post by matt_symes on 2011-10-10
Hi

You dmesg output looks like it's being installed and recognised correctly.

> yeah it does, I've tried to get it working right on both the PC and my notebook,and

> so while the Disk Utility is doing the smart test, speeds are normal and once it's done, speeds drop.That would tend to suggest it not a power supply issue from the usb power bus.

> You wrote about a windows box and an ubuntu box, That would tend to suggest it's not an OS problem.

Hmm. Not sure :(

I have a Western Digital passport 1T. I have never bothered checking the timings on it. When i get some time i will and i will post back.

Kind regards

---

### Post by davethewave83 on 2011-10-10
> **matt_symes said:**
> Hi

You dmesg output looks like it's being installed and recognised correctly.

and

That would tend to suggest it not a power supply issue from the usb power bus.

That would tend to suggest it's not an OS problem.

Hmm. Not sure :(

I have a Western Digital passport 1T. I have never bothered checking the timings on it. When i get some time i will and i will post back.

Kind regards

it's ok I'll try to get western digital to replace it once more. they seem to be resisting the idea this time. They were really nice the first time. They must think I'm toying with them :p

---

