---
title: "Sil57xx (Sil5744 or Sil5734) SteelVine Hardware-RAID-Controller"
date: 2009-07-13
forum: Hardware
---

### Post by Master One on 2009-07-13
I have two [CH3B2E](http://www.conceptronic.nl/site/desktopdefault.aspx?tabindex=1&tabid=232&cid=30&gid=3010&pid=CH3B2E[/url) storage devices from Conceptronic here, each fitted with two Samsung HE103UJ 1TB Raid- & 24/7 approved drives. That unit has a built in Hardware-RAID-Controller, which identifies as Sil57xx SteelVine.

For M$ Windows there is a 57xx SteelVine Manager software from SiliconImage, which is needed to configure the RAID-mode (I chose RAID1) and to upgrade the firmware, which I just did. The upgrade-firmware-submenu asks for a Sil5744 or Sil5734 firmware image, which is one and the same file to be downloaded from the SiliconImage website. After the upgrade it shows "IC Revision # Altair2" and "Firmware 1.1576".

The unit can be connected to a computer by either USB or eSATA. On my workstation with Ubuntu 9.04 it is recognized correctly, but as expected, smartctl can not show any info, so unless there is a way, to run that SteelVine Manager under Linux, the RAID/drive status can not be checked, exept visually by looking at the LEDs on the front of the unit.

Does anybody else have any experience with that unit or that kind of RAID controller?

I really would like to access the RAID/drive status remotely somehow. On one hand using a Hardware-RAID makes much more sense then a Software-RAID (no OS intervention, no CPU power needed for running the RAID), on the other hand it's very convenient having mdadm for managing. The CH3B2E can be run in JBOD mode as well, but then an eSATA controller, which can handle two drives on one channel, is needed, and it would have the downside of SATA bandwidth sharing on that one channel for both drives.

---

### Post by Master One on 2009-07-14
Ok, this is pretty cool! I have completely overlooked, that there is a [SteelVine Manager for Linux]("http://www.siliconimage.com/docs/57xxLinuxSteelVineManager_V5_1_24.tar.gz") available from SiliconImage. :)

It is an archive for FC6, and contains a daemon and the GUI, which can be run on separate machines. I had no problems getting it to run on my workstation with Ubuntu 9.04. The SteelVine Manager GUI offers exactly the same functionality, as the M$ Windows version, and you can configure various email reports depending on event/condition.

The only downside seen so far: The CH3B2E device does not seem to report Box Temperature & Box Fan Speed, both values are shown as "N/A". I am a little concerned about the temperature, because the box got pretty hot during the SAFE rebuild phase (which took several hours). And of course it's a pitty, that the S.M.A.R.T. status can not be accessed, if the drives are configured as RAID1.

But from what I have seen so far, the Conceptronic CH3B2E device is a nice value deal, and fully supported for use with any Linux distribution.

---

### Post by joelandsonja on 2009-12-12
How did you get the .tar.gz file installed?  I have a new Mediasonic RAID dual bay drive.  Can't get it to work in Ubuntu without the driver, but can't get the .tar.gz file installed.  Can you help since you had a similar problem a few years ago?  I know it is an old thread but I need some help.  Thanks!

---

### Post by Master One on 2009-12-13
Sorry, can't help you on that. The mentioned TAR archive does not contain any driver, since it's an USB device, so it's only about the daemon and gui. I have the unit in use, but I didn't install the SteelVine Manager (yet), since it is now connected to a server running a Debian Lenny OpenVZ setup.

---

### Post by ajoliveira on 2010-04-20
> **Master One said:**
> I have two [CH3B2E](http://www.conceptronic.nl/site/desktopdefault.aspx?tabindex=1&tabid=232&cid=30&gid=3010&pid=CH3B2E[/url) storage devices from Conceptronic here, each fitted with two Samsung HE103UJ 1TB Raid- & 24/7 approved drives. That unit has a built in Hardware-RAID-Controller, which identifies as Sil57xx SteelVine.



I had that CH3B2E box. It is one of the most unreliable pieces of hardware I have ever seen, in 4 months two boxes down. It is essentially non-compliant with European regulations (metal case without ground) so you must connect it to either the esata or usb port and power it afterwards. Even will all the care, the interfaces are bound to be dead very soon and the device will be useful as a brick...
Furthermore, when you shut down the host or disconnect the cable, the box continues to keep hard disks very alive and consuming power. If on mounting you don't see where you route the second hard disk cable, it will block the fan and the unit will overheat happily, there is no temperature limit switch.
In USB mode transfer is about 85% of what you may get from a cheap block like WD Elements (check this: [http://www.linuxinsight.com/how_fast_is_your_disk.html](http://www.linuxinsight.com/how_fast_is_your_disk.html) ), even if you use fast F3 Samsungs.
In short, a complete trap. I alerted Conceptronic about this, and no answer whatsoever was obtained. Fine customer support as well. Not recommended for faint-hearted. For masochists only.

---

### Post by Master One on 2010-04-20
How strange, I have two of these units here in use since about a year, and had no problems since, except that I had to exchange the fan on one unit, because it was not doing well. But you are right, that device is pretty much crap, but it was the cheapest external Hardware-RAID1 I could get at that time.

---

### Post by ajoliveira on 2010-04-20
Hi

You don't move those around too much, do you (i.e. no connections/disconnexions, power cycling)? That must be the reason. The last time the unit turned into a brick by being powered one day and re-powered the next one. Every time you do it you may hear the "tchac" noise and see the flash if you are in the dark due to the huge power surge.
Aargh, I was forgetting, in the non-raid mode any controller non supporting the steelvine extensions will not get to see the second hard disk in esata mode. So keep embedded controllers away.
Ordered a couple of 2Hix cheap boxes, don't need raid anyway in this application (streaming hd video).

---

### Post by ajoliveira on 2010-04-22
Hi

With the 2hix boxes, measured USB disk transfer rate went up 27% from 15MB/s to 20MB/s with the Samsungs... and each one was 18EUR+TVA... Grounded plug power supply, grounded aluminium box, clean mounting with no screws, great value for the money.

---

