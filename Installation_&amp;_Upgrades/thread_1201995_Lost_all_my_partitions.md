---
title: "Lost all my partitions"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by black669 on 2009-07-01
Hello,

I'm verry new to linux and i messed up my partitions.
Here's what i did:
I installed Ubuntu 9.04 on my laptop on the following partitions:
   / - 10 GB
   swap - 1 GB
  i left 10 GB free space because i wanted to install windows there after that
  the rest of the hard drive - one big NTFS partition

When i tried to boot a win XP CD it gave an error - NTLDR missing, i tried a NTLDR fixer but didn't help. Next i used a partitionner from a live CD and i formatted the 10 GB that i previousley left free to a NTFS partition. The program told me to reboot and after that i boot with win XP CD that worked this time but when i tried to tell windows where to install it said it needs to write MBR and after that my system froze. Ofcourse nothing works since then. I'm now on ubuntu live from mai flash drive. I ran gparted but it only displays one big unallocated disk.
  Can u pls help me recover my lost partitions or at least salvage the data from the NTFS partition.

---

### Post by theozzlives on 2009-07-01
boot the Windows CD, choose recovery console... after your at the prompt type:
```
fixmbr
fixboot
```
Then start over but use that extra 10 GB for /home (you'll be glad later)

---

### Post by black669 on 2009-07-01
unfortunatelly that didn't help much. The fixboot workeed fine, but fixboot wasn't that lucky. Here's the output from fixboot : 
   FIXBOOT cannot find the system drive, or the drive specified is not valid.
I donno if it is of any help to u, but i tried to change drives in recovery console and i've noticed that i there are 3 drives : C, D and E.
 
    thx in advance :) 


(and about your suggestion of making that 10GB for /home...yea i'll definetly do that..but my laptop is from my job and my boss starts tu vommit in the second that anybody mention linux in his presence so i need windows too:) )

---

### Post by running_rabbit07 on 2009-07-01
Did you partition the whole drive with Ubuntu and make the NTFS partition come after the Ubuntu? Windows likes to be first on the hard drive.

Whilst in Ubuntu go into Synaptic Package Manager and install gparted.

After installed, open and take a screen shot (applications-accessories-take screenshot) and post it.

I can't tell ya much for fixing this but it may help the more knowledgeable people help ya.

I attached mine to show you kinda what it should look like. I didn't make a swap drive being I have 2gig RAM I doubted I really needed it.

Good luck.

P.S. Are you part of Union 669?

---

### Post by black669 on 2009-07-01
The NTFS partition was created while win XP was firstly installed on my laptop, before Ubuntu. 
   Thx for the help.

  P.S: No, i'm not a part of Union 669...i don't even know what is that.

---

### Post by running_rabbit07 on 2009-07-01
I wish I could be of help but I don't know much about partition problems, I've been lucky I guess.



669 is a Pipefitter's Union that does fire sprinkler systems and such.

---

### Post by raymondh on 2009-07-01
> **black669 said:**
> The NTFS partition was created while win XP was firstly installed on my laptop, before Ubuntu. 
   Thx for the help.

  P.S: No, i'm not a part of Union 669...i don't even know what is that.


Kindly ... access a terminal and type/post output of

```
sudo fdisk -l
```

(small L not number 1)

Also, how did you install Ubuntu?  Do you remember the choice you made when you got to the partitioning stage of the installer?

---

### Post by black669 on 2009-07-02
> Kindly ... access a terminal and type/post output of

 	Code:
 	sudo fdisk -l 
(small L not number 1)

Also, how did you install Ubuntu?  Do you remember the choice you made when you got to the partitioning stage of the installer?

   Hi, here's the output:

```
Warning: extra link pointer in partition table 5
omitting empty partition (8)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28012800

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1095     8788976   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            1095       12162    88896512    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            1129      185976  1484784710    8  AIX
Partition 3 does not end on cylinder boundary.
/dev/sda5            2551       12162    77202432    5  Extended
/dev/sda6   ?        1129      185976  1484784710    8  AIX
/dev/sda7            1216        2551    10717168    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 2020 MB, 2020605440 bytes
255 heads, 63 sectors/track, 245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001705a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         246     1973216    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(244, 254, 63) logical=(245, 167, 49)
```

   I choose custom installation and i set the partitions myself without deleting the NTFS partition; I'm pretty sure about that because i could access it after Ubuntu was successfully installed and all my data was there.:)

   Thank you!

---

### Post by ronaldprettyman on 2009-07-02
you put windows at the end and that makes bill angry. Windows likes to be in the first 1000 or something blocks or bytes I can't remember the exact just always put it first or it gets mad. And yells at you and calls..........

Reboot to the live disk and run gparted. Delete all the linux partitions. Move the windows partion to the begining of the drive.

Go get a cup of coffee...take a smoke... 
Ok should be done now. Put in your Windows XP disc. Reboot.

get to cmd console recovery dos thingy
```
c:\> fixboot
c:\>fixmbr
```
reboot, let windows do its disc scan.
Reboot into the Live cd and reinstall putting Windows First and Linux second on your drive. keep bill happy or he won't work.

---

### Post by black669 on 2009-07-02
> you put windows at the end and that makes bill angry. Windows likes to be in the first 1000 or something blocks or bytes I can't remember the exact just always put it first or it gets mad. And yells at you and calls..........

Reboot to the live disk and run gparted. Delete all the linux partitions. Move the windows partion to the begining of the drive.

Go get a cup of coffee...take a smoke... 
Ok should be done now. Put in your Windows XP disc. Reboot.

get to cmd console recovery dos thingy
 	Code:
 	c:\> fixboot
c:\>fixmbr 
reboot, let windows do its disc scan.
Reboot into the Live cd and reinstall putting Windows First and Linux second on your drive. keep bill happy or he won't work.

   But gparted can't see any of my partitions...only one big unpatitioned space, i posted the print screen above.

 		                   		  		  		 		 			 				__________________

---

### Post by ronaldprettyman on 2009-07-02
> **black669 said:**
> But gparted can't see any of my partitions...only one big unpatitioned space, i posted the print screen above.

 		                   		  		  		 		 			 				__________________

Sorry, well that print screen looks like all your data is gone. Time to start over. Hope you had backups.

---

### Post by black669 on 2009-07-02
Here what 
```
sudo fdisk -l
```
says
Warning: extra link pointer in partition table 5
omitting empty partition (8)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28012800

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1095     8788976   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            1095       12162    88896512    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            1129      185976  1484784710    8  AIX
Partition 3 does not end on cylinder boundary.
/dev/sda5            2551       12162    77202432    5  Extended
/dev/sda6   ?        1129      185976  1484784710    8  AIX
/dev/sda7            1216        2551    10717168    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 2020 MB, 2020605440 bytes
255 heads, 63 sectors/track, 245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001705a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         246     1973216    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(244, 254, 63) logical=(245, 167, 49)
doesen't that mean that i still have some partitions on my disk?

---

### Post by raymondh on 2009-07-02
> **black669 said:**
> Here what 
```
sudo fdisk -l
```
says
Warning: extra link pointer in partition table 5
omitting empty partition (8)

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28012800

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1095     8788976   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2            1095       12162    88896512    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda3            1129      185976  1484784710    8  AIX
Partition 3 does not end on cylinder boundary.
/dev/sda5            2551       12162    77202432    5  Extended
/dev/sda6   ?        1129      185976  1484784710    8  AIX
/dev/sda7            1216        2551    10717168    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 2020 MB, 2020605440 bytes
255 heads, 63 sectors/track, 245 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001705a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         246     1973216    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(244, 254, 63) logical=(245, 167, 49)
doesen't that mean that i still have some partitions on my disk?

From the fdisk output and re-reading your first thread :

Am assuming sdb is the live USB you are using.

I only see one partition in sda that windows can reside in. And it is small and making me doubt its' future useability ... but it's your decision.  That is sda7.

Missing NTLDR can be a result of many things.  To name a few:
- PC may be booting from a wrong source (i.e. CD drive, USB drive, etc instead of the internal HD).  Check your boot options and the BIOS.
- NTLDR, ntdetect or boot.ini files are corrupt, missing or misconfigured
- Fixboot (which writes a new boot sector) is corrupt or misconfigured
- Malfunctioning IDE cables, bad HD, or hardware problems.
- or, you have a misconfigured or corrupt XP install along with the MBR.

When you tried to re-install windows, where did you tell it to install?

We could try to troubleshoot this one at a time but _sometimes, sometimes it is better to cut losses and start all over again_.

You said (in an earlier post) you were able to access the NTSF partition. If so,  save those files elsewhere ....

**Do you want troubleshoot or re-do?**

If you decide to re-do, do you have the original XP install disc ... not recovery CD?

Note : gparted will only touch/work on partitions that are unmounted. How did you access gparted to post the screenshot?

Sorry to hear about the laptop being a work computer with a "throwing-up" boss.

Some refrence materials:

[http://support.microsoft.com/kb/320397](http://support.microsoft.com/kb/320397)
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

---

### Post by merlinus on 2009-07-02
What concerns me are the errors from sudo fdisk -l -- partitions not ending on cylinder boundaries and such.  This might lead to even worse scenarios in future.

So IMFFHO it seems best to back up important data and begin afresh.

@raymond -- it is ntfs (new technology file system).  Easy error to make, but I have now seen it in a number of your recent posts.  No insult intended....

---

### Post by raymondh on 2009-07-02
> **merlinus said:**
> What concerns me are the errors from sudo fdisk -l -- partitions not ending on cylinder boundaries and such.  This might lead to even worse scenarios in future.

So IMFFHO it seems best to back up important data and begin afresh.

@raymond -- it is ntfs (new technology file system).  Easy error to make, but I have now seen it in a number of your recent posts.  No insult intended....


LOL ... thanks Merlin ... lex-dyslic of me (or I try to type too fast and end up dyslexic) ... LOL.  Thanks :)

---

### Post by black669 on 2009-07-03
Srry guys for not writting till now, but i had lots of work at my job.
Meanwhile i used TestDisk and it partially solved my problem...it didn't fix my drive so i can mount it, but i could access all my data and copy it on another drive.

Thx allot for u're help!!!!

---

