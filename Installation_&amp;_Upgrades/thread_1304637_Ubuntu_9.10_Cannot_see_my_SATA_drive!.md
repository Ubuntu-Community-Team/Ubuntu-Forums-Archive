---
title: "Ubuntu 9.10 Cannot see my SATA drive!"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by ukblacknight on 2009-10-29
I've got two SATA drives.  One is for my operating systems (Windows 7 & Ubuntu) and my other drive is for my media.

For some reason, the installer can only see my media drive (sdb), and not my OS drive, sda.

GParted can see sda fine, and the drive can be mounted on the LiveCD, which I am on now.  Any ideas why the installer can't see my sda drive?

---

### Post by niite on 2009-10-29
I had the same problem with the desktop version.  I tried the alternate version - then chose to manually configure my partition, and the drive showed up.

---

### Post by ukblacknight on 2009-10-29
I'll try that soon.  This is going to really annoy me!  GParted and the Disk Utility can both see the drive!

Don't know if it's worth noting that it's the last drive listed in the BIOS.

---

### Post by ukblacknight on 2009-10-29
Removed my media drive, hoping it would force the installer to see my sda drive - no joy :(

---

### Post by peyre on 2009-10-29
I understand there's a bug in 9.10 regarding multiple SATA drives, and seemingly, it specifically applies to 64-bit Ubuntu:  [http://www.tgdaily.com/content/view/44453/140/]("http://www.tgdaily.com/content/view/44453/140/")

---

### Post by epee on 2009-10-29
> **peyre said:**
> I understand there's a bug in 9.10 regarding multiple SATA drives, and seemingly, it specifically applies to 64-bit Ubuntu:  [http://www.tgdaily.com/content/view/44453/140/]("http://www.tgdaily.com/content/view/44453/140/")
I'm running 9.10 on 64 AMD with dual raided SATA drives - no problems with the SATA.

---

### Post by hwttdz on 2009-10-29
You sure you grabbed the final and not the RC?  Sounds like a bug that was in the RC, which was apparently fixed before the final.  The workaround would be to manually configure partitions, somehow that forces it to detect the hard drives.  Some of this is from less than stellar sources, such as the tgdaily link.

---

### Post by ukblacknight on 2009-10-29
I am on the 64bit edition.  I downloaded the full version from the website earlier today.  I may still have a disc around for jaunty so I may install that again, and then re-download the image.

---

### Post by hwttdz on 2009-10-29
Earlier today the RC was posted.  It switched around 10:30 est.  You can download the final from a torrent, which is faster than downloading from the site directly (and spreads out traffic).  I'm not sure what the naming convention was, if you still have the image file you might be able to tell by looking at the name.

---

### Post by glaze on 2009-10-29
I have this problem on Kubuntu 9.10 64-bit final release. My computer has SATA DVD and SATA HDD. The HDD doesn't show up in the Disk Setup, but I can view its contents on Dolphin. I have tried to set the HDD mode to IDE and AHCI in my BIOS to no avail. My mainboard is Intel DG45ID.

edit: Alternate CD works and I'm now installing.

---

### Post by Hordac on 2009-10-29
I am having the exact same problem.  Upgrading from 9.04 to 9.10, it does not see my SATA 80GB HDD during a fresh install.  

If I boot off the 9.10 CD, my HDD is there.  I've tried reformatting to ext2, ext3, no difference.  I've even used the disk utility to format the hdd to ext4, still does not see the drive.

I've reinstalled 9.04 now and using Update Manager to try and udpate to 9.10.  We'll see how that goes.

---

### Post by niite on 2009-10-29
> **Hordac said:**
> I am having the exact same problem.  Upgrading from 9.04 to 9.10, it does not see my SATA 80GB HDD during a fresh install.  

If I boot off the 9.10 CD, my HDD is there.  I've tried reformatting to ext2, ext3, no difference.  I've even used the disk utility to format the hdd to ext4, still does not see the drive.

I've reinstalled 9.04 now and using Update Manager to try and udpate to 9.10.  We'll see how that goes.

Thats the route I ultimately ended up going with, had to many problems with the clean install.  Though I was able to solve the not seeing drive issue by using the alternate version and then going with manual partition setup.

---

### Post by ukblacknight on 2009-10-29
I just reinstalled Jaunty, my drive showed up fine in that!  That's just a stop gap, I'll redownload the iso again and install it soon.

Quite a show stopping bug really...

---

### Post by donkeyX on 2009-11-13
I am having the same problem for days now. Have tried the bois drive options: native ide and other but every time i get to the partition manager there are no drives listed. I have also tried using the pci=nomsi option among others. I have no idea where to go from here since this is becoming a real pain... 

My system : 
2x sata 250g drives
1x sata cdrom
gigabit mb
attempting - mythbuntu 9.10

Cheers dave

---

### Post by redbear on 2009-11-13
I have the same problem :(

[IMG]http://i405.photobucket.com/albums/pp135/rubymask/Screenshot.png[/IMG]

[IMG]http://i405.photobucket.com/albums/pp135/rubymask/Screenshot-1.png[/IMG]

Installer can't see any partition on my HDD even though Gparted is still

---

### Post by ukblacknight on 2009-11-13
Using the alternative CD installer worked for me!

---

### Post by Ginsu543 on 2009-11-13
> **epee said:**
> I'm running 9.10 on 64 AMD with dual raided SATA drives - no problems with the SATA.
The Karmic installer apparently has no problems seeing raided SATA drives but apparently does have trouble sometimes recognizing multiple SATA drives as individual volumes (especially if they have been previously used in raid arrays). It could be a problem with dmraid. I had the same problem as many posters in this thread and this is how I got around it:

1) Unplug all drives except for the one installing to
2) Boot into live session using Live CD (without installing)
3) Open Terminal and run "sudo apt-get remove dmraid" (without quotes of course)
4) Run the installer by double-clicking on its icon

See if that will get the installer to recognize your drive. If it does, then you're in luck. Once you install the OS, shut down, reconnect all the other drives, and reboot. Everything should be working normally from that point. One point of note: if you install GParted, you may need to uninstall dmraid again to boot properly because GParted reinstalls dmraid as part of its package if it is not found. All this is unnecessary if you are installing Karmic onto a raid array, however.

---

### Post by RinkS on 2010-02-06
i succesfully installed 9.10 x64 bit on my RAID1 SATA rig. Just here to validate one of the techniques listed above. Im no where near being an expert on this subject, just giving my experience with this distro.
 
[LIST=1]
[*]Load the live cd (get to the desktop)...
[*]open terminal - Applications\Accesories\Terminal
[*]type in: **sudo apt-get remove dmraid** and hit enter
[*]hit **y** and then enter again, wait for it to finish then close terminal
[*]double click on the installer icon on the desktop to start the install
[*]when you get to the partition manager screen choose only one set of mounts and swap space ( ie. all on one HDD)
[*]continue with the install, i really recomend **NOT** choosing to migrate anything from a windows user, my install just crashed at 89% twice, YMMV...
[*]Choose the reboot when the install is done and "TA DA!" you got a x64 bit Ubuntu running!
[/LIST]I am by far no expert here, but i think by choosing all the mounts on one hdd in a BIOS RAID system wil reduce the risks of conflict when i try to use the disk manager to create a linux RAID in software in a few minutes..
 
Pent D805 @ 2.94GHz, 2GB DDRII Mushkin 533, 2x Barcuda 7200.12 - RAID1, nVidia 8800ultra, LG 22", Antec P182SE, Razer Lycosa & Deathadder, M Audio Studiophile LX4 5.1 Monitors, "modded" 1285VA UPS (from 100-60% charge takes 2:27 minutes @ ~ 270W), Dual boot: Ubuntu 9.10 x64 bit & XP Pro SP3 x32 bit

---

