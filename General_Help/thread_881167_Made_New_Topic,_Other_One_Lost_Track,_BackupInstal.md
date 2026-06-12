---
title: "Made New Topic, Other One Lost Track, Backup/Install Help"
date: 2008-08-05
forum: General Help
---

### Post by Ninjames on 2008-08-05
Ok so. My Windows installation was screwed up, chkdsk wont fix it, and yeah. So I've figured I need to reinstall Windows. I have a few questions.


I'm making backups of my files in the form of .zip file archives in Ubuntu, and burning them to a data DVD. I'll be able to open this when I reinstall WIndows, right? I mean, the .zip is the same as a windows .zip file, right?

Another question is, somebody told me that after I reinstall Windows if I open up a LIVECD and run the terminal I can bring back the GRUB loader. Does this mean that Ubuntu will still be installed, even after I reinstall WIndows (and am thoroughly warned about it deleted all data on my computer.)

My Windows partition is 160 GB. My recovery partition is 8 GB. My Ubuntu partition is 15GB.

Thanks

---

### Post by rfdeshon on 2008-08-05
Zip is a standard format. A zip in linux is a zip in Windows, etc.

Also, since you just recently installed Ubuntu from what I gathered from your previous thread, I'd suggest starting completely fresh. Once you backup your data, boot the Windows install CD, delete ALL partitions, create a new NTFS partition of the size you want (160GB from the sounds of it) making sure there is enough free space for your Ubuntu install. On the new NTFS partitions make sure you do a FULL FORMAT, quick formats suck on NTFS and are prone to problems. Once Windows is installed, reinstall Ubuntu in the free space you left during the Windows install. This is the safest and most thorough method of reinstalling.

---

### Post by Ninjames on 2008-08-05
Thanks for all your help.

It seems though, last time I reinstalled Windows, I never actually worked with partitions. But then again, in my previous reinstalls, it was just the OS and had nothing to do with data. So I'm assuming I'll get all this partition stuff in the full reinstall.

Thanks, if you've got anything else to add, do so, but you guys have been a great help.

---

### Post by Ninjames on 2008-08-05
AH! I just thought of one more thing. If I delete all partitions.. Wont it delete the partition I'm running the recovery from?

I guess I wasn't clear. I have a Windows OEM XP Home Edition CD, but rather than using that I'm using a partition that came with my computer (Listed as D: HP_RECOVERY) to reinstall Windows. Will I get all the partition options, and will it like.. delete itself? Having that recovery partition is thoroughly helpful. xD..

---

### Post by rfdeshon on 2008-08-05
Ah...
Usually they hide the recovery partition. I'm willing to bet though, that if you use the recovery partition to reinstall that you will not get any options as far as partitioning goes. Usually those things just reimage the hard drive back to factory default. Honestly, I hate recovery partitions. I recommend finding an actual Windows disc for your version and installing from that.

By the way, as far as not wanting to wipe out the recovery partition when partitioning the drive, just don't delete it. During the windows partitioning screen, you have to remove partitions individually anyway, and most Recovery partitions are appropriately labeled as such.

---

### Post by Ninjames on 2008-08-05
So I should go about locating a Windows XP Media Center Adition Disc, using that to install, delete the ubuntu and windows partitions and create a new one? I definitely shouldn't use the recovery one?

I hope I can find a download for a media center addition.. I mean, I Got my serial number and stuff.

Oh wait.. you said the recovery partition that it images it to factory default, wouldn't that achieve what I want of deleting the Windows and Ubuntu partitions? Then once I get into WIndows I can use a third party partition software that wont let me screw up to slice off 15 GB for Ubuntu, and then install to that with the disc?

---

### Post by rfdeshon on 2008-08-05
> **Ninjames said:**
> So I should go about locating a Windows XP Media Center Adition Disc, using that to install, delete the ubuntu and windows partitions and create a new one? I definitely shouldn't use the recovery one?

I hope I can find a download for a media center addition.. I mean, I Got my serial number and stuff.

Oh wait.. you said the recovery partition that it images it to factory default, wouldn't that achieve what I want of deleting the Windows and Ubuntu partitions? Then once I get into WIndows I can use a third party partition software that wont let me screw up to slice off 15 GB for Ubuntu, and then install to that with the disc?

I won't say you definitely shouldn't use the recovery partition. All I said is that I sure wouldn't. I don't like them, I feel they are a cheap cop-out to a full reinstall.

Yes, it will accomplish what you want, however, per my post in your last thread, resizing NTFS partitions often causes Windows to freak out. Usually a chkdsk will fix it, apparently it didn't in your case though. You run the risk of having the same problem because you will have to resize the NTFS partition again.

Also, to avoid opening multiple threads on the same topic, you can subscribe to threads and keep track of them that way. It gives you the option to subscribe any time you open a thread, you can also access it from the "Thread Tools" menu when you're viewing a thread. This helps cut down on duplicate threads and helps centralize information for other people having the same problem or trying to help you with yours.

---

### Post by Ninjames on 2008-08-05
Thanks, yeah I'm sorry I opened another. I guess I was just freaking out a little. I found a download for Windows Media Center (OEM) which means the key on the side of my computer should work just fine, right? I'll reinstall with the disk, which should allow me to access partitions and so as you said?

---

### Post by rfdeshon on 2008-08-05
> **Ninjames said:**
> Thanks, yeah I'm sorry I opened another. I guess I was just freaking out a little. I found a download for Windows Media Center (OEM) which means the key on the side of my computer should work just fine, right? I'll reinstall with the disk, which should allow me to access partitions and so as you said?

That should be correct. If Windows Media Center came preinstalled, your key should be an OEM one. If you're using the Windows disc and not a "recovery disc" then you should get the option to partition. Make sure you only partition the amount you want for windows and do a full format (it will take a while, but it's worth it) and you should be in good shape.

---

### Post by Ninjames on 2008-08-05
Thanks--again.

Downloading that, and backing up data right now. Really glad this forum turned out to be helpful, and hoping to be up and running on Ubuntu again later tonight!

---

