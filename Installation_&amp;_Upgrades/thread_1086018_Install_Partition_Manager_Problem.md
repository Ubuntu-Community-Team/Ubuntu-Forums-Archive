---
title: "Install Partition Manager Problem"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by DouglasWiley on 2009-03-03
When I attempt to install Ubuntu, on the 4th step I see "Prepare Partition" as the title, an empty box, and greyed out buttons related to managing the partition. If any additional information is needed, I'll be happy to give the info to you. I know this is somewhat vague, as I am not sure what details to post.

Thanks for your help,

Douglas

EDIT: Installed from a DVD (burned .iso) to it's own partition. I simply shrunk the main volume and left the hard drive space unpartitioned. It is the 64-bit version of Ubuntu

---

### Post by avtolle on 2009-03-03
How are you trying to install Ubuntu? From an iso to its own partition on the HDD or using a Wubi install "inside of windows"?

---

### Post by DouglasWiley on 2009-03-03
From a DVD (burned .iso) to it's own partition. I simply shrunk the main volume and left the hard drive space unpartitioned.

---

### Post by avtolle on 2009-03-03
> **DouglasWiley said:**
> From a DVD (burned .iso) to it's own partition. I simply shrunk the main volume and left the hard drive space unpartitioned.
Trying to figure this out; it appears from your initial post that the HDD is mounted in some way, or the partitioner isn't seeing the drive. Did you defrag the drive before shrinking it (I'm presuming Windows in some form as the existing os on your computer)?

EDIT: Another thought; did you run a "Live Session" and then elect to install from it? There is something in the release notes to 8.10 which indicates that in certain situations, when that is done, the HDD is mounted, and stays that way. One way around this is to back out of the installer, and then shutdown; reboot from (in your case) the DVD, and select install from the initial menu.

---

### Post by DouglasWiley on 2009-03-03
I have vista installed as the main OS. I have defragged the drive once with Auslogics Disk Defrag. I did not defrag before shrinking the partition.

---

### Post by avtolle on 2009-03-03
[http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode](http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode) is what I was blathering about *supra*.

---

### Post by DouglasWiley on 2009-03-03
> **avtolle said:**
> [http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode](http://www.ubuntu.com/getubuntu/releasenotes/810#Hard%20disks%20potentially%20not%20shown%20when%20installing%20in%20Live%20CD%20mode) is what I was blathering about *supra*.

Ok, so what do I do? I'm a little bit confused here. I have ran it straight from the Install Ubuntu option form the initial menu, not while running a Live Session

---

### Post by avtolle on 2009-03-03
Sorry for any confusion. From my reading of your initial post, it was not clear to me whether you were seeing the partitions, but couldn't take any action; or whether the partitioner wasn't "seeing" the HDD at all. Re-reading, it seemed to me that the partitioner wasn't seeing the HDD at all, thus the edit. What the link states to do is to unmount the drive; presuming that the HDD in question is the only one in your system, quitting the installer, exiting the Live session, and rebooting the computer from the DVD, then selecting install from the opening menu seemed the best way to get you going again.

---

### Post by DouglasWiley on 2009-03-03
So, what now? We know it's not detecting my HDD, so could this possibly be an undocumented bug? I have tried installion from a live session, directly installing it from the opening menu several times :/

---

### Post by avtolle on 2009-03-03
Just so I'm clear; you have, prior to installation, shrunk your Vista partition to make room; you left the additional room unallocated; prior to shrinking, you did not defrag the HDD; you have successfully booted from the Live CD, but when you get to step 4 in the installation process, the partitioner doesn't see the HDD, whether selecting "install" from the desktop or directly from the initial menu. If anything about the above is not correct, please let me know what that is.

I'll be back in a bit; hopefully, there will be others who will see this and offer assistance in my absence.

---

### Post by avtolle on 2009-03-03
BTW, you are trying to install 8.10 and not 8.04, correct?

---

### Post by avtolle on 2009-03-03
I'm not coming up with anything that is evenly remotely helpful. One final comment: the partition table is coming up blank, and the Vista partition isn't being shown at all. 

And one more question: what kind of drive is it (SATA or IDE)?

---

### Post by DouglasWiley on 2009-03-03
> **avtolle said:**
> I'm not coming up with anything that is evenly remotely helpful. One final comment: the partition table is coming up blank, and the Vista partition isn't being shown at all. 

And one more question: what kind of drive is it (SATA or IDE)?

8.10 Ubuntu 64-bit. All of the information is correct. SATA

---

### Post by ahbart on 2009-03-04
Sorry for breaking in here. But I have the same problem. 
I'm trying to install U8.10 64 bit. Two HDD (SATA), with different partitions. The partitioning screen in the installer is totally blank.
I'll try to start the install from the first menu instead of the installer from the live session. 
Would unmounting the volumes and then starting the installer not work?

---

### Post by avtolle on 2009-03-04
@DouglasWiley; thank you for the additional information. As you have a SATA HDD, please read [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) as to how to use boot options, and then try this one, which is not mentioned in the link: all_generic_ide, to be placed on the boot line as instructed in the link. There were problems with SATA drives under 8.04, which I thought had been taken care of for the most part in 8.10, and the above boot option helped some folks install.

@ahbart, yes, unmounting the volumes and then starting the installer might work. However, if you are getting a blank partition table as was the OP, your drives aren't being detected at all, as nearly as I can tell.

---

### Post by avtolle on 2009-03-04
To both: see [http://ubuntuforums.org/showthread.php?t=1086971](http://ubuntuforums.org/showthread.php?t=1086971) and look at the suggestion to turn on AHCPI (?) in the bios; taurus is very knowledgeable, and this may be an answer to the problems of one or both of you.

---

### Post by ponchojuan on 2009-03-26
This is definitely something with the partitioner.  I am having the same problem; the partitioner is not recognizing any disk.  Interestingly the partitioner utility sees the disks and partitions just fine.  The installer must be looking in a different place, like the original CD or USB drive.  Are there any config files for the installer.  My hunch is remounting the drive for the installer could do it.  One clue is the error message from the partitioner about not recognizing the root directory.

Any help is appreciated.  I don't have a bootable CD so I don't want to backtrack if possible.

---

### Post by Mark Phelps on 2009-03-28
> **ponchojuan said:**
> 
Any help is appreciated.  I don't have a bootable CD so I don't want to backtrack if possible.

Then basically, don't mess with it! Seriously... Shrinking a Vista installation with anything other than the Vista disk management utility is running the risk of corrupting the Vista OS.  With a Vista DVD, repairing this is a 5-minute operation of booting with the DVD and running Startup Repair.

Without the Vista DVD, repair is simply not possible.

And before the legion of GParted fans jumps in here and flames me, check the Notes with version 0.3.4 and notice that their own notes say that shrinking a Vista volume does not YET work! Yeah, I was surprised to read that, too.

You can go to the Neosoft forums and use torrents to download an Vista recovery CD that WILL allow you to do Startup Repair.

Would suggest doing that before you start messing with the Vista volume.

---

