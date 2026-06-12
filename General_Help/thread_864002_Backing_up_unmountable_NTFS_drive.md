---
title: "Backing up unmountable NTFS drive"
date: 2008-07-19
forum: General Help
---

### Post by spoketire on 2008-07-19
I've got a NTFS drive that has windows xp on it, but it won't boot, and I can't mount it in linux.  It won't mount because it has GRUB in its MBR, which caused a filesystem error (I think).

I really need to back up the important stuff from that drive before I try to mess with the windows installation.  I've tried out several things, including TestDisk, PhotoRec, and ntfsclone, none of which could get around the fact that the drive won't mount.

If there's a way to get any of these tools to work even though the drive doesn't mount, or if there's a solution using other programs, I would appreciate instructions, since I haven't found any specific instructions for any of these programs.

Also, I've got a second hard drive with Ubuntu on it, which is booting, so I can use that to store backups if I need to.

---

### Post by jimv on 2008-07-19
what happens when you do:

mount -t ntfs-3g /dev/theNTFSdrive /somedirectory

Do you get an error message?

---

### Post by Sef on 2008-07-19
Download [Knoppix]("http://knoppix.com") and burn an iso.  Then you can transfer your data to another disk.

---

### Post by spoketire on 2008-07-19
jimv, I get this error when I try the command you suggested:
```
NTFS signature is missing.
Failed to mount '/dev/sda': Invalid argument
The device '/dev/sda' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```
I don't think it's a matter of sda vs sda1, because I've tried both ways and neither one works.

Sef, I don't mind trying out Knoppix, but since I'm pretty new to Linux, could you tell me how I would go about transferring the data, or give me a link to instructions?

---

### Post by Zack McCool on 2008-07-19
it is a matter of sda vs sda1 (or whatever).  /dev/sda is a hard drive.  /dev/sda1 is a partition.  A drive cannot be mounted, a partition (filesystem) can.

Also, are you sure it is sda1, and not something else?  How about giving the output of the command fdisk -l /dev/sda

And grub is not your issue.  The MBR is not part of your partition.  You can do what you want to the MBR without affecting the partition, though you can keep it from booting...

---

### Post by spoketire on 2008-07-19
mount -t ntfs-3g /dev/sda1 /media/win gives:
```
Unexpected clusters per mft record (-127).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
```

fdisk -l /dev/sda
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x765c765c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS
```
I'm pretty sure sda1 is the right one, since it's the only ntfs drive on my system.

If grub is not my problem, then what is?  I have booted directly to the ntfs drive in BIOS, and all I get is "GRUB," and the computer sits there.

---

### Post by spoketire on 2008-07-19
Ok, I've found out that when I boot the ntfs drive with the Ubuntu drive disabled, I just get "GRUB" printed. However, when I boot the ntfs drive with the Ubuntu drive enabled, I get the actual Grub menu. I also get the grub menu when booting the ubuntu drive.

Am I correct in deducing that my ntfs drive doesn't have the actual GRUB on it, but it just redirects the system to the GRUB on the ubuntu drive when booting? If so, how can I make the ntfs drive load its own bootloader instead of grub? If I could get the ntfs drive to boot windows, then I wouldn't have to worry about the data recovery, since I could just do it inside windows.

---

### Post by Taxman415a on 2008-07-19
> **spoketire said:**
> 
Am I correct in deducing that my ntfs drive doesn't have the actual GRUB on it, but it just redirects the system to the GRUB on the ubuntu drive when booting? If so, how can I make the ntfs drive load its own bootloader instead of grub? If I could get the ntfs drive to boot windows, then I wouldn't have to worry about the data recovery, since I could just do it inside windows.

Yes, that's the way grub works, it installs an MBR that redirects booting after that to GRUB on the Ubuntu drive. You can do what you're asking by restoring the MBR (google for that phrase, there are lots of ways to do it and I can't think of them off the top of my head.) You probably want to back up your current one to make things easy for yourself. I think the partitionmagic livecd (50mb) does this all pretty easily.

But the bigger problem isn't that the bootloader isn't trying to boot XP, it's that the filesystem is hosed. Trying to boot it will likely fail. Instead of going through the above you could just try booting from your XP install cd and using what recovery it has.

Also, reading back to your original question, most of those tools don't require that the partition be mountable, so I'm not sure how that became a problem. I guess give us specific errors or ask on the tool's mailing lists/IRC channels. Also try this guide: [http://www.informationweek.com/shared/printableArticle.jhtml?articleID=208403254](http://www.informationweek.com/shared/printableArticle.jhtml?articleID=208403254)  It explains the need to create an image of the parition/drive before making things worse and links to how to use some of the tools.

---

### Post by spoketire on 2008-07-19
About the MBR, I tried FIXMBR from the XP reinstall cd, and it acted like it did something, but when I boot the ntfs drive, it still redirects to grub.  Maybe there's a better way to restore the MBR?

I've tried making an image of the drive with partimage, and I get this:
```
terminate called after throwing an instance of 'std::bad_alloc'
what():  std::bad_alloc
```

I've tried testdisk and photorec too. In both of these, I create a new log file, select the disk, and then it just prints root@computername:~# and sits there. 

You're probably right that the problem isn't that the drive can't mount. I think the problem might be that the filesystem has an inconsistency or error, and none of the recovery programs I tried could handle that.

Someone suggested knoppix, and I'm not sure if that would be any easier than just running the same utilities from Ubuntu.  And if I try using knoppix, should I use regular knoppix or [knoppix s-t-d]("http://www.knoppix-std.org/")?

---

### Post by Taxman415a on 2008-07-19
> **spoketire said:**
> 
I've tried testdisk and photorec too. In both of these, I create a new log file, select the disk, and then it just prints root@computername:~# and sits there.
I've not yet had filesystem corruption and a need to test these tools out, so I don't know, but it sounds like they were working. I think they take a while.

> 
You're probably right that the problem isn't that the drive can't mount. I think the problem might be that the filesystem has an inconsistency or error, and none of the recovery programs I tried could handle that.
It shouldn't be that, those tools ignore the filesystem data to an extent, but I suppose it is possible. You could try the other tools listed in that article I linked, starting with ddrescue, then foremost or scalpel. All are installable with apt-get, etc.

> 
Someone suggested knoppix, and I'm not sure if that would be any easier than just running the same utilities from Ubuntu.  And if I try using knoppix, should I use regular knoppix or [s-t-d]("http://www.knoppix-std.org/")?
I think they would have the same tools.

---

### Post by spoketire on 2008-07-19
> I've not yet had filesystem corruption and a need to test these tools out, so I don't know, but it sounds like they were working. I think they take a while.
Should it really take that long in the step right after the hard disk is selected? (this is right before you select the partition table type, according to the testdisk documentation) It seems like it is just passing control back to the terminal so you can enter commands.

I'll try ddrescue and let you know how it goes.

---

### Post by spoketire on 2008-07-19
I am currently imaging the ntfs hdd with ddrescue (gnu ddrescue, not dd_rescue).  I'm copying the ntfs drive to an image on the Ubuntu drive, and I am pretty surprised it's working so far, since everything else for the last 2 days has not worked at all!

However, both my drives are 160GB, so will there be a problem with filling up my Ubuntu drive?  The ntfs drive had about 80GB used, so I'd think it would be possible to just make an image file of the used space, but I'm not sure.

Edit: Assuming this image backup finishes smoothly, what should be my next course of action: extract the filesystem, try to get individual files (since the drive hasn't been mounting), or something different?

---

### Post by Taxman415a on 2008-07-19
> **spoketire said:**
> Should it really take that long in the step right after the hard disk is selected? (this is right before you select the partition table type, according to the testdisk documentation) It seems like it is just passing control back to the terminal so you can enter commands.

Hard to tell without seeing it and knowing exactly what you're running. Yeah, I suppose that doesn't sound right. I guess this is where you have to ask for help from those specific tools' sites.

And yeah, if you try to image the whole first disk you've got a problem, but again I don't know the tool's syntax to avoid doing that. But once you get the image, you can try any of the other tools on it. I guess try foremost and scalpel and see if they are easier for you.

---

### Post by spoketire on 2008-07-19
I stopped the image at about 120GB out of 160GB, so I guess it might have all the used space on the disk inside the image, unless it was really fragmented and some of it is in the last 40GB.

Then I ran foremost on it to get as many files off it as I can. It found about 26,000 files before I stopped it, but it wasn't saving any of them to the directory I specified. Does it wait to do the saving till the very end?

I would really like to rebuild the filesystem if possible though, because then I could browse through the folders as they were before instead of looking through a huge list of files without the original names.  Is sleuth the only thing that can do that, or are there other ways?

By the way, thanks for all the help I've gotten so far from everyone. I'm starting to see the light at the end of the tunnel, but I've still got a long way to go.

---

### Post by spoketire on 2008-07-19
Ok, sorry to double post, but I'm going to try using Scalpel instead, since foremost didn't actually save any files.  Scalpel and Foremost have a number of file formats built in and supported, but I would really like to be able to restore some more formats.  Does anyone know of where to find configuration files for other formats?  In particular, I need them for .blend and .mus. Thanks!

---

### Post by librarian on 2008-07-29
I'm having a similar problem with a crashed NTFS drive. When I ran foremost, I knew it created a ton of files, but I couldn't see them. Turns out I needed to chown the directory...

```

sudo chown -R youruser:youruser /path/to/recovery/foremost

```

---

### Post by spoketire on 2008-08-09
I've finished doing my file recovery for that drive, but you might find these two pages helpful. I don't know though, it depends on what your problem is.

[http://matt.matzi.org.uk/2008/07/03/reconstructing-heavily-damaged-hard-drives/]("http://matt.matzi.org.uk/2008/07/03/reconstructing-heavily-damaged-hard-drives/")
[http://forums.gentoo.org/viewtopic-t-365703.html]("http://forums.gentoo.org/viewtopic-t-365703.html")
I think the second one is supposed to be better, but I haven't tried either of them.  What they do is reconstruct the file/folder structure if you have a damaged filesystem (I think).

---

