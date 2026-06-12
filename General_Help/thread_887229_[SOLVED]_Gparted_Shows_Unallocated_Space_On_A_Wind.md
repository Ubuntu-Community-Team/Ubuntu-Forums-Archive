---
title: "[SOLVED] Gparted Shows Unallocated Space On A Windows Drive!"
date: 2008-08-11
forum: General Help
---

### Post by dhughes on 2008-08-11
This is freaking me out.

 I have a 100GB drive, my plan was to dual boot Windows XP and either Kubuntu or Ubuntu and give it to my Aunt, I think she will like Linux. So I installed Windows and then realized I probably should have partitioned the drive first. After the Windows install I defragmented Windows, rebooted to a Xubuntu LiveCD (it was close by...no reason other than that) to use Gparted and divided the drive equally.

 I had some trouble since I wanted to make the 50GB Linux half into a 30GB /home partition, an 18GB / (root) and a 2GB Swap. The partitioning got a bit confusing since I was trying to make a Swap in a Primary partition, or that's my guess but whatever I doing was wrong I couldn't seem to be able to put Swap anywhere without getting an error.

 So at the end of it I just deleted any Linux partitions to the Linux half and left it as nothing, no Primary, no partition just unallocated. I rebooted into Xubuntu and got that sick feeling from what I saw...the entire drive was "unallocated"! Hours setting up Windows (mostly ATI drivers fault!) drivers, reboot, drivers, reboot, updates, reboot etc. and it was gone, worse was the stupid Activation since I had to call them on the phone since a web activation failed.

 Just for fun I rebooted to see what would happen and Windows starts! It had to go through a disk check but it started fine and even after a few reboots. BUT rebooting into Xubuntu still shows the entire drive as unallocated space...empty, no partitions, no data at all. Now I'm really stuck!

 Has anyone ever seen this?

---

### Post by unutbu on 2008-08-11
Your problem reminds me of this thread:
[http://ubuntuforums.org/showthread.php?t=857564](http://ubuntuforums.org/showthread.php?t=857564)
The solution ([http://ubuntuforums.org/showpost.php?p=5551635&postcount=11](http://ubuntuforums.org/showpost.php?p=5551635&postcount=11)) was to use testdisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk))
to repair the partition table.

---

### Post by sandysandy on 2008-08-11
post output of [COLOR="Red"][SIZE="4"]sudo fdisk -lu[/SIZE][/COLOR]

regards

---

### Post by dhughes on 2008-08-11
> **unutbu said:**
> Your problem reminds me of this thread:
[http://ubuntuforums.org/showthread.php?t=857564](http://ubuntuforums.org/showthread.php?t=857564)
The solution ([http://ubuntuforums.org/showpost.php?p=5551635&postcount=11](http://ubuntuforums.org/showpost.php?p=5551635&postcount=11)) was to use testdisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk))
to repair the partition table.

Thanks for the info, it makes sense, from what I can tell reading those links I pretty much caused the partitions to get messed up while trying to make so many partitions and failing, the boundary between them is not right.

 I'll try a different LiveCD with the TestDisk added feature.

 Stay tuned...!

---

### Post by dhughes on 2008-08-12
> **sandysandy said:**
> post output of [COLOR="Red"][SIZE="4"]sudo fdisk -lu[/SIZE][/COLOR]

regards

 Too late, I guess we posted at the same time. 


 Anyway I downloaded Gparted, again, the newest version and used TestDisk from the Terminal and muddled my way through it to make the Primary show as bootable and deleted the other two Linux partitions.

 At first I don't know what I did but the Windows NTFS and one of the Linux partitions were still unallocated but one of the Linux partitions was showing as ext3 and it existed.

 After making the original Primary (Windows) partition bootable (even though Windows did boot fine) and deleting the other two Linux partitions, after a reboot it came up as just that one NTFS partition and the other half is unallocated, which is what I want.

---

### Post by dhughes on 2008-08-13
Well, sort of solved...the partitions were visible instead of one big blob of 'unallocated' space, or at least one partition was but Windows was not able to be booted, only Ubuntu was. 

 I tried to reinstall Grub, tried the SuperGrub LiveCD, before all that I tried to undo anything I changed - all I did was change the stanza titles - I even tried wiping Linux and using Linux application ms-sys (available in Universe) to fix the Windows MBR but no go.

 Now in the process of starting over the install of Windows and Linux only this time a bit more careful. 

 It's too bad though because the "starting up" hang problem is quite common going by how many posts there are not just here but on many other Linux forums.

---

