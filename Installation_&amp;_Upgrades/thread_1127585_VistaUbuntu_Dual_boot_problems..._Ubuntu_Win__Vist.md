---
title: "Vista/Ubuntu Dual boot problems... Ubuntu Win / Vista FAIL"
date: 2009-04-16
forum: Installation &amp; Upgrades
---

### Post by EdgarAllen on 2009-04-16
Hello everyone!

I am having some dual boot issues, mainly on vista's end, but I figured you guys may be a bit more knowledgeable on the woes of dual booting.

I guess I'll start off with what I did.

I had an el cheap-o Dell special laptop with a 300gig hard drive. The partition layout was in its factory state. 
sda1 - fat16 40mb some DellUtil thing
sda2 - ntfs - 15 gig recovery partition
sda3 - ntfs - 285 gig vista partition

I removed hibernation files, disabled system restore, disabled and removed page files, defragged like a mad man, and then shrunk the sda3 partition by 40 gig. 

I loaded up an Ubuntu live cd and gparted. I deleted sda2, slid over the sda3 partition in the graph thingy, and installed Ubuntu 8.10 on the largest available free space, which was a now continuous 55gig unallocated space at the end of the disk. 

Install went fine and Ubuntu loads fine. I've been using it for a few days now. About an hour ago, I figured I should reboot into Vista and enable the page files and whatnot again before I forget and see if Vista still works. This is where the problems start. 

I selected Vista from the Grub menu and Vista started to load. It decided it wanted to do a check disk and some error check scan. I had left the room to get something to drink figuring that the scans were going to take a while and did not get to see the results. When I returned the computer was sitting at the Ubuntu login screen. I assume it rebooted and Grub defaulted back to Ubuntu. I rebooted to Vista, no checks this time, and made it to the Vista login screen. And this is where the goodness ends...

All my users show up to log into fine.
The keyboard layout had switched to US Qwuerty from my usual US DVORAK. (Trying to type in passwords was a pain in the ****) 
Also, the tablet pc on screen keyboard that usually appears during login wasn't there.

When I log into a user it goes into a "Preparing Desktop" loading screen. After a while it goes into an ugly classic windows themed screen and I get an endless loop of error dialogs complaining that an error occurred with my Dell wireless network card and it had to be closed. 

If I ignore the error dialog, I can ctrl+alt+del and get the task manager. There are only like 5 processes running(not explorer or things like that) and 80% of the services give a status of N/A.
If I start explorer using "New Task" it will start up a vista themed desktop and complain that it couldn't locate my profile and is using a temp one. When I try to run just about anything, it gives me a file not found error. 
I noticed that the drive letter also has changed to D:\ from the previously used C:\

So I busted out my vista cds and tried to do a repair but it found no errors. I also noticed that the repair software labeled the installed partition as the original C:\.

So that's basically where I am at now. I really really don't want to have reinstall vista and the gobs of software I use on it.

Has anyone had similar issues? Any ideas?

Sorry if it's a bit long and TMI. Thanks.

Cheers,
EdgarAllen

---

### Post by Pumalite on 2009-04-16
Boot your Ubuntu Live CD and; from the Terminal, post:
```
sudo fdisk -lu
```

---

### Post by ronparent on 2009-04-16
Are your system restore point still avaiable? That is probably your best bet for restoring Vista. Note that gparted (the ubuntu partitioner) has issues with Vista but the issues you have now do not appear to be related.

If all else fails, you might try posting in a windows forum.

---

### Post by EdgarAllen on 2009-04-16
> **Pumalite said:**
> Boot your Ubuntu Live CD and; from the Terminal, post:
```
sudo fdisk -lu
```

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8a092352

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2       522739035   625137344    51199155    5  Extended
/dev/sda3   *       80325   522739034   261329355    7  HPFS/NTFS
/dev/sda5       522739098   620864054    49062478+  83  Linux
/dev/sda6       620864118   625137344     2136613+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

[QUOTE=ronparent]Are your system restore point still avaiable? That is probably your best bet for restoring Vista. Note that gparted (the ubuntu partitioner) has issues with Vista but the issues you have now do not appear to be related.

If all else fails, you might try posting in a windows forum. [/QUOTE]
No I don't. I had disabled window restore because every time I tried to use it the thing never worked and I had to do a fresh install.


I think the problem is that during the shifting of partitions Vista decided to detect the boot drive letter as D and is still looking for all its system files on a non existent C. I've found a few mailing list posts that describe something similar and explain how to change it back through the windows registry. Only problem is that I can't get vista to run regedit. Does anyone know of a way to edit the registry from ubuntu? 

Thanks for the help.

Cheers,
EdgarAllen

---

### Post by ronparent on 2009-04-16
Astute observation. If Vista now is on a D: that would fowl-up registry references. Despite discussion it started on last mention, I would suggess getting hold of a 'Partition Magic' boot disk with the warning that Partition Magic doesn't work with Vista. The boot disk is a DOS based utility, and although it may not be usable for partitioning a Vista partition, it may be useful to redesignate a D: drive to C:. I can't think of any other remedies.

---

### Post by Pumalite on 2009-04-16
You problem is that you have vista now in a 'logical' partition (inside of extended sda2), Vista prefers a 'primary partition'.

---

### Post by ronparent on 2009-04-16
Yes, that too. Was it that way originally?

---

### Post by EdgarAllen on 2009-04-17
> **Pumalite said:**
> You problem is that you have vista now in a 'logical' partition (inside of extended sda2), Vista prefers a 'primary partition'.

The vista partition is not a logical partition. It's just listed after sda2, its sectors don't reside inside sda2s. I wouldn't be able to set it as boot if it was a logical partition. 


Sadly, it looks like I am going to have to reintall vista. 


Thanks for the help.

Cheers,
EdgarAllen

---

### Post by Will4 on 2009-04-17
I had the same problem and after re-formating my (sda2) partition to "primary"Vista installed OkyDockie.!! 

Thanks Pumalite!!!

---

### Post by lisati on 2009-04-17
An observation: The CHKDSK and restart is normal if you have resized a Windows partition....

A suggestion: be very careful about messing with recovery partitions. My Toshiba laptop came with three (!) partitions - a Vista recovery partition, a Vista partition, and another which seems only to have been needed as part of the Vista installation process. I didn't dare touch the recovery partition or the "extra" partition until I had made a backup of the recovery partition using the "create recovery disk" tool Toshiba had thoughtfully provided.

---

### Post by EdgarAllen on 2009-04-17
Finally got it sorted. The biggest thing was finding a boot cd with a reg editor that would load vista's hive files. Most seemed to not be compatible and would cry when I tried to load them.

Once in the registry editor:
```

Select the HKEY_USERS hive.

From the File menu, choose the Load Hive option. Browse to C:\Windows\System32\Config\ and select the SOFTWARE hive.

Randomly pick a name for the hive that you've loaded now. 

Navigate to the HKEY_USERS\Randomly picked name\SYSTEM\MountedDevices key.

Find the drive letter you want changed. Look for "\DosDevices\D:" and rename it to the correct one.

Select the Randomly Picked name from the tree navigator.

From the File menu, choose the UnLoad Hive.

Reboot.

```

For some reason, I had a bunch of duplicate and redundant keys, which I guess were left over from the partition I had deleted. I just deleted them. I wouldn't recommend deleting keys like that unless you are sure of what you are deleting and have a backup saved.

After that, every thing started to load normal again. :D


Thanks for the help every one.

Cheers,
EdgarAllen

---

