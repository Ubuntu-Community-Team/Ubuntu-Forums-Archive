---
title: "Ubuntu 8.10, 9.04 booting from CD destroys my fakeraid array."
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by Throwback on 2009-04-22
Motherboard: Gigabyte GA-M750SLI-DS4 (rev. 1.0)

I thought I'd post this here first to see if anyone else is suffering from this problem; I currently have Server 2008 on a mirrored (RAID0) array comprising three SATA disks and I am keen to see if I can get a Linux distro (ubuntu being my favourite but certainly not the only option) to share this. If needs be I can free up a drive from the RAID and install linux to a single drive and select the boot order from the bios.

However, booting from the Ubuntu CD (x86 or x64 it makes no difference) has an unfortunate effect on the existing raid arrays- once i have booted from the Ubuntu CD every time I cold start the pc from a power off state the RAID does not check out and comes up as "faulty" in the nvidia raid bios. As a result in order to boot the PC I must boot into an ubuntu live environment, then restart and then after ubuntu has "looked" at the hard disks the RAID will initialise correctly. I have tested various configurations and have come to the conclusion that something Ubuntu does to the hard disks on bootup is deeply unpopular with the Nvidia raid bios!

I have not yet tried any other linux distros on this configuration yet (planning to try openSUSE as I am told it supports fakeRAID straight out of the box)as it is somewhat irritating to have to wipe the drives, rebuild the RAID from scratch and restore the filesystems. However I do have backups and can restore my filesystems intact so I am able to experiment with little repercussion.  Anyone else had this happen to them?

---

### Post by ronparent on 2009-04-22
Your conclusion in regards to the nVidia raid bios is probably correct, though not in the sense that anything has been written to the array! Are you using either the alternate cd or the server cd. Either of those distro's will recognise the raid . The standard desktop cd does not recognize that an array is present.

Also is it a raid0 (stripped array) or raid1 (mirrored array). If it is actually a raid0, do you have your data well backed up.

---

### Post by Throwback on 2009-04-24
Hi Ron thanks for replying.

Its a RAID 0 and yes my data is well backed-up. The weird thing is that the array itself remains intact- once i boot off an ubuntu cd and then power off and power up again the array status (on the raid bios screen) comes up as "FAULTY". I can reset all I like, boot windows based live cds etc and the array still comes up as "FAULTY". I have to boot off an Ubuntu disc and then restart before the array will come up as "HEALTHY", and then windows will boot as normal from the array. I will try the alternate CD however and see if it does the same thing. 

Does the alternate CD have support for dmraid straight out of the box? I have tried using DMRAID with various linux distros before on nvidia raid arrays with no success (I normally just end up with hosed arrays and have to start again, although lack of documentation and help at the install stage has often left me in the dark as to precisely how Linux views fakeraid arrays and how they should appear to the OS once they are initialised.

Its rather time-consuming testing this because each time the array gets made "unstable" by booting off an ubuntu cd, I have to destroy the array, shut down, start up, recreate it, reboot into my windows live environment, load f5 drivers, then restore the image from a usb drive, then boot off the server 2008 disk, load more drivers, enter the recovery console and fix the MBR. Its about an hours work to repair what booting off the live cd messes up in seconds. 

Its enough to make me just buy some SSDs and give up on RAID...

---

### Post by ronparent on 2009-04-24
Is it possible that your raid hardware requires a linux specific driver to function correctly? For windows such is a requirement to be able to use the disks in the arrays. For many raid setups, especially motherboard based one, dmraid serves that purpose. It sounds like merely looking at the array sets a flag declaring the array faulty. 

In-so-far as how the fakeraid arrays appear in linux, look for /dev/mapper/. If dmraid actually mapped the partions on your raid array, the raid partitions will appear as symbolic links in this directory. These symbolic links are made visible in your filesystem by attaching them to mount points you have to create in the filesystem for that purpose and mounting them on boot in /etc/fstab.

---

### Post by Throwback on 2009-06-23
Thanks for your response Ron. I had to hold off on this until I had an external hard disk and a windows-based boot disk to ghost my array off with. I have now done this so have the nuclear option of "wipe it all, rebuild from images" so I can now afford to break stuff.

I removed the RAID in the nvidia bios, booted off a (windows) boot disk, overwrote the drives with 0s, recreated the array, and then reapplied my ghost images from a live windows environment with Norton Ghost.

Now booting off the 9.04 disk (have not bothered trying 8.10) no longer causes the array to set a "faulty" flag. Interestingly when I do a "dmraid -ay" now I can see some nvidia arrays, however even more perplexingly they are the wrong size and don't include the correct drives- my setup is as follows:


/dev/sda }
/dev/sdb }  these three drives make up a single ~480gb Raid0
/dev/sdc }

However when I first embarked on this oddyssey it was:

/dev/sda }
/dev/sdb } These drives make up a ~300GB raid0 for windows

/dev/sdc ~160GB single drive for Linux

However dmraid doesn't see the new setup properly, it picks up two 300gb arrays- and one of the partitions from the actual 480gb array. What's more is one of the 300gb arrays appears to be the old 2-drive array from when I was simply trying to get ubuntu onto the 3rd drive, without even using dmraid- previously just booting ubuntu broke the raid0 on the first 2 drives, no longer. Weird- I have introduced no hardware changes since then.

using dmraid -sE (or whichever switch erases metadata) doesn't permanently clear out the old raid mappings- once I reboot I get a "FAULTY" from the nvidia raid bios (to be expected!) but even more oddly when i power off and on again... the raid is back up and "healthy" and when I check dmraid again... all the old metadata are back.

So clearly nvidia raid bios isn't quite as straightforward as we think it is... my (admittedly layman's) opinion is that it is retaining its own database of arrays and metadata and checks the data on the drive with its information, and asserts over the drive's metadata if it finds faults. This would explain the incidence of "ghost" arrays showing up. It would also need to be restoring old metadata, possibly with some "deleted flag" that dmraid doesn't understand. I need to try destroying the array, and overwriting the disks with 0s again and NOT apply my ghost images again to see if the old drive data came from the imaging or from the BIOS. Unfortunately this is a not a quick task.

This could be a problem for nvidia, could be a problem with dmraid, could be both. Either way it is a major gotcha/stumbling block for anyone trying to transition from Windows to ubuntu who has all their existing hard disks in an nvidia RAID (a very common setup actually) and thus has no spare drive to install ubuntu to. In researching this I have found a lot of people giving up on linux because they do not want to have to go back to reduced read/write speeds on BOTH os's. In my case I know that using 3 drives in a raid0 increases my maximum read speed from about 45 MB/s to over 100 so its no insignificant difference. Moreover not every windows user has access to the UBCD4Win and a full win32 copy of norton ghost, and a floppy drive to load the raid drivers, that I needed to back up the existing array. Trouble indeed...

Unfortunately I am at work now and away from the system so I can't provide the proper output. I will follow up this post with more tonight. I had pretty much decided just to go for an mdadm RAID0/lvm2 setup and send nvidia raid to the knackers yard, but I think tonight I will have one last shot at trying to make this work- Its not even about wanting to dual boot windows raid anymore (got sick of it completely, in spite of the headaches the linux way of handling hardware and software is simply better. Shame about the gotchas...) but rather about beating a problem whose solution has evaded me for months. I don't quit easily! 

So yeah, back for round 3 tonight. Takeaway will be ordered. Coffee made. Cigarettes rolled. 2 arrays walk in, one walks out...


You may well be right though- perhaps the boot-time driver for windows does more than just present device-mapped raid to the OS... In any case its moot. My plan is to switch to md raid with LVM2 on top (just because I can) after this, success or none.

---

