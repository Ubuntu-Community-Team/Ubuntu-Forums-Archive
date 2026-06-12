---
title: "Create Partitions page blank on 9.10 install"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by Takara Pearl on 2009-10-30
I'm trying to install 9.10 on my computer. It will be running with Windows 7.  Windows 7 will be 20 GB and Ubuntu will have the rest. When I try to install, I get stuck on Step 4 with a blank page instead of the partitions listed. I checked Gparted to check the partitions and it all seemed fine. Not sure what else to do. Any ideas?

---

### Post by tommcd on 2009-10-30
So that screenshot you posted is from GParted on the live CD, but when you try to install and get to the partitioning part those partitions in the screen shot are not listed? Is that correct?
I don't know why that would happen; but you could try first shrinking the partition you want to install Ubuntu on with GParted to create some empty space, then try to install Ubuntu to the empty space you created.

---

### Post by Takara Pearl on 2009-10-30
That's exactly right. I'll try that and get back with you.

---

### Post by Takara Pearl on 2009-10-30
Okay, tried that, nothing worked. So, now, I deleted all the partitions. All it is is unallocated space. I still get nothing when trying to get past the partition setup. Gparted sees it but when installing, it's blank.

---

### Post by Takara Pearl on 2009-10-30
Anyone? >.>

---

### Post by vyruz18 on 2009-10-30
I had the same problem as you.
I am now successfully installing 9.10 using the alternative CD.

An interesting thing to note might be:
The alternate (text based) installed gives me an option "Do you want to load SATA RAID driver", I don't get this option in the nice graphical installer using the standard CD.
When I select 'yes' and have this driver loaded, also the alternative installer can't find my disk. However, when I answer 'no' and the driver isn't loaded, my disk is detected fine.

Currently I have only one disk but normally I have 4 disks:
- sda : 80GB for linux
- sdb : 140GB RAID1 array for Win7
- sdc : 250GB data (storage) disk

When all 4 disks(3 in fact since 2 are RAID) are connected the installer will see the last 2 disks but not the first one.

---

### Post by Ron-In-Kerrville on 2009-10-30
I have the same problem. My hardware worked fine with 9.04 verson. Now with 9.10, the installer just hangs with a blank screen at the step 4, partition creation. I deleted the space and left it unallocated -- same thing. I allocated the partitions using dpart -- same thing. Cannot get past the partition step of the install. Anyway to pass this problem to the developers? We are dead in the install!   Forgot to mention that 9.10 Beta did install without and problems -- looks like they broke it on the final release.

---

### Post by Takara Pearl on 2009-10-30
I'm referring to just one 250 GB hard drive. I have no need for MULTIPLE ones. >.>; EDIT-- Nevermind, miread that.

---

### Post by Takara Pearl on 2009-10-30
Okay, instead of installing 9.10 outright, I installed 9.04, since it installs fine and upgraded to 9.10.  I guess I just can't install 9.10 directly.

---

### Post by tommcd on 2009-10-31
There was a bug in the 9.10 RC where the installer could not see multiple hard drives. I believe this was limited to the 64 bit version. I installed 9.10 from the 32 bit RC and I did not encounter this problem. That bug was fixed before the 9.10 final release though:
[http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-cant-use-multiple-drives-765311/](http://www.linuxquestions.org/questions/ubuntu-63/ubuntu-cant-use-multiple-drives-765311/)
That should not affect anyone with just 1 hard drive anyway.
If anyone is trying to install from the RC CD, use the final release instead.
Try the alternate install CD, as Vyruz18 had success with that. I always install from the alternate CD. 
Check out the BIOS options for your hard drive(s). Make sure they are not set to RAID if you are not using RAID. Try changing to different options in the BIOS for the hard drives, like IDE compatibility mode if your BIOS has that.
Lastly, try the 32 bit CD if you have no success with the 64 bit CD.

---

### Post by socket on 2009-10-31
I have the same problem...
My topic: [http://ubuntuforums.org/showthread.php?t=1307012](http://ubuntuforums.org/showthread.php?t=1307012)

I'm trying to install Ubuntu 9.10 Desktop 32bits on a 250Gb SATA HD with all partitions prepared.

Now I'll try the Alternate to see what happens...

PS: I'm not trying RC! It's the FINAL VERSION!

---

### Post by ColJep on 2009-10-31
I posted a similar thread yesterday. I was able to get the install working after running gparted from the live install and then the install program.

Enough cases here to be a bug I think.

---

### Post by dhavalbbhatt on 2009-10-31
Bump -

I am trying to install Ubuntu 9.10 64 bit on my laptop - HP dv5 - using LiveCD. The LiveCD worked fine - which is why I was OK to install. However, it seems that the LiveCD is hanging on partition manager, trying to partition my HDD. Oh, BTW, I did burn the ISO on 10/29 using bittorrent. It seems there is some activity going on, but I can't seen any progress. It's been 20 minutes (never has taken so much time to partition my HDD in the past - I use Ubuntu 9.04 64 bit, and don't have any issues with creating partitions and stuff.

Has a bug been filed on launchpad?

Thanks,
DB

---

### Post by tommcd on 2009-11-01
> **dhavalbbhatt said:**
> 
Has a bug been filed on launchpad?

This does indeed seem like a bug. I did a quick search on Launchpad and  only found bugs related to RAID setups and the previously mentioned problem with the 9.10 RC CD.
You can file a bug report on Launchpad. See this:
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
I would be interested to see what the developers have to say.

Can someone try creating partitions first with a Parted Magic live CD and then try installing 9.10? I have seen at least one case where Parted Magic worked when GParted did not.
[http://partedmagic.com/](http://partedmagic.com/)
This is the only other thing I can think of, other than the what has already been posted.

---

### Post by kal on 2009-11-01
I got the same problem here with final iso version 32 bit. Need to go with alternate CD :(

---

### Post by Ron-In-Kerrville on 2009-11-03
I had to do the same thing that you mentioned.  I deleted the ubuntu partitions and reallocated them with a product called DriveManager.  Then I reinstalled version 9.04 and after all the maintenance, I installed version 9.10 from the Internet site.  I do not have a RAID system, but my controller board has the ability to setup RAID.  I only use and have 1 disk drive.  This is really a bad bug in the 9.10 ISO install.  Version 9.04 ISO disk installs perfectly.  Anyhow, I am now up and running on 9.10 version.  Thanks for your ideas...

---

### Post by Arand on 2009-11-30
This is likely the bug described at [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/459054)

One solution which seems to have worked for several is to remove the dmraid package temporarily in the livecd, which would make the installer see the disks/partitions again.

This can be done speedily through the terminal:```
sudo apt-get remove dmraid
```or through **Synaptic**: System>Administration>Synaptic package Manager>> search for "dmraid" and remove that single package.

- Arand

---

