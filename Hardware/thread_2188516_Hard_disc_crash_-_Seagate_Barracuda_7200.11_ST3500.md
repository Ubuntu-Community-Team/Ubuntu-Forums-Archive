---
title: "Hard disc crash - Seagate Barracuda 7200.11 ST3500320AS"
date: 2013-11-17
forum: Hardware
---

### Post by mkngl84 on 2013-11-17
I also posted to the Seagate forum and the details of that follows:
> I recently updated the drive to SD1A with the bootable ISO after noticing link errors and finding the update prescribed for this model on the Seagate site.
 
A few days after this, there was a period of massive disc access and the next day I noticed the entire system was in a bad state.
 
When I run the SMART monitor tool for the drive it outputs:
"
smartctl 6.2 2013-04-20 r3812 [x86_64-linux-3.11.0-13-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)
=== START OF INFORMATION SECTION ===
Vendor: /2:0:0:0
Product:
User Capacity: 600,332,565,813,390,450 bytes [600 PB]
Logical block size: 774843950 bytes
scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46
scsiModePageOffset: response length too short, resp_len=47 offset=50 bd_len=46
>> Terminate command early due to bad response to IEC mode page
A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.
"
I had connected the drive to another computer to get that SMART data because an important partition for the original computer had it's user folder stored on the failing drive.
 
The test computer automounted some of the failing drive's partitions when I plugged it in. Most if not all top directory folders seem to be there. However, not all of them that had contents show any now. Some files that are visible have zero file size.
 
I have not attempted to repair filesystems because I'm afraid that will destroy data if it is a hardware problem that is masking some of the data. Also, some partitions were seen but failed to mount. I'm praying the reading head didn't swan dive into the disc surface or bad firmware screwed with sync and positioning of disc and read head.
 
Is this something that might only be fixable, if possible say by a reflash, via the diagnostic data port of the drive?
 
Maybe a PCB swap will fix it as long as the PCB has been updated too or firmware transferred?
 
Naturally, I need the data that is/was on this drive and am not sure what to do, that is safe, in order to get this done.
 
Thanks much,
Mark

Scratch the comment about diagnostic port because there doesn't seem to be one on this model or brand.

Any ideas as to what happened to the drive and how to move forward with recovering the data that, short of filesystem checking, seems to no longer exist? The SMART errors freak me out.

Thanks!

Link to Seagate forum post: [http://forums.seagate.com/t5/Desktop-HDD-Desktop-SSHD/Semi-bricked-crashed-HD-Barracuda-7200-11-ST3500320AS/td-p/207347]("http://forums.seagate.com/t5/Desktop-HDD-Desktop-SSHD/Semi-bricked-crashed-HD-Barracuda-7200-11-ST3500320AS/td-p/207347")

---

### Post by tgalati4 on 2013-11-17
I've done PCB swaps with 50% success on older drives.  The problem is that the PCB is custom to each drive--there are digital trim settings that get lost so the new board won't read disk at all or will read it with lots of errors.

Why did you feel the need to update the firmware on the drive?  Normally this is a risky proposition, unless it fixes a critical issue and your drive would not function correctly without it.

I was not aware that Seagate made 600 petabyte drives.

Is it possible to reload the firmware with the Seagate tools?

---

### Post by mkngl84 on 2013-11-22
> Why did you feel the need to update the firmware on the drive? Normally this is a risky proposition, unless it fixes a critical issue and your drive would not function correctly without it.

Agreed. The only issue with the drive was link errors (per dmesg) where the drive would spontaneously spin down and slowly spin up again. I'ld prefer that over this.

> I was not aware that Seagate made 600 petabyte drives. Who would have known they made them and passed them off as 500GiB drives, right? :P

I just plugged the drive back in after setting mounts read-only and looked at dmesg to find this line:

> [   92.075026] sdc: detected capacity change from 500107862016 to 0

This seems familiar. As in: [http://www.msfn.org/board/topic/143880-seagate-barracuda-720011-read-me-first/]("http://www.msfn.org/board/topic/143880-seagate-barracuda-720011-read-me-first/")

> LBA0 - or drive detected by BIOS with size 0

dmesg: [http://pastebin.com/zggFwgCc]("http://pastebin.com/zggFwgCc")

Whenever I try to use seatools or the bootable firmware cd, I get an error that there are no drives connected. I've disconnected all but that drive. I also have a spare PCB that has the older firmware version. if that one could be upgraded with SD1A, could it work? How would I do so? Connect to the disc or connect on it's own?

You know that message at the end of flashing where it says in bold letters that restarting is not good enough and that the computer+drive has to be shut down after flashing? There is a possibility that that was not noticed. If that was the case, any idea what the effect actually is?

---

### Post by tgalati4 on 2013-11-22
After a firmware reflash, the power needs to be removed from the drive, so that the drive's boot microcode will reload properly and then load the new firmware.  I don't know what the effect of not following this recommendation is, except that possibly bad things can happen.  Try the reflash again, then disconnect the drive.  If seatools can't see the drive, then it is effectively bricked.

The link you posted gives a pretty clear indication that this particular drive has a tendency to brick itself.

Anytime you see "Unhandled Error Code" in dmesg effectively means you are getting gibberish from the device.

---

### Post by leeper69 on 2013-11-23
Hi mkngl84 I also had this happen to me using three seagate 500 gb drives it started with read errors on one drive so I backed up my personal data within 5 days it had spred to two drive and within 2 weeks I had three bricks.
I now just use one drive and back up with another cant afford to raid agin at this point and I am not running a server anyway, and with the bigger drive it just is not nessary. Hope this is the case with your setup mkngl84!

---

### Post by mkngl84 on 2013-11-23
>  If seatools can't see the drive, then it is effectively bricked.

After changing the ATA controller mode from AHCI to IDE, seatools can now see the drive. The drive fails both Short and Long DST. Attempting to change the drive size to native/default fails.

I tried reflashing and, while it did not come back with an error, it seemed to have no effect. I've asked Seagate if there is a way to force the microcode to update in case it hasn't already.

I wonder if the drive is/has unnecessarily added a lot of sectors to the grown list/g-list of bad sectors. Is there any way to reset that? Better yet, (and probably actually safe) test each original sector listed in the g-list and if it isn't actually bad, remove it from the list.

This was an overnight failure so no chance for backups except BEFORE flashing.

Some kind of laboratory fix *might* be the only way.

> Hi mkngl84 I also had this happen to me using three seagate 500 gb drives it started with read errors on one drive so I backed up my personal data within 5 days it had spred to two drive and within 2 weeks I had three bricks.
I now just use one drive and back up with another cant afford to raid agin at this point and I am not running a server anyway, and with the bigger drive it just is not nessary. Hope this is the case with your setup mkngl84!

Hehe. Thanks, but no. At least the root file-system was on a different drive (SSD). Also, other data was on a separate drive. So, if the data can not be recovered, it isn't a total loss.

---

### Post by tgalati4 on 2013-11-23
The fact that the ATA controller is not working possibly means that the firmware loaded OK, but the controller's circuitry is bad.  I don't know of any tool to reset the bad sector list.  It's possible that a capacitor went bad or a chip delaminated and the drive did its best to keep going until it ran out of bad sector space.  It might be possible to do a board swap to read the data.

---

