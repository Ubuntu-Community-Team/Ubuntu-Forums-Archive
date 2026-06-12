---
title: "I want to install on C: drive Help"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by mattbatt on 2009-04-28
So I currently have two XPs on my one hard drive the old one C: and the new one D:. I'm done with the old version of XP and would like to replace the C: partition with an Ubuntu install. 
Will I screw up my good XP install D: by removing the first Partition?  
Will XP recognize the Ubuntu partitions as C: or maybe C:, E:and F: ?  
Or will it ignore hda and try and boot it'self as C: only to fail since everything refers to D: ?

Thanks for your help

---

### Post by pastalavista on 2009-04-28
Before you install Ubuntu, first run the partition editor (System > Administration > Partition Editor) and delete your old Windows partition. Since you don't have an MBR any more, it will install grub (linux bootloader) on the Ubuntu partition. Just make sure you delete the right Windows. When you install, use manual mode and only use the now unallocated space on the drive. Linux doesn't lable drives like Windows does. [This guide]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") will explain better.

---

### Post by lisati on 2009-04-28
Don't forget to make a backup of important data. As much as we might not want to admit it, things can occasionally go wrong, even with the best planning.

---

### Post by mattbatt on 2009-04-28
yes I know all that stuff My question is How will Windows React to the first NTFS partition being gone?  
I had everything backed up on my External Drive and then my drive took a dive and I heard the heads scraping across the platters.  This happened last night so now I'm buying a new drive before I do anything.

---

### Post by pastalavista on 2009-04-28
> **mattbatt said:**
> yes I know all that stuff My question is How will Windows React to the first NTFS partition being gone?
It won't know anything's different except it won't be able to read or write to that drive any more.

---

### Post by shailendra on 2009-04-28
I suggest you to use C: drive for windows. This is because, windows sometimes look for C: drive by default. No one knows how windows will react if it doesn't find C: drive.

Then, create a new partition or use your D: drive for Ubuntu. I had done the same on my Dell laptop. Ubuntu does not have any problem with drives.

Most important, take backup of all your important data.

---

### Post by mattbatt on 2009-04-30
Thanks

---

### Post by Sef on 2009-04-30
> So I currently have two XPs on my one hard drive the old one C: and the new one D:. I'm done with the old version of XP and would like to replace the C: partition with an Ubuntu install. 
Will I screw up my good XP install D: by removing the first Partition?  
Will XP recognize the Ubuntu partitions as C: or maybe C:, E:and F: ?  
Or will it ignore hda and try and boot it'self as C: only to fail since everything refers to D: ?

Windows needs to be on the first primary partition.

---

### Post by Abu Sajid on 2009-05-01
> **Sef said:**
> Windows needs to be on the first primary partition.

Can you explain this a bit more? I don't understand it quite, because I have Vista on C, and XP on D, I'm using XP all the time, and it runs fine...

I had a question similar to mattbatt's question. I'd like to keep my XP, and install Ubuntu on C:. It's only because I want to do less work. :-)

---

### Post by dandnsmith on 2009-05-01
> **Abu Sajid said:**
> Can you explain this a bit more? I don't understand it quite, because I have Vista on C, and XP on D, I'm using XP all the time, and it runs fine...

I had a question similar to mattbatt's question. I'd like to keep my XP, and install Ubuntu on C:. It's only because I want to do less work. :-)

Windows after WinMe will quite happily exist on a non-C: drive.

I'm not sure what the precise installation requirements are, but I've installed Win95, Win98, WinMe on a primary partition which wasn't the first - the restriction was that it should be the first 'visible' partition (which excludes linux and other partitiontypes, as Windows just doesn't understand them).
Starting with XP, the conditions changed, and one of the additional changes was that they could be installed and co-exist with earlier Windows versions on the same HDD.

HTH

---

### Post by Abu Sajid on 2009-05-01
A great explanation, just what I needed, thanks a lot.

How can I now install Ubuntu on C:, where Vista is now? When I started the installation, Ubuntu was automatically placed on D:, and I couldn't change that, not with any of the options (guided resize, manual, etc.).

---

### Post by pastalavista on 2009-05-01
It may be possible to do what you want without re-formatting if you use ms-sys. [ms-sys.sourceforget.net]("http://www.google.com/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fms-sys.sourceforge.net%2F&ei=SCz7SdiEMt-Mtgfe07XaBQ&usg=AFQjCNHouAMN52pdpYF3GLVbuAbKrUFJYg&sig2=uPx7rr64Gq8HLNg0xrQiQg")

---

### Post by ezsit on 2009-05-01
Be very careful about overwriting your C: drive, Windows XP may have its first stage bootloader and the boot.ini file on the C: drive.

Even though Windows XP can be installed to another hard drive location, the Windows bootloader and boot.ini files must reside on the first primary partition on the hard drive, which is almost always C:

> I'm not sure what the precise installation requirements are, but I've installed Win95, Win98, WinMe on a primary partition which wasn't the first - the restriction was that it should be the first 'visible' partition (which excludes linux and other partitiontypes, as Windows just doesn't understand them).
Starting with XP, the conditions changed, and one of the additional changes was that they could be installed and co-exist with earlier Windows versions on the same HDD.

This sounds accurate except you neglect to mention that the Linux partition must be created BEFORE Windows was first installed for what you said to apply. If Windows XP was installed WHILE the first primary partition WAS a native Windows partition, Windows XP would have placed its bootloader on the C: drive.

Hopefully, if someone installs Linux over the C: drive, GRUB will take the place of the Windows bootloader, but I wouldn't bet my data on that.

---

### Post by Mark Phelps on 2009-05-01
> **Abu Sajid said:**
> A great explanation, just what I needed, thanks a lot.

How can I now install Ubuntu on C:, where Vista is now? When I started the installation, Ubuntu was automatically placed on D:, and I couldn't change that, not with any of the options (guided resize, manual, etc.).

I know the transition to Linux can be difficult, but you've got to quit using the "C", "D" terms for drives.  Those have no meaning at all in the Linux world.

If your first partition was formatted FAT32 or NTFS, of course Ubuntu didn't install to it -- it can't be installed to an MS Windows formatted partition.  It must be installed to an Ext3 (or Ext4 if you choose that option in 9.04) formatted partition.

If you want to install to the place occupied by your "C" drive, presuming that is the first partition on the drive, boot into the liveCD and use the Partition Editor to delete and reformat that partition.

---

### Post by Abu Sajid on 2009-05-01
> **Mark Phelps said:**
> I know the transition to Linux can be difficult, but you've got to quit using the "C", "D" terms for drives.  Those have no meaning at all in the Linux world.

If your first partition was formatted FAT32 or NTFS, of course Ubuntu didn't install to it -- it can't be installed to an MS Windows formatted partition.  It must be installed to an Ext3 (or Ext4 if you choose that option in 9.04) formatted partition.

If you want to install to the place occupied by your "C" drive, presuming that is the first partition on the drive, boot into the liveCD and use the Partition Editor to delete and reformat that partition.

At the moment I have only Windows installed, so I thought I shouldn't mix. :-) 

One thing confuses me: If Ubuntu couldn't install on the first partition because it was Windows formatted, why did it let me to choose the second partition to install Ubuntu on it? 

By the way, what do you think about ezsit's post, about Window's bootloader being on "C"? That should play a role if I reformat it, right?

Edit:

Thank you all for replying, and thanks in forward for future replies. I appreciate them very much. And sorry for (some :D) ignorant questions, I'm pretty new to Ubuntu.

---

### Post by ezsit on 2009-05-01
> By the way, what do you think about ezsit's post, about Window's bootloader being on "C"? That should play a role if I reformat it, right?

Simple. Check the root of the C: drive for the files:

ntldr
boot.ini
ntdetect.com

If these files are located on your C: drive, and not your D: drive, then the Windows bootloader is located on C: and therefore formatting C: will make Windows XP unbootable. These files are system files and hidden, so you will need to disable the hidding of hidden system files. Alternatively, you could open a CMD window and cd to the root of your C: drive and do a:

dir /a

to show the directory contents including system and hidden files.

---

### Post by mattbatt on 2009-05-01
I was most concerned with what Windows sees not what linux sees.  Linux doesn't care.  I think my easiest answer is going to be to delete all the content off of my C: drive use GParted to reduce the partition to as small as possible and reformat the rest for linux as hda3.  That way windows still sees a C: drive and it still has the bootloader unchanged.  Of course that means that It will want to still give the option of booting into the old XP install so I'll have to mess with the bootloader anyway. But first I still need to get a replacement drive for my broken one!

---

### Post by Abu Sajid on 2009-05-04
> **ezsit said:**
> Simple. Check the root of the C: drive for the files:

ntldr
boot.ini
ntdetect.com

If these files are located on your C: drive, and not your D: drive, then the Windows bootloader is located on C: and therefore formatting C: will make Windows XP unbootable. These files are system files and hidden, so you will need to disable the hidding of hidden system files. Alternatively, you could open a CMD window and cd to the root of your C: drive and do a:

dir /a

to show the directory contents including system and hidden files.

Thanks a lot. The Ubuntu Forums are just great, I got many stuff explained. =D>

---

