---
title: "Nvidia &quot;soft&quot; RAID not working."
date: 2005-05-14
forum: Hardware &amp; Laptops
---

### Post by himuraken on 2005-05-14
Just to warn you this is a long winded but important question because I know that many users are having this identical problem since so many people are using these motherboards with SATA RAID configurations. I have just installed Ubuntu 5.04 onto my system. I am using a MSI Nforce2 Ultra 400 motherboard with 1 gigabyte of RAM, and a AMD Athlon 2500 Barton. My hard drive setup is as follows: 40Gb Maxtor on IDE 1, 100Gb Western Digital on IDE3 (Part of the onboard Promise "RAID"), and 2 Western Digital 200GB drives on SATA1 and SATA2. Ubuntu is installed on the 40Gb drive and is working perfectly. I am unable to gain access to the 100Gb and 200Gb drives. The 200's are setup in a RAID 1 mirror. All three drives in question were originally formatted NTFS under XP Professional and were working correctly. Ubuntu's device manager shows all three "missing" drives, each is under the category "SCSI Host Interface->SCSI Device->DRIVE NAME->Volume. From researching online I have found dozens of people that are having the exact same issue. Apparently these so called RAID controllers are really "soft" or "fake" driver/BIOS controllers. Sounds almost like a WinModem in linux situation. Does anyone have clear cut instructions or a link to a howto? The catch to this whole situation is that I [COLOR=Red]CANNOT[/COLOR] format the drives and set them up with linux software RAID because data is on all three drives. Any help would be greatly appreciated. Thank you in advance!

---

### Post by nad on 2005-05-14
The problem as I see it is that you now need to use the nvidia linux driver instead of the nvidia windows driver to control your array. This is an nvidia problem. Please see several recent news articles decrying the use of closed source software in open source projects.

As far as using the drives, the 100G unit should be available as a separate drive, whatever the filesystem type. Knowing promises' past, there is probably some non-standard code in the partition table. The 200G drives in mirror should be able to be separated. From windows, remove one of the drives from the mirror configuration and shutdown and remove all the large drives. Install the 'spare' drive, boot up ubuntu and create a mirror raid with a missing spare. Make your filesystem and shut down. Reinstall the active ntfs raid drive and copy the data over. Then add your missing spare to the new linux raid. Easy.

Of course, if you can not access the drives separately because of non-standard and/or proprietary coding, this whole excerise is moot.

---

### Post by himuraken on 2005-05-15
Have you worked with dmraid at all? I have heard some success stories using it, but I am unsure which direction to proceed. Where do I access filesystem/RAID tools in ubuntu?

---

### Post by nad on 2005-05-15
I've worked with promise, highpoint and adaptec raid controllers and linux software raid. I have yet to work with any flavor of sata raid. dmraid could work as the nforce format is now supported. This is something I have been following but have yet to work with. Your instance seems to be a good fit with the technology and as there are non-destructive test procedures you have nothing to lose but time and effort. 

man mdadm, man evms

---

### Post by himuraken on 2005-05-15
Where do I access filesystem/RAID tools in ubuntu?

---

### Post by nad on 2005-05-15
man mdadm, man evms

---

### Post by himuraken on 2005-05-15
Thanks Nad, I have found a great HowTo on the Ubuntu forums dealing with this exact situation and a solution using dmraid. Here is the link to the HowTo: [http://ubuntuforums.org/archive/index.php/t-2557.html](http://ubuntuforums.org/archive/index.php/t-2557.html) . The problem that I am having is now with dmraid. When I run   dmraid -ay -v all of my SATA partitions are activated. But when I run     [COLOR=DarkRed]mount -t ntfs -o users,owner,ro,umask=000 /dev/mapper/pdc_edafhjfg /home/himuraken/sataraid/[/COLOR] I get this error:    [COLOR=DarkRed]mount: /dev/mapper/pdc_edafhjfg already mounted or /home/himuraken/sataraid/ busy[/COLOR]. Any idea as to why I am having this mount issue?

---

### Post by nad on 2005-05-15
1 You can not give a mount command from the mount point
2 Try logging out and back in
3 Gnome volume manager still has some issues regarding the entire hotplug subsystem

---

### Post by himuraken on 2005-05-15
Ok, I logged out and then at the console as root, I ran the same command to mount the dmraid device and go the same exact error, I am thinking that I might just get my 200Gb's of data onto another medium, wipe the drives and setup a raid in linux. I was really hoping to gain access to them through dmraid.

---

### Post by nad on 2005-05-15
Have you tried unmounting, maybe with the lazy switch?

umount -l /home/himuraken/sataraid/

and remounting?

---

### Post by himuraken on 2005-05-15
Nad thanks for all of your help. I was tinkering around in the console figured something out. Hopefully this will help any other users that are having this issue. I was able to sucessfully mount the drives when I referenced the disk itself not just the partition, such as: [COLOR=DarkRed]mount /dev/sda1 /home/himuraken/sataraid[/COLOR]. Now while this doesn't mount the entire RAID volume, it does allow you to get access to the data. Now that I can access either of the 200Gb drives, I will format one, copy the data to it, format the other, and then let the linux software RAID rebuild them. This seems like a sound plan to me.

---

