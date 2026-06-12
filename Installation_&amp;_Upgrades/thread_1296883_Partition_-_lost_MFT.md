---
title: "Partition - lost MFT"
date: 2009-10-21
forum: Installation &amp; Upgrades
---

### Post by birchyboy on 2009-10-21
I have been multi-booting Windows, SUSE and Fedora for some years, but with the Linux distros on a separate drive. I have now removed the Linux drive and put all my windows material on a new 1Tb Hitachi, with a OCZ Vertex SSD to hold the OS and all the programs on the Hitachi (4 partitions). Some, but not all, the data is backed up.
 
I thought I would like to try the latest Unbuntu, so I used the installer on a Linux magazine DVD. I placed the installer on the Hitachi and all seemed to go well, until the reboot, when I got a message which advised me there was no suitable partition available for some function (I forget the actual message). However, I could not close the warning either by clicking OK, the X, CTRL+Z, CTRL+ALT+Del or any other means. 
 
On the reboot, Win7 and Ubuntu appeared on the bootloader, so I selected Ubuntu and got only the cursor. 
 
I selected Win7 on the next reboot and it loaded, but there was no Hitachi drive in file manager. 
 
My Paragon Disk Manager reports just under 1Gb of 'unallocated' space, but can't apply any changes to it. CHKDSK /F finds no problems. Win7 repair mode finds no problems. 
 
Needless to say, I am not very happy with Ubuntu at the moment, although I have no way to tell if the same would have happened with a SuSE installation. 
 
"Recover My Files" tells me that the MFT is corrupt (presumably the copy is also corrupt) and finds many of the files, but there are a lot listed as 'fragments', presumably bits of whole files without the MFT to identify the original. Since they are all listed as Filexxxxx I would have to go through the lot and attempt to find they type and then contents. However, RMF costs $70 (about twice the cost of the Hitachi at £45). 
 
I am reasonably familiar with MBR operations, but not with MFT. I know MFT restoration is notoriously unreliable, but does anybody know a way to recover the situation, other than the expensive one?

---

### Post by Mark Phelps on 2009-10-21
From personal experience, using all of the different MS Windows file recovery tools, I've found the GetDataBack series, of which RMF is a member, to be far and above the BEST.  I've had numerous situations in which other utilies would find nothing or very little, while these products found everything.

So, if RMF is saying your MFT is corrupt, I would believe it.

Unfortunately, you're stuck with all the bogus filenames because, when an MFT gets corrupted, the filename entries get corrupted as well.

There are threads in these forums about using PhotoRec and Testdisk in Ubuntu to recover data, and while I've never had any success with either, others have.  So, that approach might work if you don't want to spend the money for RMF.

Also, every time you write to a drive with a corrupted MFT, you worsen the problem; so, if you really want to recover the files, you would do best removing the affected drives and setting them aside.

---

### Post by birchyboy on 2009-10-22
Mark
 
Many thanks for your reply and suggestions.
 
I had pretty much resigned myself to losing the data, although nothing has been written to the disk, since it's still Unallocated space. 
 
Fortunately, all the work is on a USB stick and updated with Synctoy 2.0. All my favourite music and my address book are also on my phone. What I will have lost is old documents, images and other bits like themes for phones, etc. 
 
The real pain is going to be putting all the software back on.  Because the SSD is only 60 Gb, all the programs were on the 1Tb disk.  My only consolation is that I have a working desktop in 40 sec and a complete reboot takes 63 sec. 
 
Thanks again for your time.

---

### Post by Mark Phelps on 2009-10-22
Was it the filesystem on the SSD that had the corrupted MFT?  If so, suggest you do some forum searches on SSD because I remember that there were some posts about data corruption and SSDs that advised folks to disable some functions.

Sorry, can't afford an SSD, so I don't have any of the details.

---

### Post by birchyboy on 2009-10-23
Mark
 
No, the SSD still runs fine and fast (Win7 RC). My SSD has all the alterations advised by the experts (disabling prefetch, indexing, etc.). 
 
The problem may have been that the installer was not on the boot drive. I just installed Fedora 11, with the installer on my 4Gb USB stick and the whole system boots from the stick, with what appears to be a Flash-specific file. 
 
I'm not a Linux specialist, although I have played with many of the distro's over the years, so this is quite a setback in my appreciation of it.

---

