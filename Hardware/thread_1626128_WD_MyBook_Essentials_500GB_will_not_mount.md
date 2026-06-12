---
title: "WD MyBook Essentials 500GB will not mount"
date: 2010-11-19
forum: Hardware
---

### Post by Geobot on 2010-11-19
Just bought a WD MyPassport(sorry, the title is wrong) Ess 500GB external drive. These are problems I had straight out of the box. This is the second one I've bought, and the other didn't have any problems.

I plugged it into my desktop( 10.04 ), and it didn't seem to be recognized, no mount, etc. Tried playing with the cables, no go. The light on the drive comes on, does its blinking thing for a few seconds, then goes steady like normal.

Plugged it into my netbook( 10.08 ), same deal. 

Grabbed a dmesg from my desktop:
```

[ 1285.060032] usb 1-6: new high speed USB device using ehci_hcd and address 10
[ 1285.212176] usb 1-6: configuration #1 chosen from 1 choice
[ 1285.213020] scsi12 : SCSI emulation for USB Mass Storage devices
[ 1285.213208] usb-storage: device found at 10
[ 1285.213214] usb-storage: waiting for device to settle before scanning
[ 1290.350238] sd 12:0:0:0: [sdb] Sense Key : Data Protect [current] 
[ 1290.350245] sd 12:0:0:0: [sdb] Add. Sense: Logical unit access not authorized
[ 1290.350254] sd 12:0:0:0: [sdb] CDB: Read(10): 28 00 ff eb 0f f8 00 00 01 00
[ 1290.350268] end_request: I/O error, dev sdb, sector 4293595128
[ 1290.353233] sd 12:0:0:0: [sdb] Unhandled sense code
[ 1290.353238] sd 12:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE

```

The last 6 lines(time 1290) repeat about 40 times over the course of 3 seconds, this is just the first block. The others have different numbers for the CDB:Read(10) and the sector, but other than that are identical.

After reading around, I assumed that the problem was due to WD's encryption software built-in to the drive. One solution I found was to access it in Windows and turn off the encryption, format, etc.

The problem there is that when I boot my desktop into XP, it doesn't work there either. It just says "A problem was encountered during hardware install. Your device may not work properly." Thanks for the massive amounts of helpful info, MS...

It doesn't show up in gparted, I can't find it... anywhere.

Like I said, I've bought one of these drives before with no problems. The only difference I can think of is that it got plugged into a Win7 PC before anything else and formatted straight away. I don't have easy access to any Windows PC besides my XP, and it doesn't seem to want to work right with that.

Anything I'm missing? Suggestions?

---

### Post by endotherm on 2010-11-19
does it show up to fdisk?
```
sudo fdisk -l
```I agree with your analysis of the log info, it does look like a cypher problem. 
so the encryption is a hardware thing then, if you have to disable it, right? how do you go about disabling it in windows? may provide a useful hint. 

it makes sense that the drive would prevent format/partitioning without the passkey. after all, protecting data destruction is as important as protecting it from exposure. 

it is likely that your drive requires vista or higher, as they have some more advanced crypto features, and better usb support. there may be an xp driver (check with WD.com). there may also be firmware upgrades available that address autoconf bugs.

---

### Post by Geobot on 2010-11-19
No, it doesn't show up with fdisk at all either.

As for the encryption, I'm not 100% on this, but from what I gathered, it is software implemented. I read that there is a separate small partition by default on the drive that handles this. However, it isn't supposed to come out of the box encrypted anyway, because there's no 'default' passkey or anything along those lines. It shouldn't be encrypted at all until I do it myself.

I thought about the Vista req, but the box it came in is clearly labeled with "XP, Vista, 7", and the quick install instructions for XP are basically "plug it in and hit ok".

I'm thinking about taking it back since I still have the receipt, but I'm not sure that's going to help anything.

---

### Post by endotherm on 2010-11-19
this thread may help you get it going in XP, at least enough to format it.
[http://en.kioskea.net/forum/affich-86235-help-my-western-digital-is-not-recognized](http://en.kioskea.net/forum/affich-86235-help-my-western-digital-is-not-recognized)

---

### Post by endotherm on 2010-11-19
this may be the answer you seek:
[http://support.microsoft.com/kb/925196/en-us](http://support.microsoft.com/kb/925196/en-us)

---

### Post by Geobot on 2010-11-20
Well, the steps in the article did -something-, but still no fix. Since I hadn't used WinXP in quite a while, I had to install SP3 to use their FixIt program, which required Windows Installer 3.1, etc.. 

After doing all of that, it -did- install my drive in XP... kinda. It shows as installed and working properly in Device Manager, but is not mounted. It doesn't show up in the Disk Management window either, is not assigned a drive letter, and does not appear in My Computer.

So I tried running the firmware updates from WD, and it updated the drivers in Device Manager, but still no fix. 

I even tried changing USB cables, since a few people said that worked for them.

So, now in XP it's recognized as "working properly", but it doesn't. In Ubuntu it still just doesn't show up anywhere.

I'm tempted to just set it on fire.

---

### Post by Geobot on 2010-11-22
Update:

So I exchanged it at the store, and the new one works perfectly. Just for future searchers that may have this problem...

---

### Post by typhoon_tip on 2010-11-22
> **Geobot said:**
> Update:

So I exchanged it at the store, and the new one works perfectly. Just for future searchers that may have this problem...

Ahahaha thanks for the update. It seemed strange as a problem to me as well. Usually when a disk doesn't get recognized like that, it's most probably a bad one. At least for me, according to my experience, that is almost solely cable or disk trouble.

---

### Post by wet-willy on 2010-11-22
As of late I've been hittin' the keys a little hard, running a variety of operating systems. Strange things happen lately while booting between systems when a USB drive is left plugged in/powered on. My live Maverick key has two partitions, one NTFS, the other FAT where the CD and persistence are. Often I find I can't boot it, (no operating system found), thankfully I have bootitng as a boot manager and just go into maintenance and always find the FAT partition's active bit is removed and needs to be reactivated. 
 
I had similar issues as yourself with my 500GB Seagate tethered with USB2 drive mate to the box. It sometimes appears to go south, just like your experience, the drive is somewhat there but not accessible. Through my boot manager I find it sees the two existing partitions, but when looking at the MBR, it's empty, strange indeed. So, I hit the button to write a standard MBR to which the existing partition structure is written to it and reboot into an OS and all is good. 
 
So..... 
I guess my point is, if someone else runs into a similar situation, run testdisk or bootitng on the drive, it might just be a corrupt MBR. Or Debian Squeeze de-activating partitions marked active that didn't boot (that's the OS that put's a sad face on me when showing off my live Ubuntu that don't boot anymore, (Debian vs. Debian :)), Come to think of it, when I let Squeeze see a partition with a mirror image of itself, it goes coo-coo and neither partition will boot after).

---

