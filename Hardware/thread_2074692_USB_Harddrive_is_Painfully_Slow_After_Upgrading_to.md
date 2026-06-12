---
title: "USB Harddrive is Painfully Slow After Upgrading to 12.10"
date: 2012-10-22
forum: Hardware
---

### Post by DBQ on 2012-10-22
Hi Everybody.

I have recently upgraded to Ubuntu 12.10.

Now my USB hard drive is so slow it is unbelievable. The copy speed now is 470 kB per second. The drive is connected to the USB 2.0 HUB
which is attached to a USB 3.0 port on my laptop.

This was not a problem with 12.04. Any ideas?

---

### Post by DBQ on 2012-10-22
I tried this with another USB hard drive and the same problem happens.

This even happens when I connect it directly to the laptop's USB.

Is anybody else having this problem?  Any ideas?

---

### Post by DBQ on 2012-10-26
Bump...am I really the only one affected by this?

---

### Post by DBQ on 2012-10-27
bump...

I tried booting from the Ubuntu 12.10 live CD. I tried copying files and the write speed is what is expected.

So why is this happening in my non-liveCD Ubuntu.

Please help.

---

### Post by emmdarakis on 2012-11-12
I have the same problem after upgrading to 12.10 from 12.04.

Benchmark from the disks' utilities reports acceptable read/write speeds (around 30MB/s) for my USB external disk, but when I access real files, the speed falls below 1MB/s (around 600-700kB/s in my case). 

For example it takes several seconds to open or copy a simple 2-3MB jpg image file. 

In Windows and with ubuntu 12.04 the speed is ok (~30MB/s).

Anything we could try??

Thanks

---

### Post by DBQ on 2012-11-12
It seems to be related to the kernel version used by 12.10

Booting with earlier kernel does not have this problem.  BTW, I was wrong; the speed is still slow when booting with lived cd.

Moreover this problem occurs only for writing NTFS USB drives. 

Please help us somebody!

Since I copy many VMs to from USB drives, for me this is a huge show stopper esp. Considering the fact that my drive is USB 3.0 complient and the laptop has USB 3.0 port.

---

### Post by varunendra on 2012-11-13
DBQ, emmdarakis,
Please make sure 'dkms' and 'linux-headers' are installed -
```
sudo apt-get install --reinstall dkms linux-headers-generic
```
Then do -
```
sudo apt-get update
sudo apt-get dist-upgrade
```

And see if that makes any difference.

As for now, please post output of -
```
lspci -k | grep -iA2 usb
```
to let us see the current driver in use for your usb buses.

---

### Post by DBQ on 2012-11-13
Thanks for the response. Here is my output

```

00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
	Subsystem: Lenovo Device 21cf
	Kernel driver in use: ehci_hcd
--
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
	Subsystem: Lenovo Device 21cf
	Kernel driver in use: ehci_hcd
--
0e:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
	Subsystem: Lenovo Device 21cf
	Kernel driver in use: xhci_hcd

```

---

### Post by varunendra on 2012-11-13
Well that is as it should be.

Please try the rest of what I suggested and post back if there is any improvement.

---

### Post by DBQ on 2012-11-13
I tried it, but not luck :(

---

### Post by emmdarakis on 2012-11-13
Same here

---

### Post by varunendra on 2012-11-13
Ok, that was a guessed shortcut which didn't work. We need to dig deeper. Please post the following outputs after the drive is connected and detected -
```
dmesg | tail
usb-devices
dpkg --get-selections ntfs*
```
In usb-devices output, we are only interested in the block pertaining to the drive. So you may strip-off the rest of the output.

Plus the Brand, model, type (portable 2.5" or 3.5") and capacity of the drive(s).

I'm assuming it is only happening with **ntfs** partitions on **usb drives**, as DBQ remarked. Do you have an ntfs partition on the local drive? How's the performance there. We want to make sure if the problem is device (or device-type) specific or filesystem (ntfs) specific.

---

### Post by emmdarakis on 2012-11-14
Thanks for the interest:

$dmesg | tail
[ 4207.162257] sd 6:0:0:0: [sdc] Write Protect is off
[ 4207.162271] sd 6:0:0:0: [sdc] Mode Sense: 2f 08 00 00
[ 4207.163309] sd 6:0:0:0: [sdc] No Caching mode page present
[ 4207.163322] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 4207.168157] sd 6:0:0:0: [sdc] No Caching mode page present
[ 4207.168171] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 4207.188109]  sdc: sdc1
[ 4207.191813] sd 6:0:0:0: [sdc] No Caching mode page present
[ 4207.191827] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[ 4207.191839] sd 6:0:0:0: [sdc] Attached SCSI disk

$ usb-devices
T:  Bus=02 Lev=01 Prnt=01 Port=03 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bc2 ProdID=3300 Rev=01.30
S:  Manufacturer=Seagate 
S:  Product=Desktop         
S:  SerialNumber=2GHJX3R1    
C:  #Ifs= 1 Cfg#= 1 Atr=c0 MxPwr=2mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

$ dpkg --get-selections ntfs*
ntfs-3g						install

You are right that it happens only with external, usb, NTFS disks. Internal NTFS partitions (one parition on an SSD drive and one on ordinary diskdrive in my case) work fine. 

In my case the external problematic disk is: Seagate, 1TB, 3.5", Barracuda series, 7200rpm, sata sitting on its original "1T Seagate Desktop" case.

BUT, I just tried another external disk (Fujitsu, 120GB, 2.5", 5400rpm, sata, NTFS) sitting on a different usb/sata adaptor and it works fine.

Unfortunately I can't swap disks/adaptors because the 3.5" needs extra power that the other adaptor doesn't have. I'll try to think of something else.

I hope these help.

Thanks a lot

---

### Post by varunendra on 2012-11-14
emmdarakis,

With my very limited knowledge, everything I can understand in those outputs seems normal. I have a couple of portable 2.5" usb HDDs (a seagate and a Silicon Power) lying around with both ext4 and ntfs partitions. I can read/write to and from them normally. However, I'm on 12.04, haven't tested 12.10 yet. I'll need some time to experiment with them to see what other parameters can be queried. Unfortunately, right now I'm a bit stuck in some other tasks, so can't say when I'll get enough time for that.

Meanwhile, just for a test, can you create a small fat32 partition on the same drive and see if the speed problem is same there ? Also, make sure the drive is properly 'defragmented' on a windows system. To be extra sure about disk's own health, you may also run chkdisk on it, then 'safely remove' it from the windows system.

It'll also be interesting to see what DBQ has to tell us, apart from those outputs.

One thing I'm curious about is - after (re)installing dkms and linux-headers, did the OS actually download any updates ? If not, you should keep trying until new updates arrive. Also make sure that all the four common repositories (main, universe, multiverse, restricted) are enabled in **Software Center > Software sources** before attempting a manual check for updates.

---

### Post by emmdarakis on 2012-11-14
I did try a fat32 partition on the disk and it works fine.

I'm pretty sure drive's health is ok, I'll chkdsk/defrag it later just to make sure.

Also when I reinstalled dkms and the linux headers, fresh copies were actually 
downloaded from the repos for the installation. 

For me it's nothing urgent - just annoying - I use the drive mostly for backup. I just wanted to make sure I am not doing something wrong.

Thanks anyway...

---

### Post by rickcorp on 2012-11-20
I am having the same performance issue, on 12.04 performance was fine, however since upgrade to 12.10 performance is less than fine.

---

### Post by varunendra on 2012-11-20
> **emmdarakis said:**
> Also when I reinstalled dkms and the linux headers, fresh copies were actually downloaded from the repos for the installation.Sorry, I totally forgot this thread, thanks to *rickcorp* for bumping it.
Actually I was interested in whether the updates downloaded and installed any 'additional' packages - besides the headers and dkms.

I just did some tests on my 2.5" seagate 320GB drive on ntfs parition, and the speed is as fast as can be expected on a USB2 port. However, I'm using 12.04, so it's no real comparison.

For now (based on your output of dpkg --get-selections ntfs*), you may try installing '*ntfsprogs*' package. It is nothing but just a transitional package which eventually installs the* ntfs-3g* package which you already have. Still I am suggesting it in hope that maybe it could install a newer, more suitable version of ntfs-3g -
```
sudo apt-get install ntfsprogs
```If that doesn't help, please post the output of -
```
sudo hdparm -I /dev/sdb
```assuming that your external problematic drive is sdb. If it is not, change sbd with relevant one. *(please note that it is capital 'i' in 'hdparm [COLOR=DarkRed]**-I**[/COLOR])*

Post the same output from your Fujitsu drive also which is working fine. I'm not an expert on this, so am just hoping to get clues in the output.

Also, although may not be related, have you tried using a shorter USB cable for the seagate drive? Because the ones I have seen for 3.5" drives are 1.5m long, and thus may suffer signal or voltage-drop problems, especially if they are weak from the beginning!

**[PS:** Please do **sudo apt-get update** and **sudo apt-get dist-upgrade** once more after installing ntfsprogs.]


***@rickcorp,***
If there is even a minor difference in your case, it would be difficult and very confusing to troubleshoot three problems together in one thread.
So I would suggest to post your own thread regarding the problem, then post a link to it here.

---

### Post by emmdarakis on 2012-11-21
I did install ntfsprogs, and updated with no difference. 

For the problematic (Seagate) drive:

```

sudo hdparm -I /dev/sdc

/dev/sdc:

ATA device, with non-removable media
	Model Number:       ST31000528AS                            
	Serial Number:      5VP172JT
	Firmware Revision:  CC36    
	Transport:          Serial
Standards:
	Used: unknown (minor revision code 0x0029) 
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
	LBA48  user addressable sectors: 1953523055
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:      953868 MBytes
	device size with M = 1000*1000:     1000203 MBytes (1000 GB)
	cache/buffer size  = unknown
	Nominal Media Rotation Rate: 7200
Capabilities:
	LBA, IORDY(can be disabled)
	Queue depth: 32
	Standby timer values: spec'd by Standard, no device specific minimum
	R/W multiple sector transfer: Max = 16	Current = ?
	Recommended acoustic management value: 254, current value: 0
	DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
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
	   *	DOWNLOAD_MICROCODE
	    	Power-Up In Standby feature set
	    	SET_FEATURES required to spinup after power up
	    	SET_MAX security extension
	   *	Automatic Acoustic Management feature set
	   *	48-bit Address feature set
	   *	Device Configuration Overlay feature set
	   *	Mandatory FLUSH_CACHE
	   *	FLUSH_CACHE_EXT
	   *	SMART error logging
	   *	SMART self-test
	   *	General Purpose Logging feature set
	   *	WRITE_{DMA|MULTIPLE}_FUA_EXT
	   *	64-bit World wide name
	    	Write-Read-Verify feature set
	   *	WRITE_UNCORRECTABLE_EXT command
	   *	{READ,WRITE}_DMA_EXT_GPL commands
	   *	Segmented DOWNLOAD_MICROCODE
	   *	Gen1 signaling speed (1.5Gb/s)
	   *	Gen2 signaling speed (3.0Gb/s)
	   *	Native Command Queueing (NCQ)
	   *	Phy event counters
	    	Device-initiated interface power management
	   *	Software settings preservation
	   *	SMART Command Transport (SCT) feature set
	   *	SCT Long Sector Access (AC1)
	   *	SCT LBA Segment Access (AC2)
	   *	SCT Error Recovery Control (AC3)
	   *	SCT Features Control (AC4)
	   *	SCT Data Tables (AC5)
	    	unknown 206[12] (vendor specific)
Security: 
	Master password revision code = 65534
		supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
	162min for SECURITY ERASE UNIT. 162min for ENHANCED SECURITY ERASE UNIT.
Logical Unit WWN Device Identifier: 5000c500184e376e
	NAA		: 5
	IEEE OUI	: 000c50
	Unique ID	: 0184e376e
Checksum: correct

```


For the non-problematic (Fujitsu) drive:
```

sudo hdparm -I /dev/sdd

/dev/sdd:

ATA device, with non-removable media
	Model Number:       &#65533;&#65533;&#65533;&#65533;&#65533;\$_yJ&#65533;S&#65533;C&#65533;&#65533;YA<-8&#65533;g!hc&#65533;puwI&#65533;%;cy&&#65533;
	Serial Number:      &#65533;&#65533;&#65533;&#1034;&#65533;&#65533;&#65533;{&#65533;]v&#65533;R&#65533;&#65533;
	Firmware Revision:  p&#65533;&#65533;&#65533;&#65533;8
	Media Serial Num:   v{&#65533;&#65533;&#65533;<|&#65533;O&#65533;h&{&#797;&#65533;&#65533;X&#65533;CQ&#65533;&#1336;&#65533;bW}b/&#65533;&#65533;(&#65533;(&#65533;
	Media Manufacturer: '	&#65533;&#65533;%&#65533;&#65533;X&#65533;	47>&#65533;mO	4&#65533;
	Transport:          Parallel; Revision: 0xa3db
Standards:
	Used: unknown (minor revision code 0xa473) 
	Supported: 14 13 12 9 7 6 5 
	Likely used: 14
Configuration:
	Logical		max	current
	cylinders	0	46028
	heads		0	47998
	sectors/track	510	62714
	--
	CHS current addressable sectors: 2605688847
	Logical/Physical Sector size:           512 bytes
	device size with M = 1024*1024:     1272309 MBytes
	device size with M = 1000*1000:     1334112 MBytes (1334 GB)
	cache/buffer size  = unknown
	Nominal Media Rotation Rate: 32767
Capabilities:
	IORDY(cannot be disabled)
	Standby timer values: spec'd by Vendor
	R/W multiple sector transfer: Max = 8	Current = 121
	Recommended acoustic management value: 186, current value: 30
	DMA: not supported
	PIO: unknown
	   *	reserved 69[0]
	   *	reserved 69[3]
	   *	reserved 69[6]
	   *	reserved 69[7]
	   *	DOWNLOAD MICROCODE DMA command
	   *	READ BUFFER DMA command
	   *	DEVICE CONFIGURATION SET/IDENTIFY DMA commands
	   *	Data Set Management TRIM supported (limit 38532 blocks)
Security: 
	Master password revision code = 14184
	not	supported
	not	enabled
	not	locked
	not	frozen
	not	expired: security count
		supported: enhanced erase
Integrity word not set (found 0x3592, expected 0xaba5)

```


As you can see, the characters in the "ATA device" section for the Fujitsu drive are not readable...

---

### Post by varunendra on 2012-11-21
Were these drives connected to USB3 port? Because I just retried mine with both USB2 and USB3 ports, and it gave me full and stable results only on USB2 port (drive itself being USB2 compliant).
When connected to USB3 port, it would give me different results each time I re-entered the command. Including non-readable characters sometimes, similar to your last output with fujitsu drive.

This makes me more suspicious -
> **emmdarakis said:**
> ..
..
    cache/buffer size  = [COLOR=Red]**unknown**[/COLOR]
..
..
    R/W multiple sector transfer: Max = 16    **Current = [COLOR=Red]?[/COLOR]**
   
The seagate one's output is more like mine when connected to USB2 port, but I get both buffer/cache size and current speed for R/W multi-sector transfer in that mode.

So if it wasn't already, please re-post each output while the drives are connected to USB2 port(s).

It could have helped if DBQ had posted the same results from his drive(s). Because if it is happening with only "**Ubuntu 12.10 + Seagate + ntfs**" combination and every-time everywhere, then it may indeed be a bug with 12.10 which you should report at launchpad.


**PS :**
Please make it a habit to always wrap output codes in **'Code'** tags generated by clicking on **#** at the top of the edit box in which you create new posts, then copy-paste the output text in-between the generated tag pair.
Please also edit your above post to wrap it now. You can do so by just highlighting the output part using mouse cursor, then clicking on **#** (in advance edit mode), or simply type [noparse]```
 at the beginning and 
```[/noparse]at the end of the output part.

It preserves the output formatting and puts the code in a nice box, thereby making your post neat, compact and more readable :)

---

### Post by emmdarakis on 2012-11-21
I only have access to USB 2.0 ports, so whatever I have been posting here is applicable for usb 2.0 ports only!

**PS:** 
Thanks for the instructions on Code. I could tell that the output of the command would look ugly as normal text, but I didn't know how to do it correctly. Honestly, I was planing to ask you how to do it in my last post but I forgot! Thanks anyway...

---

### Post by varunendra on 2012-11-21
> **emmdarakis said:**
> Honestly, I was planing to ask you how to do it in my last post
Nice to know you were interested, because that's the key to learning all the stuff we keep dealing with here :)

One last question before I leave for a long (maybe a few hours, maybe a day) break, what architecture of 12.10 are you using? 32bit or 64bit ?

I've just finished downloading 32bit iso, so may try it on a USB or in a VM. But if you have 64bit, I'm afraid it's going to take me about a couple of weeks to download it @ my crawling GSM connection speed !! :P

Better post the outputs of -
```
uname -a
lsb_release -d
```

---

### Post by emmdarakis on 2012-11-21
I'm using 64bits but I don't know which architecture DBQ is using.

```

$ uname -a
Linux laptop 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:26:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```

$ lsb_release -d
Description:	Ubuntu 12.10

```

---

### Post by XeHK on 2012-11-29
Try to install usb-modeswitch from synaptic if its not installed.

---

### Post by DBQ on 2012-12-22
usb mode switch is already installed. I am still having the same problem.

Outputs:

Linux ThinkPad-W520 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:49:53 UTC 2012 i686 i686 i686 GNU/Linux


LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch:cxx-3.0-ia32:cxx-3.0-noarch:cxx-3.1-ia32:cxx-3.1-noarch:cxx-3.2-ia32:cxx-3.2-noarch:cxx-4.0-ia32:cxx-4.0-noarch:desktop-3.1-ia32:desktop-3.1-noarch:desktop-3.2-ia32:desktop-3.2-noarch:desktop-4.0-ia32:desktop-4.0-noarch:graphics-2.0-ia32:graphics-2.0-noarch:graphics-3.0-ia32:graphics-3.0-noarch:graphics-3.1-ia32:graphics-3.1-noarch:graphics-3.2-ia32:graphics-3.2-noarch:graphics-4.0-ia32:graphics-4.0-noarch:printing-3.2-ia32:printing-3.2-noarch:printing-4.0-ia32:printing-4.0-noarch:qt4-3.1-ia32:qt4-3.1-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

---

### Post by sudodus on 2012-12-22
Try to monitor the read/write activity with
```
sudo iotop -o
```
It's in the repos, simple to install.

And, could your problem be related to that of this link?
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2097241[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2097241")

---

### Post by DBQ on 2012-12-23
iotop shows transfer speeds similar to speeds reported by nautilus. 

Any other ideas? It definitely looks like a kernel/NTFS driver -related issue.  It worked like a charm till Ubuntu 12.04.

I wonder if anybody else was ever able to resolve this.

Because of this issue, I had to resort to using Fedora many times.  I cannot simply format the drive into ext<X> (as such systems give the correct speed) because I need NTFS in order to share my data with other machines.

---

### Post by sudodus on 2012-12-24
I think that 12.10 is not mature yet, and that it is a bug. I will continue with 12.04 (which is also an LTS release). If there are features in 12.10, that you need, I suggest that you use some other file system for your USB harddrive, for example ext2, ext3 or ext4.

These file systems can be mounted by Windows, if you install a driver program. See this link

[[COLOR="Red"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

---

### Post by DBQ on 2012-12-24
This is not an option.

I wonder if there some mounting parameters that could be the cause.

This issue seems to be gaining a wider notoriety, although no real solutions have surfaced.

---

### Post by sudodus on 2012-12-26
> **DBQ said:**
> This is not an option.

Is it an option to go back to 12.04?
> 
I wonder if there some mounting parameters that could be the cause.

I don't know, but I think it is a bug, not bad parameters or lack of parameters, since it used to work.
> 
This issue seems to be gaining a wider notoriety, although no real solutions have surfaced.
Yes, and there will be a bug fix, but we don't know when.

---

### Post by DBQ on 2013-01-27
It's been a while. There have been many kernel upgrades released.

However, the problem persists.

---

### Post by sudodus on 2013-01-28
> **DBQ said:**
> It's been a while. There have been many kernel upgrades released.

However, the problem persists.
Try (booted from a CD or USB drive) with 12.04 LTS and check if the USB drive is faster (as fast as it should be).

And if it is faster, consider [re]installing 12.04.

---

### Post by DBQ on 2013-05-12
Well Ubuntu 13.04 is out. 
I burned it to DVD, booted from it, and tried transferring files to that same USB drive.

The problem is still there. Perhaps it's time to consider changing my distro...

---

### Post by sudodus on 2013-05-12
Unless you need some new features in 12.10 and 13.04, try (booted from a CD or USB drive) with 12.04 LTS and check if the USB drive is faster (as fast as it should be).

- And if it is faster, consider [re]installing Ubuntu 12.04, which will live until April 2017.

Otherwise, is it really faster in another OS?

- You mentioned Fedora before. If it cooperates better with your drive and NTFS file system, fine! It's linux too :-)

- But there might also be something wrong with the drive (for example the firmware or electronics).

---

### Post by slumbergod on 2013-05-23
The problem of USB file transfer speeds has been an issue since I started using Ubuntu several years ago. The problem seems to be in the kernel and can be present in one release, absent in the next, then back again. It is frustrating because when one thing works something else gets broken. I gave up on the kernels that ship with 13.04 because I was having problems with my sound and my webcam. Going to a newer kernel fixed both of these issues for me.

I am certainly not an expert but I suggest you try a different kernel. There are two you can try.

[http://blog-darryldias.rhcloud.com/category/ubuntu-2/](http://blog-darryldias.rhcloud.com/category/ubuntu-2/)

or the pf variant:
[http://repos.natalenko.name/ubuntu/pf/](http://repos.natalenko.name/ubuntu/pf/)

I am finding my system is working much better using the pf kernel though file transfer speeds with the 9.3 are slow so I have gone back to the 9.2 release. Make sure you get the 64bit version if your system uses that. Grab the headers too.  

You can install grub-customizer to change the boot order safely.

---

