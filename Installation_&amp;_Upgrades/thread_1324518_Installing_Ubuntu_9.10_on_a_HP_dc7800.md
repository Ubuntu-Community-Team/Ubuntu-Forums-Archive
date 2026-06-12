---
title: "Installing Ubuntu 9.10 on a HP dc7800"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by chococharlie on 2009-11-12
Hi guys,

I am trying to install Ubuntu 9.10 and I am running into a problem during install.

So basically I booted my PC using the Ubuntu CD, I'm in the GUI. On the desktop there's an icon called **Install Ubuntu 9.10**, I double-click that and an Install windows pops. Here's a step by step:

1. Choose English, click Forward
2. Choose Region and Zone, click Forward
3. Keep default Keyboard layout, click Forward
4. Now here's the problem, am at **Prepare partition** section of the install but the device list is blank/empty.. nothing's there. If I click Forward I get *No root file system is defined.*

My guess is that Ubuntu doesn't detect my HDD.. Is that possible? I was kinda expecting problems with the sound or webcam drivers, but HDD?? :o

I booted the PC with the latest SystemRescueCD 1.3.2 and I can see my HDD with GParted, I can even partion it with NTFS or EXT3 (However format only works with NTFS, if I tried to format EXT3/4 partions it complains that the HDD is already in use - messed up)

Any help/suggestion are appreciated,
Many thanks.
Choco

---

### Post by chococharlie on 2009-11-12
anyone?

---

### Post by audiomick on 2009-11-12
Can't help much but:
Boot into the live CD, see if it finds your disc. Start Gparted from the system admin menu, see what that says.
This will tell you if Ubuntu as such has a problem, or just the installer.
also, I saw a thread dealing with this subject this afternoon in this part of the forum. Go look for it, it can't be too buried yet...

---

### Post by chococharlie on 2009-11-13
I downloaded and booted with GParted LiveCD, it doesn't report any problems at all and actually I was able to repartition my HDD and format it with any file system (included ext3)

I even chose **create partition table** which wipes the previous partition table with a fresh one, nothing helps, the Ubuntu installer still doesn't recognize my HDD.

---

### Post by dhavalbbhatt on 2009-11-13
Try using the "Alternate" installation CD to install Ubuntu as against the Desktop installation CD that you are using right now. There is only one material difference between the two - the Desktop installation CD has a GUI interface, while the alternate installation CD is more CLI (but don't fret, it still is just typing in a few things, no more). The "under the hood" difference is that the alternate installation CD uses a different partition manager than the desktop installation CD, which seems not be working in desktop installation CD for 9.10 (for all other versions, this is not an issue). If the partition manager is indeed the issue here, then the alternate CD will resolve it.

---

### Post by audiomick on 2009-11-13
Hallo.
@ dhavalbbhatt: thanks for the tip. That may just help me out with another weird problem I had recently.

@ charlie: he's right; the alternate CD's are a piece of cake. I've used one a number of times to install Ubuntu Studio. I find them even a little more relaxed than the live cd, because they don't try and guess what you want, but rather just sit there and wait for your input. This means you have plenty of time to toss coins if you're not sure about what you're doing...;)
Michael

---

### Post by chococharlie on 2009-11-13
I downloaded the latest Alternate Ubuntu installer: **ubuntu-9.10-alternate-i386.iso**

It boots alright, it gets to a point where it says:

```
[!] Detect disks
One or more drives containing Serial ATA RAID configuration have been found.
Do you wish to activate these RAID devices?

Activate Serial ATA DAID devices?
<Yes>  <No>
```So I chose **Yes**

The next screen says:

```
[!!] Partition disks
This is an overview of your currently configured partitions and mount
points. Select a partition to modify its settings (file system, mount
point, etc.), a free space to create partitions, or a device to
initialise its partition table.

<BLANK>

Undo changes to partitions
Finish partitioning and write changes to disk
```If I chose **Finish partitioning and write changes to disk**, I get this:

```
[!!] Partition disks
No root file system
No root file system is defined.
Please correct this from the partitioning menu.
<Continue>
```Any suggestions at this point are appreacited.

---

### Post by dhavalbbhatt on 2009-11-13
> **audiomick said:**
> Hallo.
@ dhavalbbhatt: thanks for the tip. That may just help me out with another weird problem I had recently.


you're welcome - always happy to help!

---

### Post by dhavalbbhatt on 2009-11-13
> **chococharlie said:**
> I downloaded the latest Alternate Ubuntu installer: **ubuntu-9.10-alternate-i386.iso**

It boots alright, it gets to a point where it says:

```
[!] Detect disks
One or more drives containing Serial ATA RAID configuration have been found.
Do you with to activate these RAID devices?

Activate Serial ATA DAID devices?
<Yes>  <No>
```So I chose **Yes**

The next screen says:

```
[!!] Partition disks
This is an overview of your currently configured partitions and mount
points. Select a partition to modify its settings (file system, mount
point, etc.), a free space to create partitions, or a device to
initialise its partition table.

<BLANK>

Undo changes to partitions
Finish partitioning and write changes to disk
```If I chose **Finish partitioning and write changes to disk**, I get this:

```
[!!] Partition disks
No root file system
No root file system is defined.
Please correct this from the partitioning menu.
<Continue>
```Any suggestions at this point are appreacited.

Is this after you have installed the system? Or during installation? If it is during installation, then I am guessing you have not selected a partion for the root - the fix for that should be simple. On the partition that you want to be the root partition, mount the partition as "/" and you will be good.

---

### Post by audiomick on 2009-11-13
Hey Charlie,
Why is it finding a RAID disc?
I am not an expert on that subject, but as far as I know, RAID  stuff always involves more than one disc. You have only written about your HDD in the singular, and that picture of your computer that I found in the net doesn't look like one that would have more than one disc in it.

---

### Post by chococharlie on 2009-11-13
I'm not sure you understand the problem.
[B]
This is an example of what the screen should look like:[/B]

```
  +------------------------+ [!!] Partition disks +-------------------------+   
  |                                                                         |   
  | This is an overview of your currently configured partitions and mount   |   
  | points. Select a partition to modify its settings (file system, mount   |   
  | point, etc.), a free space to create partitions, or a device to         |   
  | initialise its partition table.                                         |   
  |                                                                         |   
  |        SCSI1 (0,0,0) (sda) - 73.4 GB FUJITSU MAY2073RCSUN72G            |   
  |        >      #1  31.5 GB                                               |   
  |        >      #2   8.6 GB                                               |   
  |        >      #4  99.0 MB B K ext3       /boot                          |   
  |        >      #5  31.8 GB   F xfs        /                              |   
  |        >      #6   1.4 GB   F swap       swap                           |
  |        SCSI1 (1,1,0) (sdb) - 73.4 GB FUJITSU MAY2073RCSUN72G            |
  |                                                                         |
  |        Undo changes to partitions                                       |
  |        Finish partitioning and write changes to disk                    |
  |                                                                         |
  |     <Go Back>                                                           |
  |                                                                         |
  +-------------------------------------------------------------------------+
```
**And this is what mine looks like during installation:**

```
  +------------------------+ [!!] Partition disks +-------------------------+   
  |                                                                         |   
  | This is an overview of your currently configured partitions and mount   |   
  | points. Select a partition to modify its settings (file system, mount   |   
  | point, etc.), a free space to create partitions, or a device to         |   
  | initialise its partition table.                                         |   
  |                                                                         |   
  |                                                                         |
  |        Undo changes to partitions                                       |
  |        Finish partitioning and write changes to disk                    |
  |                                                                         |
  |     <Go Back>                                                           |
  |                                                                         |
  +-------------------------------------------------------------------------+
```

---

### Post by chococharlie on 2009-11-13
> **audiomick said:**
> Hey Charlie,
Why is it finding a RAID disc?
I am not an expert on that subject, but as far as I know, RAID  stuff always involves more than one disc. You have only written about your HDD in the singular, and that picture of your computer that I found in the net doesn't look like one that would have more than one disc in it.

Hi there,
No RAID in my system, just one SATA HDD.. Why Ubuntu detects a RAID is beyond my understanding. (And probably part of the problem)

---

### Post by audiomick on 2009-11-13
Hi. The mystery deepens...
I've just read over the thread again, it seems that other things can find the disc, just not the installer.

I would have tried booting into Ubuntu from the live CD by now. Did you? and did it run?

In the Alternate installer, given the results up to now, I would run it again and tell it not to activate the RAID disc it is claiming to have found. That might make it have another look...

---

### Post by chococharlie on 2009-11-13
Hi guys,

Here's something interesting.

I tried installing the latest Debian (debian-503-i386-netinst.iso)

What's interesting is that the setup options/order are/is exactly the same like the Ubuntu alternate installer, same questions with the same options..

One big difference, it actually detected my HDD and partitioned it succesfully...

**The Debian installation was completed successfully!**

What I will do next is try to install Ubuntu and see if it detect the HDD this time (since the partition table was "fixed" by Debian)

---

### Post by audiomick on 2009-11-13
Glad you're having some success!
It is no surprise that Debian stuff is so similar to Ubuntu; Debian is the Linux that Ubuntu is based on.

Edit: Just found this in another thread. 
> The Karmic installer apparently has no problems seeing raided SATA drives but apparently does have trouble sometimes recognizing multiple SATA drives as individual volumes (especially if they have been previously used in raid arrays).

Had your drive been in another computer?

---

### Post by chococharlie on 2009-11-13
> **audiomick said:**
> Hi. The mystery deepens...
I've just read over the thread again, it seems that other things can find the disc, just not the installer.

I would have tried booting into Ubuntu from the live CD by now. Did you? and did it run?

In the Alternate installer, given the results up to now, I would run it again and tell it not to activate the RAID disc it is claiming to have found. That might make it have another look...

OK, not activating the disk led to a positive outcome, it detected my HDD and I was able to setup partitions.. it actually installed succesfully (and I bet pre-installing Debian wasn't necessary)

Thanks for you help guys ;)

Edit:
[quote=audiomick]Had your drive been in another computer?[/quote]

Nope.

---

### Post by dhavalbbhatt on 2009-11-13
Consider marking this thread as "Solved" so that other people can use it to resolve similar issues.

Glad you were able to finally get everything to work.

---

