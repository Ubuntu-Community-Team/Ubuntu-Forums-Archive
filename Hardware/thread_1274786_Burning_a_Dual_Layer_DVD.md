---
title: "Burning a Dual Layer DVD"
date: 2009-09-24
forum: Hardware
---

### Post by gali98 on 2009-09-24
I have been trying to burn a dual layer dvd for the past several hours with no success. I have scoured the web in hope of finding something, but nothing has gotten me anywhere.
In my research, I have discovered the two major underlying mechanisms for burning dvds (and cds.) The First is growisofs (k3b, brasero, etc...) and the other is wodim (what cdrecord and dvdrecord are...)
Both are giving me errors:
Wodim
```
kory@kory:~/Desktop$ wodim dev=/dev/sr0 ./creaturefactory.ISO 
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'Slimtype'
Identification : 'DVD A  DS8A1H   '
Revision       : 'WH66'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
Driver flags   : SWABAUDIO BURNFREE 
Supported modes: PACKET SAO
Speed set to 3324 KB/s
Starting to write CD/DVD at speed   2.0 in real unknown mode for single session.
Last chance to quit, starting real write in    0 seconds. Operation starts.
[B]Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
CDB:  53 00 00 00 00 00 3E 32 B0 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 27 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x27 Qual 0x00 (write protected) Fru 0x0
Sense flags: Blk 0 (not valid) [/B]
cmd finished after 0.366s timeout 40s
wodim: Cannot open new session.
```
and Growisofs:
```
growisofs -dvd-compat -Z /dev/dvd=./creaturefactory.ISO 
Executing 'builtin_dd if=./creaturefactory.ISO of=/dev/dvd obs=32k seek=0'
/dev/dvd: splitting layers at 2038112 blocks
**:-[ SEND DVD+R DOUBLE LAYER RECORDING INFORMATION failed with SK=5h/WRITE PROTECTED]: Input/output error**
```

I also tried IMGBurn with wine. But also had the same kind of output. Bascially for some reason the drive is write protected when trying dual layer. I know this is a dual layer drive and just for kicks this is some of the output from k3b showing this:
```
(K3bDevice::Device) /dev/sr0 feature: CD Mastering
(K3bDevice::Device) /dev/sr0 feature: CD Track At Once
(K3bDevice::Device) /dev/sr0 feature: CD-RW Media Write Support
(K3bDevice::Device) /dev/sr0 feature: DVD Read (MMC5)
(K3bDevice::Device) /dev/sr0 feature: DVD+R
(K3bDevice::Device) /dev/sr0 feature: DVD+RW
**(K3bDevice::Device) /dev/sr0 feature: DVD+R Double Layer**
(K3bDevice::Device) /dev/sr0 feature: DVD-R/-RW Write
(K3bDevice::Device) /dev/sr0 feature: Rigid Restricted Overwrite
(K3bDevice::Device) /dev/sr0 feature: Layer Jump Recording
```

I have only tried one brand, so that could be a problem, but I doubt it.
This burns normal dvds and cds just fine.
I have tried this with root (both sudo and su) and have boot into recovery mode and tried it there as well.
Any help would be greatly appreciated! I have download puppy, and am going to live boot it and see if it is able to burn anything, but I wanted to go ahead and post this here because my hopes aren't high...

Thanks All!
Kory

---

### Post by gali98 on 2009-09-25
Fail. Puppu gave the same kind of messages. I am now going to try and compile the latest versions of wodim and its libraries. Will update.
If anyone knows anything, or even something to try, please post :)
Kory

---

### Post by gali98 on 2009-09-25
Compiling the latest version (which happens to be the version in ubuntu now) doesn't make a difference. I may take a stab at running windows in a vm or installing it into another partition. I'm also going to try my media in another drive. When possible, I am going to aquire dual layer dvd-r media and see if that works.
Kory

---

### Post by gali98 on 2009-09-26
After sufficient research, I have discovered that DVD-R DL (note the minus) are either not manufactured at all, or are very scarce, so that would rule out that problem.
The Karmic beta comes out soon, and I will test it with that then. Until then, I will just deal with it.
Kory

---

### Post by gcbzzzz on 2009-10-16
where do you find dvdrecord?

can't find it's package anywhere

*update* dvdrtools.

also, i don't knot it's possible to burn DL medias.

---

