---
title: "Mounting SATA Drives by Label?"
date: 2009-10-30
forum: Hardware
---

### Post by kgearhardt on 2009-10-30
So I've got an 8-year old 2GHz Dell P4 system that I just finished setting up with Desktop 9.10. My primary use for the system is as a home media server. I have a Norco 4618 PCI 4-port eSATA controller with 4 AMS DS-2350S 5-bay SATA enclosures attached, fully populated with drives. Right now everything's working fine as long as my /etc/fstab uses /dev/sdb1-sdbu1 for the device. The drives are loaded with my entire movie collection and were previously attached to a Windows Vista HTPC, so they're all formatted as NTFS. If I try and modify my fstab file to use LABEL=MyMedia01-20 for all 20 drives to avoid any future boot sequencing problems, the drives are not mounted at boot time.
 
From reading this forum and other sources I gather that the "LABEL=" capability does NOT work for NTFS formatted drives, is that correct? Is there some other trick I might be able to use other than moving data, reformatting drives, and moving data back? I'd rather not do that since I'd like to retain the ability to move the enclosures between the Ubuntu PC and the Vista PC in the future.
 
Thanks, Kevin (P.S. This is my first linux setup at home. I like it but I'm certainly not experienced with linux administration. Just got my "Linux Administration Handbook" from Amazon.com today!)

---

### Post by coffeecat on 2009-10-30
You can use UUIDs for NTFS drives. They should be unique. Use the form "UUID=" for the first field in fstab, and you can get the UUIDs of your drives with "sudo blkid" from a terminal.

---

### Post by sisco311 on 2009-10-30
Using the LABEl is prefered for external disks.

For internal disks use the UUIDs:
[uhelp]community/UsingUUID[/uhelp]

To get the UUID of the partition:
```
sudo blkid
```
or
```
sudo blkid /dev/sd##
```

i.e.
```
sudo blkid /dev/sda3
/dev/sda3: LABEL="home" UUID="e2bdf561-94b1-45f0-af97-02d43a1890c1" TYPE="ext4"
```
the fstab entry for /dev/sda3 would look like:
```
UUID=e2bdf561-94b1-45f0-af97-02d43a1890c1   /media/data ext4 relatime 0 2
```

---

### Post by kgearhardt on 2009-10-30
> **coffeecat said:**
> You can use UUIDs for NTFS drives. They should be unique. Use the form "UUID=" for the first field in fstab, and you can get the UUIDs of your drives with "sudo blkid" from a terminal.
 
I actually tried setting up the fstab file with UUID= as well, but that didn't appear to work either, i.e. same results as LABEL=.  I'll give it a shot again this evening to make sure I didn't screw up the UUID value.  Thanks!

---

### Post by coffeecat on 2009-10-30
"UUID=" certainly works fine with NTFS partitions with my simple home setups - that is, NTFS partitions on internal discs (either sda or sdb) connected directly to the SATA connector of the motherboard. Whether it will work with your more sophisticated hardware setup, I don't know. I would be interested to hear.

By the way, I've come across one little glitch when copying files (using the GUI at least) from an ext3 partition to an internal NTFS partition. Depending on the fstab mount options, the date/time stamp gets changed to current - which is highly irritating. This happens with the Ubuntu installer default fstab setup for NTFS partitions which is:

```
UUID=C052B04A52B04746 /media/Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```By trial and error, I found that a simple....

```
UUID=C052B04A52B04746 /media/Data     ntfs    defaults   0       1
```... solved this particular problem. If it intruduces others, I have yet to encounter them. What annoys me is that this has been going on since Hardy, if not before. If you select 'Manual' in the installer and specify a /media folder for an NTFS partition, you get "nls=utf8,umask=007,gid=46" in the fstab line, and the problem must lie somewhere in there. Exactly where I have neither the energy nor inclination to determine - not while "defaults" does the business for me. And, yes, I have posted about this on Launchpad. It was ignored.

Good luck, anyway.

---

