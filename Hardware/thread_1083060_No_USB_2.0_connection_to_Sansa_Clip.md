---
title: "No USB 2.0 connection to Sansa Clip"
date: 2009-02-28
forum: Hardware
---

### Post by eckeroo on 2009-02-28
I bought a 2GB Sansa Clip to make use of the MSC USB setting for Ubuntu. My old MP3 player was a Creative Zen V that only had MTP to interface with the computer. It only worked on USB 1.1, so I bought the Sansa Clip hoping it would work on USB 2.0.

I updated the firmware to latest version V02.01.32F (using my windows laptop)

On the Sansa Clip, I set the USB setting to MSC.

Also within the Sansa Clip, I did a format.

The Sansa Clip only works on my USB 1.1 ports and fails to mount on my USB 2.0 ports.

My USB memory stick (Kingston) works on the USB2.0 ports at the USB 2.0 download rate of approx 6Mb/s. So my USB 2.0 ports do work.

The USB 2.0 ports are on a PCI expansion card: VIA USB 2.0 Host Controller with VT6202 chipset.

The lsusb output when the Sansa Clip is connected to the USB 1.1 ports:
```
Bus 005 Device 003: ID 13fe:1f00 Kingston Technology Company Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0781:7435 SanDisk Corp. 
Bus 001 Device 001: ID 0000:0000  
```

The lsusb output when the Sansa Clip is connected to the USB 2.0 ports:
```
Bus 005 Device 003: ID 13fe:1f00 Kingston Technology Company Inc. 
Bus 005 Device 002: ID 0781:7435 SanDisk Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

The Sansa Clip is being detected on lsusb. But how can I get it to mount on my USB 2.0 ports?


OS: Hardy 8.04
Processor: 1733MHz [2100] Athlon XP [palamino] processor
MB: ASUS A7M266, BIOS version [1008.02b]
Memory: 1Gb 266DDR PC2100

---

### Post by eckeroo on 2009-03-01
*bump*

---

### Post by eckeroo on 2009-03-02
*bump*

---

### Post by khelben1979 on 2009-03-02
I would like to see the output of your connected devices with this:
```
df -h
```
when the Sansa Clip is connected to the usb 2.0 port.

Using
```
mount -t vfat [path to usb memory] /mnt/
```
mounts your usb memory to the /mnt catalog.

---

### Post by eckeroo on 2009-03-03
As requested, output from: df -h 
after: mount -t vfat /dev/sdd1 /mnt/
with Sansa Clip and USB memory connected on USB 2.0 ports

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   11G  7.2G  59% /
varrun                506M  104K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   68K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   39M  467M   8% /lib/modules/2.6.24-23-generic/volatile
df: `/mnt/data': No such file or directory
gvfs-fuse-daemon       19G   11G  7.2G  59% /home/alex/.gvfs
/dev/sdd1             7.5G  129M  7.4G   2% /mnt

I originally had sdb1 mounted on /mnt/data looks like I should have unmounted that first.

---

### Post by khelben1979 on 2009-03-03
Is everything working now?

Can you access the files?

---

### Post by eckeroo on 2009-03-04
I'm afraid the sansa clip will not mount.

When I try to mount the sansa clip to a directory I created '/mnt/sansa/', this is what I get:

> sudo mount -t vfat /dev/sdd1 /mnt/sansa/
mount: special device /dev/sdd1 does not exist

This is what appears on the syslog after I connect the sansa clip:

> Mar  4 19:32:01 alex-desktop kernel: [  657.274428] sd 3:0:0:0: Device offlined - not ready after error recovery
Mar  4 19:32:01 alex-desktop kernel: [  657.274454] sd 3:0:0:0: [sdd] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK,SUGGEST_OK
Mar  4 19:32:01 alex-desktop kernel: [  657.274460] end_request: I/O error, dev sdd, sector 496
Mar  4 19:32:01 alex-desktop kernel: [  657.274468] Buffer I/O error on device sdd, logical block 62
Mar  4 19:32:01 alex-desktop kernel: [  657.274496] sd 3:0:0:0: rejecting I/O to offline device
Mar  4 19:32:01 alex-desktop kernel: [  657.274546] sd 3:0:0:0: rejecting I/O to offline device
Mar  4 19:32:01 alex-desktop kernel: [  657.274550] Buffer I/O error on device sdd, logical block 62
Mar  4 19:32:01 alex-desktop kernel: [  657.274563] sd 3:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Mar  4 19:32:01 alex-desktop kernel: [  657.274567] end_request: I/O error, dev sdd, sector 504
Mar  4 19:32:01 alex-desktop kernel: [  657.274570] Buffer I/O error on device sdd, logical block 63
Mar  4 19:32:01 alex-desktop kernel: [  657.274574] Buffer I/O error on device sdd, logical block 64
Mar  4 19:32:01 alex-desktop kernel: [  657.274577] Buffer I/O error on device sdd, logical block 65
Mar  4 19:32:01 alex-desktop NetworkManager: <debug> [1236195121.237460] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_SanDisk_Sansa_Clip_2GB_940DFB034126B6A80000000000000000_0_0').

It may be worth mentioning that a MP3 player icon for my sansa clip labelled 'USB Drive' does appear in 'Computer' on gnome.

---

### Post by eckeroo on 2009-03-13
I am now preparing a bug report for Launchpad. However, I've never done this before. So I'm not sure what information is needed.

I do not know what package the USB 2.0 connection fault is on. 

I would like as much help as possible to put together a useful bug report. 

Regards

---

### Post by khelben1979 on 2009-03-13
You can always start by [reading this document]("https://help.ubuntu.com/community/ReportingBugs") first.

---

### Post by eckeroo on 2009-03-14
The Apport application can only be used when a package crashes. This issue doesn't involve any crashes. The Sansa Clip is failing to mount on my USB 2.0 ports and I don't know what package is responsible for this. I've read some bug reports on Launchpad that refer to the package hal, but it is not obvious from the log outputs what package is causing me problems.

Before I create a new bug report on Launchpad, I really need more information. Are there more places to look for info other than the /var/log/ files?

---

### Post by eckeroo on 2010-02-07
It's almost been a year now and I've come no closer to solving this problem. The Sansa clip works fine on my netbook [eee PC 701SD, karmic koala] with Rhythmbox picking it up no problem.

I'm still using Hardy on my desktop where the problem persists. I would like to make a correction: the USB 2.0 PCI card actually has the VT6212L chip set and not the VT6202 specified in my original post.

I intend to upgrade my desktop from Hardy to Lynx when it comes out later this year. But I suspect my problem with the mounting of the Sansa Clip is due to hardware incompatibilities. My hardware again is:

OS: Hardy 8.04
Processor: 1733MHz [2100] Athlon XP [palamino] processor
MB: ASUS A7M266, BIOS version [1008.02b]
Memory: 1Gb 266DDR PC2100 
PCI USB 2.0 Card: PC Line VIA VT6212L chip set

doesn't work with:

Sansa clip 2GB (set to MSC mode and formated), firmware: V02.01.32F

My Desktop is my music bank, as it has a cd player with which to rip CDs. I have to sftp stuff from the desktop to the netbook and then over to the Sansa. I really need the Sansa to work direct with my Desktop to get that USB 2.0 download rate of 6 Mb/s.

:-({|=

---

### Post by clubsoda on 2010-02-23
I'd try one or both of the following:-
+ A Karmic live CD on your desktop machine.
+ Your VIA PCI USB card in a Windows machine.

Cheers.

---

### Post by Nordicnurse on 2010-04-15
I too have VIA PCI USB2.0 card with VT6212L chip and it's a no go.

---

### Post by eckeroo on 2010-05-02
UPDATE:

I've now upgraded to Ubuntu 10.04 (Lucid Lynx) and the problem persists.

Unfortunately the VIA VT6212L chipset is quite common for this sort of I/O card. I don't have a windows machine, but I would assume the VT6212L card works fine on windows unless someone knows otherwise.

I want to report this problem as a bug on Launchpad. But as I said before, I don't know what program to flag this bug against.

---

### Post by clubsoda on 2010-05-03
Some hardware combinations [seem to be problematic](http://www.linuxquestions.org/questions/linux-hardware-18/problem-vt6212-chipset-on-4-port-usb-pci-card-594514/). I've had trouble with a Scythe internal card reader [Alcor 058f:6362] and a particular SD memory card, where a different card or a different reader works fine but the two don't play together at all. I was geared up to file a bug but then I discovered that the combination didn't work in Windows either. I found kernel threads from 2007 where developers suggested the SD cards must be faulty, based on kernel error messages, however I believe the problem is elsewhere. At least in my case the card (and reader) are both brand new and work fine in other combinations.

I think it must be very complex to decide whether a problem is hardware or software related. On the one hand, driver developers may make assumptions which hold on the particular hardware they were using. On the other hand, manufacturers are always looking to save 20 cents by leaving out a few components...

Your Lucid kernel should be recent enough to get [Greg Kroah-Hartman](http://kerneltrap.org/mailarchive/linux-usb/2009/5/24/5796833) interested.

Cheers.

---

### Post by zob on 2010-05-10
I seem to have this problem to with my sansa clip+, ubuntu 10.04.
I had some similar problems last year with some other hardware. I fixed that by adding "acpi=off" to the bootline (either in grub at boot or in /etc/default/grub).
Since 10.04 I haven't been able to boot with acpi=off though. But I might be testing some more, now that my sansa clip+ won't mount.

Oh and by the way. Sometimes it seems to work if I boot with the hardware plugged in.
Mine is a NVIDIA nForce3 USB 2.0 controller (on the MOBO).

---

### Post by zob on 2010-05-11
Sooory.
I upgraded my firmware on the sansa clip+ not to long ago, and that must have affected some settings in the clip+ that i totally forgot about.

On the clip you must navigate to settings and set the usb-protocol to MSC. I won't work with "auto" or "MTP" on ubuntu it seems. I see you already metioned the MSC mode, but hey, recheck it maybe...

That was the reason it stopped working for me (the firmwareupgrade on the clip that changed those settings, not the upgrade to 10.04). Now it's working great for me.

---

### Post by eckeroo on 2010-05-27
*Update*

I recently purchased an external DVD reader/writer that operates over a USB 2.0 port. The device is a Samsung SE-S084.

This works well on my other computers, but I get intermissions with connection for the computer this thread is for. It may or may not mount a DVD when inserted (when it fails to mount the device automatically tries again until it does mount). Playback is brief as the connection is inevitably lost and displays this error:

"Unable to mount *title*

 DBus error
 org.gtk.Private.RemoteVolumeMonitor.Not.Found: The given
 volume was not found."

This is the first time a program has been pointed to for errors with the USB mounting. So far I have a possible incompatibility with the VIA VT6212L chipset and a definite flagging of an error with DBus. I will now place a bug report on Launchpad citing the DBus error.

---

### Post by eckeroo on 2010-05-27
There is already a bug report on Launchpad titled "DBus error
org.gtk.Private.RemoteVolumeMonitor.Not.Found: The given
volume was not found." under programs HAL, usb-creater and others. Nothing in that thread mentions MP3 players.

I did a search for VT6212L and returned no hits.

I did a general google search and found this page:

[http://www.linuxquestions.org/questions/linux-hardware-18/problem-vt6212-chipset-on-4-port-usb-pci-card-594514/](http://www.linuxquestions.org/questions/linux-hardware-18/problem-vt6212-chipset-on-4-port-usb-pci-card-594514/)

It is likely that the brand of my USB 2.0 card is incompatible rather than the chipset. I would advise against the purchasing of a PC-LINE USB 2.0 PCI card.

---

### Post by Shanghai on 2010-11-02
> **zob said:**
> Sooory.
On the clip you must navigate to settings and set the usb-protocol to MSC. I won't work with "auto" or "MTP" on ubuntu it seems. I see you already metioned the MSC mode, but hey, recheck it maybe...


That worked for me thanks a lot.

---

### Post by monkster on 2010-12-18
> **Shanghai said:**
> That worked for me thanks a lot.
With a sansa clip+ 4 gig, this worked for me, too. I was unable to access the clip with Nautilus until changing this setting on the clip. If you see this output from /var/log/kern.log:
> Device offlined - not ready after error recovery
then you need to go to Settings/System Settings/USB Mode on your clip and change the setting from "Auto Detect" to "MSC". Here is the output from kern.log right after the device scan after the setting change was made:
>  Direct-Access     SanDisk  Sansa Clip+ 4GB  v01. PQ: 0 ANSI: 0
I want to add that even before making this setting, the device appears fine in rhythmbox, a linux app I really like. But, transferring files this way on the 0.12.8 version is still too buggy and seemed to freeze the poor clip a few times during ejecting, so I gave up on that.

---

