---
title: "ubuntu-8.10-alternate-powerpc.iso not verified in Disk utility - errors"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by Cyanaether22 on 2009-02-03
Hey! So I've already burned a copy of the 8.10 Alternate Install CD for PowerPC, but I wasn't reading the instructions carefully so I burned at 8x without verifying anything.

When I tried installing, I got LOADS of corrupt file & debootleg (or something like that ) errors during the actual installation step, and as a result it failed.

So this is my second time around burning the CD, I'm trying to be very careful not to waste another CD. I've downloaded the image via BitTorrent and when I put it into Disk Utility I encountered a few problemos.

First of all, there is no MD5 option in the menu Images > Checksum. All I see there is CRC-32 image checksum. So I used that, and then tried verifying it. Here are the logged results:

```
Checksumming “ubuntu-8.10-alternate-powerpc.iso” using UDIF-CRC32
	Checksumming Driver Descriptor Map (DDM : 0)...
	     Driver Descriptor Map (DDM : 0): calculated CRC32 $56C99300
	Checksumming Apple (Apple_partition_map : 1)...
	     Apple (Apple_partition_map : 1): calculated CRC32 $89A721A1
	Checksumming Ubuntu 8.10 ppc                  (Apple_ISO : 2)...
	Ubuntu 8.10 ppc                  (Ap: calculated CRC32 $91E44B2C
	Checksumming Ubuntu 8.10 ppc (Apple_HFS : 3)...
	     Ubuntu 8.10 ppc (Apple_HFS : 3): checksum failed with error 22.
Unable to checksum  “ubuntu-8.10-alternate-powerpc.iso” - Invalid argument.
Verifying volume “Ubuntu_PowerPC_intrepid”
Checking HFS volume.
Invalid number of allocation blocks
The volume  needs to be repaired.

Error: The underlying task reported failure on exit

```

I'm hoping this is just Disk Utility, or myself being stupid. So I went into Terminal and did the trick where you type "md5 " and then drag in the file.

It resulted with this hash:

96aae33958e0e1a6f6cf1ee4d4cd9b7c

I looked on the web at various pages, and the hash for ubuntu-8.10-alternate-powerpc.iso isn't there.

So all I'm really asking is whether or not this ISO is good to burn and install successfully on my iMac G3 Bondi Blue Slot-Loading PowerPC.

Background Note: I'm hoping this alternate-powerpc install will result in the graphical Linux OS? Please correct me if I'm wrong, or suggest anywhere where I'm going wrong in any of this.

Thanks a lot. :)

---

### Post by Cyanaether22 on 2009-02-04
Alright, I went ahead and burned it since no answer here.

It worked just fine, the installation was just finishing but now when it was on "Unmounting and ejecting the CD" my crappy CD slot wasn't doing a good job of pushing it out, so it went back in.

I used the paper clip technique to get it out, but I think the installation got hung because it's not doing anything now. I can use Ctrl-Alt-F2 to bring up another console but not sure what to do there.

HELP! What do I do? Is it okay to restart and try to redo the finishing step?

Quick answers would be MUCH appreciated.

---

