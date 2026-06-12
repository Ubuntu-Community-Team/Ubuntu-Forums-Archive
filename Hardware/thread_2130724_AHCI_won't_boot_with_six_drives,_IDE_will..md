---
title: "AHCI won't boot with six drives, IDE will."
date: 2013-03-30
forum: Hardware
---

### Post by creepwood on 2013-03-30
I've disassembled my FreeNAS drive and moving the drives over to my ubuntu machine (12.10).

Pre-move: I had two drives. one system (750GB) drive and one datadrive (1500GB) on an ABIT IP35 PRO mobo. It has 6 sata ports on an ich9 controller. It also has 2 esata ports on a Jmicron controller (not used)

After-move: four more drives. maxing out the internal SATA ports. the computer halts where it should boot from a drive telling me that there isn't any boot drive. I've checked that the boot order is right. It doesn't matter if which 6 drives I'm using, I've tried with 6 different drives in the 4 spots that were left over before moving over the drives. I tried different cables. I've tried a different PSU. I've tried having a second PSU power two of the drives since I had my suspiciouns that it was a power problem. I tried with replacing two of the drives from the FreeNAS system to just make sure it doesn't try to boot from my ZFS volume which the four drives were part of.

What I finally did was reset my BIOS and it didn't work. I started messing with the SATA settings in BIOS and finally it booted with 6 drives, but with IDE instead of AHCI. I would like for it to work with AHCI. I am not using the IDE port on the mobo

Does anyone have any idea?

EDIT: I did install Ubuntu with AHCI enabled.

---

### Post by dabl on 2013-03-30
Couple of thoughts:

- Some BIOS's like the "boot" flag set on the bootable partition -- you might check that, and also make sure there is only one partition set that way.  And of course make sure the BIOS is upgraded to the current release.

- I assume these are all hard disk drives, and no SSDs.  Because most SSDs actually perform better in "legacy" or IDE mode, and some aren't recognizabe as bootable devices by some BIOS's.

---

### Post by creepwood on 2013-03-30
I am fairly new to linux and I'm unfamiliar with many of the operations. And I'm unsure how I do check the boot flags. I read a little about it, but I don't want to mess things up.

How would I check if the boot flag is set on the other drives. They shouldn't be, but they might be.

I also did a little more research. I set up a USB-thumb drive as boot device as #2

If 6 drives and no USB drive it doesn't boot.
If 6 drives and with USB drive, it boots from USB
if 5 drives and with USB drive, it boots Ubuntu.

This is getting weirder and weirder.

EDIT: and yes, these are all HDD

EDIT#2: I just checked the BIOS update page, there is an AHCI update to the second newest BIOS. But right now. ABIT's ftp doesn't seem to host the files anymore.

---

### Post by creepwood on 2013-03-30
Problem solved. It was a BIOS upgrade that was needed. 

Thank you for your help.

---

### Post by dabl on 2013-03-30
Good -- glad it's fixed.

---

### Post by creepwood on 2013-03-30
Sadly. What happened was that now my mixed memory sticks won't boot. I had 2 x 2GB PC6400 DIMMS and 2 x 2gb PC3200 DIMMS and it won't boot when it's mixed like it did before the BIOS flash.

---

### Post by dabl on 2013-03-30
Your PC3200 is way under the FSB speed rating for your motherboard, which is PC6400.  You apparently got lucky with an earlier BIOS that wasn't checking the DIMM speeds.

---

### Post by creepwood on 2013-03-30
That's not the problem. I'm using 333mhz and 400mhz now to get 6GB of ram instead of the previous memory. It's just that the old setup doesn't work anymore.

---

