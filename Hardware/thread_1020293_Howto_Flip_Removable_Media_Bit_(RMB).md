---
title: "Howto Flip Removable Media Bit (RMB)"
date: 2008-12-24
forum: Hardware
---

### Post by Youresorock on 2008-12-24
I bought a 16GB PNY SD card to use on my Dell mini.  It works fine in Ubuntu (naturally) but I want to switch the Removable Media Bit (RMB) so that windows will see it as a fixed disk.  This allows multiple partitions to be visible and configurable in Windows.

I have googled extensively, and found only the Lexar Bootit utility (didn't see my SD card).  Surely there has to be a way to do this in linux.  Perhaps even just dd'ing /dev/zero to the whole drive?  

The RMB is apparently the 7th bit of the first byte on a disk.  It needs to be 0 for a fixed disk.

---

### Post by 2hot6ft2 on 2008-12-24
You know 20 years ago I think I could have pulled that off in DOS with a good hex editor but not anymore. I would like to know if you find a way.

---

### Post by cong06 on 2010-03-10
No one?

---

### Post by Peter Peterssonn on 2010-06-05
Hello..
I know how to do that **and** the cause of the problem ..
On all windoze-OS a disk that has the RMB set to "1"(actually it seems like m$ and the chip-mfg's don't always agree on this  !)
will be identified as a "removable disk" and windoze does not allow multi-partitioning of "removable disks" 
or accessing more than **the first partition** by design . 

Linux doesn't care about this, neither does your BIOS . 
It's probably designed that way because windows previously didn't create properly aligned partitions 
and this has a noticeable negative performance-influence on all flash-based media .. 
Besides, on flash-media partitions don't "exist" in the same physical manner as they do on a "normal" HDD,
the data is all over the place, being moved around by wear-levelling and all the other neat tricks controllers have up their sleeve
to allow the use of inferior MLC -flash . Some of these controllers are Multi-lun capable btw.. That's even better  !!
You could have up to 8 primary partitions on one of those .
Anyway, it's done "in hardware", this isn't correct :
> The RMB is apparently the 7th bit of the first byte on a disk. The RMB does not reside on the disk, it's coded in to the controller . 
> The removable media device setting is a flag contained within the SCSI  Inquiry Data response to the SCSI Inquiry command. 
Bit 7 of byte 1  (indexed from 0) is the Removable Media Bit (RMB).
A RMB set to zero  indicates that the device is not a removable media device. 
 A RMB of one  indicates that the device is a removable media device.
 Drivers obtain  this information by using the **StorageDeviceProperty** request.
[http://www.microsoft.com/whdc/archive/usbfaq.mspx](http://www.microsoft.com/whdc/archive/usbfaq.mspx)
Some cards (and/or readers) can present the media as a "Fixed" disk to windows,
allowing multiple,usable partitions, but usually it's hard finding the software that allows
"flipping the removable media-bit" .
 It is worth going through the trouble of finding the tools for doing this in hardware, 
if possible, because it will work on all windows-machines .
The HID/PID of your controller may lead to something useful on google :)

In case the specific card/controller you use can not be "flipped" in hardware
there are also a couple software-solutions, 
the **"Hitachi Microdrive Filterdriver"**
[FONT=Arial, Helvetica, sans-serif][SIZE=2]**or "dummydisk.sys**[/SIZE][/FONT]" [http://www.codeproject.com/KB/system](http://www.codeproject.com/KB/system)
/soviet_direct_hooking.aspx
Your device(s) will need to be configured to use the Hitachi-driver whereas [FONT=Arial, Helvetica, sans-serif][SIZE=2]**"dummydisk.sys**[/SIZE][/FONT]" makes **all** "removable disks" "fixed" ..
There's a very good guide on how to configure the Hitachi-driver available here :
[http://chdk.setepontos.com/index.php?topic=2332.0](http://chdk.setepontos.com/index.php?topic=2332.0)

Obviously, this will only work on boxes that have either driver installed and
admin-rights are required to install ..

Hope that helps you out ..

---

### Post by pygo on 2011-07-18
Incredibly sorry to dig up an old post, but I've seen some questions on how to do this in linux out on the interweb.
I think that simply using DD will produce the desired results. A bit of a hammer approach, but can be narrowed down. You don't need to wipe the whole disk, just the first byte.
[INDENT]dd if=/dev/zero of=/dev/sdx bs=1 count=1
[/INDENT]That should do it. I had a big fat32 partition on mine when I did it and I don't appear to have suffered any data loss.

Again, sorry for digging around in a graveyard.

---

### Post by The_Highwayman on 2011-07-25
Yours is an Excellent thread. Most other web articles cite WINDOWS OS tools (1) BootIt - Lexar USB Flip the Removable Media Bit Tool from "http://search.4shared.com/q/1/BootIt" and (2) HP USB Disk Storage Format Tool from "http://www.pscience5.net/downloads/CFP/SP27213.exe". Neither tools changed the Windows OS Recognised Removable status in my USB Pen sticks.

This article seems to be more universal, even if Bit 7 RMB only refers to some USB pen sticks / Flash Drives without Controller supplied RMB.

It seems to me if one can distinguish the two implementations, one can see if the Linux / cygwin (Unix OS) dd method will work.

Does anyone know how to distinguish pen drives with CONTROLLER emulated RMB from Implementations with explicit Bit 7, Byte 1 ?

---

### Post by The_Highwayman on 2011-07-25
It occurs to me if one completely obliterated the Media Byte 1 with all zeroes using dd, could one lose access to the entire drive ? 
   
  Could some Host OS fail to distinguish the now ‘all zero’ USB Stick media byte from say a USB mounted Floppy disk ? 
   
  Perhaps some caution is required here. Fortunately, the dd command had no effect on my USB pen Sticks regarding use and Removable Status.

---

### Post by 14218f4114b1fd99 on 2012-01-08
> **2hot6ft2 said:**
> You know 20 years ago I think I could have pulled that off in DOS with a good hex editor but not anymore. I would like to know if you find a way.

I got myself a good Hex Disk Editor ([HxD]("http://mh-nexus.de/en/hxd/"))
How could I flip it (cannot work out how to find bit 1 of byte 7)

(I am new to Hex Editing)

Thanks.

---

### Post by coffeecat on 2012-01-08
Old thread. Closed.

@saleemrashid1, the software you link to runs only in Windows. This is an Ubuntu forum. If you need help running a Linux hex editor please start a fresh thread.

---

