---
title: "[SOLVED] Installing Ubuntu onto RAID"
date: 2008-12-27
forum: Installation &amp; Upgrades
---

### Post by ggb-uk on 2008-12-27
[LEFT][COLOR=black]xLde>en Googlec[IMG]http://ubuntuforums.org/data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABwAAAAOCAYAAAA8E3wEAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1QUUDyoqJjAqRwAAAN1JREFUOMu1lMkVwyAMBYe0JGpCNUFNVk3k4AUwxPGS+ILxkzX8jyTH/Sfu9nrmJ3cXlnMASyWRPwd2d5XlHCBZn1BthcbRAdxTZQDI8k3mQzg11rhF+QZ9jdNOcQib6GFQYJYgCFucSRf6GsLU6wEY5yubTFqF2yq1vRwr3INXdQUWG+je1pELX4ED1wDyRAR0WfuAA9gloITyvsFMIMgYInYRqF6rO9Sqz9qkO5ilyo0o3YBwJ+6vrdQonxWUQllhXeHcb/wabMPkP2n81ocAIoLZrMqn/4y2RwP8DcQ+d6rT9ATiAAAAAElFTkSuQmCC[/IMG]
[/COLOR][/LEFT]
 	 	 I have been trying to install Ubuntu (AMD64) over a RAID system for about a week now.
 

 No problems installing without the RAID, but despite every devious plan I could imagine, I have been unable to persuade Ubiquity to install over the RAID, or when I have installed, it has not been a bootable system.
 

 The RAID is RAID-1 over two drives.
 

 The partition layout I would desire is a small /boot partition, a swap partition, and the root and all else on the remaining disk as a single partition.
 

 Firstly, I have created a startup USB pen drive from the Live CD so that I could add the RAID drivers so it can see the RAID when trying to install.  That was the easy bit.
 

 1) My ideal solution would be to allow the BIOS (NVidia chipset) to use fake RAID to manage the two drives.  That way I should be able to boot straight into RAID.
 

 Configuring the two drives in BIOS as RAID-1 drives, and starting Ubuntu from the USB pen drive:
 

  Linux sees the two separate drives, as well as seeing a RAID drive.  This means that whenever I try and partition the RAID drive, those partitions appear 3 times, once on the RAID, and once separately on each of the underlying drives that make up the RAID.  This is more an irritant than a serious problem, except when dealing with the swap partition, since Ubiquity tries to search for all swpa partitions it can find, and it finds 3 swap partitions, even though what it really sees is the two base swap partitions and a RAID image over the top of them.  Again, this is a problem that can be managed, since I have 4GB of RAM, and can do without a swap partition until the install is finished, and can tweak this afterwards.
 

 The killer for this is that while Ubiquity goes a fair way through the installation, but when it goes to installing Grub, and it crashes while trying to install Grub (some files have been placed on the /boot partition, but some other files are clearly missing).
 

 
[LIST=1]
[*]Using Linux soft RAID that is 	ignored by the BIOS, but contains partitions for swap and root 	(since the BIOS does not know about soft RAID, it cannot boot from 	it, so the /boot partition must be outside of the RAID – not a big 	problem, since this is static data that can be manually kept in line 	on the two disks).
[/LIST]
 

 Initially Ubiquity could not see the RAID drive under /dev/md0.  Since all of my drives (including the CD) are SATA, so I have no /dev/hd? Drives, so I created a hard link from /dev/hd0 to /dev/md0, and Ubiquity found the RAID under /dev/hd0.
 

 Managed to install this configuration, but upon booting, Linux would not auto-detect the RAID drives, so while Grub would load, it could not find the root partition.
 

 
[LIST=1]
[*]Using soft RAID on a partition by 	partition basis (i.e. no partitions inside RAID).
[/LIST]
 

 Since non-partitioned RAID (where /dev/md1 would map to /dev/sda1 and /dev/sdb1, and /dev/md3  maps to /dev/sda3 and /dev/sdb3) looks very much like a non-RAID partition, but with the superblock tagged onto the end of the partition – so it should be possible (so all I have read tells me to be the case) to boot off such a configuration.
 

 The problem is, how does one get Ubiquity to load a system onto the drives.
 

 Ubiquity does not recognise /dev/md1 or /dev/md3, so I cannot get it to place the system directly onto the RAID partitions, so the only way I can think of is to define the RAID pairs (add the superblocks onto the drives), then switch off the RAID, install onto /dev/sda1 and /dev/sda3, and then rebuild the RAID so that the installation is now mirrored on the other drive.
 

 The problem is that once the RAID pairs are created, I don't want to reformat sda1 and sda3, otherwise I lose the RAID superblocks, but Ubiquity seems to fail if I try and get it to install without formatting (I don't want to format, otherwise I will lose the RAID superblocks on the partition) it keeps telling me it cannot remove some operating system files it needs to remove.  I even tried changing the partition type back from FD to 82 (which I would change back after the install had completed) to see if this got around the issue, but to no avail.
 

 Anybody got any bright ideas about how I can achieve my objective?

---

### Post by ggb-uk on 2008-12-28
[LEFT][COLOR=black]xLde>en Googlec[IMG]http://ubuntuforums.org/data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABwAAAAOCAYAAAA8E3wEAAAABmJLR0QA/wD/AP+gvaeTAAAACXBIWXMAAAsTAAALEwEAmpwYAAAAB3RJTUUH1QUUDyoqJjAqRwAAAN1JREFUOMu1lMkVwyAMBYe0JGpCNUFNVk3k4AUwxPGS+ILxkzX8jyTH/Sfu9nrmJ3cXlnMASyWRPwd2d5XlHCBZn1BthcbRAdxTZQDI8k3mQzg11rhF+QZ9jdNOcQib6GFQYJYgCFucSRf6GsLU6wEY5yubTFqF2yq1vRwr3INXdQUWG+je1pELX4ED1wDyRAR0WfuAA9gloITyvsFMIMgYInYRqF6rO9Sqz9qkO5ilyo0o3YBwJ+6vrdQonxWUQllhXeHcb/wabMPkP2n81ocAIoLZrMqn/4y2RwP8DcQ+d6rT9ATiAAAAAElFTkSuQmCC[/IMG]
[/COLOR][/LEFT]
OK, problem solved.

I downloaded the text based installation CD  (the Ubuntu Alternate CD), and it installed beautifully - recognised the NVidia fake RAID, and just went ahead and partitioned and installed onto it.

---

