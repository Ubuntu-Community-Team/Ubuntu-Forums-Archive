---
title: "Ubuntu killed my new lappy"
date: 2009-01-29
forum: Hardware
---

### Post by troegs on 2009-01-29
Okay. So maybe killed is a harsh word but I was hoping to get some knowledgeable eyes on my post ASAP. 

I got a new Asus G50VT-X1 delivered to me today. As soon as I got rid of the bloatware that comes standard with it my first goal was to get the HD split in two and load up Ubuntu on it 8.10 64 bit.

The first problem I ran into was the issue of the HD being in enhanced mode vs compatibility mode. I've since remedied that issue but since the install part where I ran into the issue is AFTER the partitioning phase of the install, it already partitioned my HD. Now when trying the install again I had to partition the partition, the install got further but still failed. I checked my DVD and it's not flawed so I'm hoping someone can help before I slice and dice my HD into a million unusable pieces trying to get this OS to work.

I've searched the forums but so far to no avail. I'm a new Linux user but am determined to switch as I've completely had it with windows. I'm a CS major at university so the Linux switch, to me, is a natural part of learning more about computers and having the realization of the built in problems with windows sink in.

If someone can please help I'd greatly appreciate because as things are now I'm already having problems getting the comp to boot into windows after these two failed attempts at getting ubuntu installed. If I end up with a $1,000 paperweight there's a good chance you'll be seeing me on the news in a bell tower. 

Any knowledgeable Linux/Ubuntu Gurus out there that don't mind doing a little hand holding with a fairly computer savvy individual would/will be GREATLY appreciated.

Thank you in advance.

T.

P.S. Please save any "query google" or "search the forums" replies really aren't much help. I've done both and am now here because I haven't found what I'm looking for. Remember you too were a Ubuntu noob yourself at one point.

P.P.S. If anyone out there can tell me whether or not I'll be able to merge all these sliver sized partitions together so they'll be usable once I get this going I'd appreciate that. Also if you could point me in the right direction of learning how to do this would be a great help. (or you could just spell it out barney style for me if you've got the time)

---

### Post by ByteJuggler on 2009-01-29
What exactly happens/Where do you run into trouble?  You've not given any specifics, without which it's quite hard to diagnose and suggest a course of action.  

But, suffice it to say you can probably relatively easily fix your partition table/get rid of any redundant ones.  

Questions:
1.) Does the LiveCD work?
2.) What hardware's in your laptop?  (Gfx? CPU? RAM?)
3.) What version of Windows do you have?  XP? Vista?
4.) Please post the output of the following command (which you can copy/paste into a terminal when running the LiveCD (assuming it works):
```
fdisk -lu >/tmp/fdisk.txt; gedit /tmp/fdisk.txt
```
Copy the output which should be in a text editor into a post here (and remmber to click the # to put it inside "code" tags so it's properly quoted/formatted.

---

### Post by troegs on 2009-01-29
Here's the pertinent specs:

Processor: Intel® Core™2 Duo Mobile

Processor Speed: 2.26GHz

System Bus: 1066MHz

Cache Memory: 2MB on die Level 2

System Memory (RAM) 4GB

Type of Memory (RAM): PC2-5300 DDR2 SDRAM

Hard Drive Type: Serial ATA (5400 rpm)

Hard Drive Size: 320GB

Optical Drive: Double-layer DVD±RW/CD-RW

Graphics
NVIDIA GeForce: 9800M GS

Video Memory: 512MB


The system is currently running vista home premium 64 bit with SP1

When I try to run the fdisk command I get the following error message:
Cannot open /dev/dsa

---

### Post by troegs on 2009-01-29
cancel that. I DID get a return for the command after I used "sudo" before it. here is the return


Disk /dev/sda: 320.0 GB, 320072933376 bytes
4 heads, 44 sectors/track, 3551945 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    22523129    11261533+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    22523130   335083769   156280320    7  HPFS/NTFS
/dev/sda3       335083936   625142319   145029192    f  W95 Ext'd (LBA)
/dev/sda5       335083980   341375583     3145802    7  HPFS/NTFS
/dev/sda6       341375628   346033599     2328986   83  Linux
/dev/sda7       613533756   625142319     5804282   82  Linux swap / Solaris
/dev/sda8       346033644   602584399   128275378   83  Linux
/dev/sda9       602584444   613533711     5474634   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by troegs on 2009-01-29
I will name my firstborn after anyone that can help with this. I'm desperate.

---

### Post by caljohnsmith on 2009-01-29
You say when you get to the partition part of the installation that the install failed--so what errors do you get? Or what exactly happens? Please give as much detail about that so maybe we can help you.

---

### Post by troegs on 2009-01-29
The first time the install failed immediately following the partition part of the install the screen went black and I got an error that repeated over and over and over. I can't recall exactly what the error message was but it said something to the effect of

[13570.092000] VFS: busy inodes on changed media.
[13570.280000] VFS: busy inodes on changed media.
[13570.680000] VFS: busy inodes on changed media.
[13570.840000] VFS: busy inodes on changed media.
[13571.000000] VFS: busy inodes on changed media.

I researched this error and found that it had to do with the HD being set to enhanced mode. After switching to compatibility mode I didn't get this error again. 

The next attempt at installing I had to go through the partition part again, (this is where I start getting all the partitions. I believe I'm up to 6 now). This time around the install starts but quit at around 27%. The message said that it could be due to a bad disk, however I've checked the disk through the option that comes up when you run the live CD as well as the MD5Sum check. 

I've since then created a new disk, (the original one was put onto a dvd, the new one is on a cd). I'm not against trying again with the new cd but I AM against slicing my HD into a million little pieces. Especially if I can't easily merge them back together once I get things up and running. 

I hope this helps you help me! Thanks again in advance for any help anyone might offer.

Troegs

---

### Post by IQRules on 2009-01-29
Can you boot to Windows? If so delete the extended partition, as free space.
Shutdown, and use Ubuntu 8.10 CD, reload OS, and choose to use ALL free space.

The easiest way, could be wipe everything out. You have Windows OS DVD, right?

---

### Post by caljohnsmith on 2009-01-29
Troegs, how about trying to install again but with your new CD, and also before you start the installation, first try the "check CD for defects" type option at the main menu just to make sure the CD is OK. If it is, once you boot to the Ubuntu desktop, how about opening gparted (System > Admin > Partition Editor), and using that, delete partitions sda6 through sda9. Then quit, run the Ubuntu installer, and choose the "guided using free space" type option when it comes to the partition stage. Try that, and let me know exactly what happens, especially any errors you might get.

---

### Post by troegs on 2009-01-29
> **IQRules said:**
> Can you boot to Windows? If so delete the extended partition, as free space.
Shutdown, and use Ubuntu 8.10 CD, reload OS, and choose to use ALL free space.

The easiest way, could be wipe everything out. You have Windows OS DVD, right?

I actually don't have a full OS DVD. All I got was a recovery CD.

Between this post and my last I contacted one of my professors who is a Linux/Ubuntu guru. He said that I should just bring in the comp first thing tomorrow morning at 7am so I think that's just what I'll do. 

I appreciate all the help but after talking to him, and being to give him more clear/better details of what's going on he thought it best I stop tinkering around else I have a solid shot at screwing up my windows partition as well. 

Thanks again for the help though all. I'll post back and let you know what exactly was the problem, and how everything went. I'll also make a thread on my specific comp as in my searching I saw a lot of people asking the same questions as me without any definitive answers.

Troegs

---

### Post by IQRules on 2009-01-29
I did use OpenSuse other versions. It looks to me the 8.10 partition tool is troublesome sometimes. 

Can the 8.10 LiveCD work / boot it right up? That proofs your laptop still good.

---

### Post by ByteJuggler on 2009-01-30
> **troegs said:**
> 
The next attempt at installing I had to go through the partition part again, (this is where I start getting all the partitions. I believe I'm up to 6 now). This time around the install starts but quit at around 27%. The message said that it could be due to a bad disk, however I've checked the disk through the option that comes up when you run the live CD as well as the MD5Sum check. 

OK, if you've got partitions from a prior install then you should either go into the "Partition editor" first, and delete the previous partitions from your disk before starting the installer, or you have to, from the installer, pick the "manual partitioning" option and re-use or manually create the partitions you want.  That's all.

As for the error messages you're getting, you need to post the exact messages you're seeing.  In your case for example it's not clear whether the message is in fact relating to the CD or the hard disk.  It's unlikely, but not impossible that your new laptop has problems somewhere on its surface that hasn't shown up on Windows due to Window's location on the disk (close to the beginning) and might now be showing under Ubuntu (due to it being placed closer to the end of the disk, depending on how much space you're allocating to Ubuntu.)

PS Yeah I forgot the "sudo", my apologies!

---

### Post by ByteJuggler on 2009-01-30
> **troegs said:**
> I appreciate all the help but after talking to him, and being to give him more clear/better details of what's going on he thought it best I stop tinkering around else I have a solid shot at screwing up my windows partition as well. 

OK no worries.  We'll be here if you have further questions... :p  (Always easier to have someone knowledgeable have a look at things in person!)

---

