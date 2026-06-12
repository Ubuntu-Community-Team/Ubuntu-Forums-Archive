---
title: "Has my hardrive died or is it just a fixable error?"
date: 2011-04-15
forum: Hardware
---

### Post by mattsony on 2011-04-15
Well i had ubuntu 10.10 installed on the master drive of a two HDD machine. it was working fine but when i tried to do a clean install with natty narwal beta, it failed. so i tried a different disk, same error same spot. i booted into XP and the master drive which used to be used for pictures and even when ubuntu was installed on it, was visible, no longer is. so back in ubuntu(now on live CD because 10.10 was erased) i start up disk utility and try to format it, of course it fails coming back with this error:
    error creating partition table: helper exited with exit code 1: in
    part_create_partition_table: device_file=/dev/sda,
    scheme=0
    got it
SMART data status says the disk is healthy but im really not sure.

---

### Post by dandnsmith on 2011-04-16
> so i tried a different disk
Is this a different CD or the other HDD?

> i booted into XP
So, how are you achieving this? Have you changed the boot sequence (as XP doesn't normally like not being on the first HDD?
Is that HDD still visible to the BIOS - presumably so, to get the SMART report

> i start up disk utility why not use gparted - it's safer and better?

I guess that you are using the same partition for installation that 10.10 was installed in?

---

### Post by mattsony on 2011-04-16
it was a different dvd with ubuntu 11.04 burned on it. 
Also, the machine has two HDDs on it and one has windows xp loaded. it only boots to xp because the drive with ubuntu was wiped.

---

### Post by Edward46 on 2011-04-16
I am going to bring this up just in case, but is the drive recognized under the bios?  Ironically enough, while upgrading from 10.04 to 10.10 on a dedicated second drive, my sata port failed on the motherboard.  I originally thought that my drive failed until I changed ports.  Just think, a port that has never been used until recently, blows up because of a linux upgrade:shock: 

The upgrade process finished, but it was during the reboot process when the port failed.

Edward K.

---

### Post by mattsony on 2011-04-16
yes it is, in bios it shows up as the master HDD 320 GB. it also connects to the drive in live CD mode but its unable to do anything in regards of formating.

---

