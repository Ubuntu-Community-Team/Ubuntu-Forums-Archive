---
title: "Ubuntu 9.10 Has Much Wrong With It"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-11-09
I've written other posts about Ubuntu 9.10, and none of them are flattering.  I've read posts by others, and I see I am mot alone in the low regard for it.

It's had glut added to it to make a better show of the install process, but at the cost of many applications and a cut in the thorough underpinning that would make its install and operation as painless as with earlier versions.

I've noted with several releases that using F4 to enable safe graphicsw mode only worked until you got to the Desktop, at which point the screen would revert to the highest resolution setting allowed for it.  That makes it too hard to read the text, but then you have to figure out where the controls of the screen resolution is located and how to adjust it.

Ubuntu takes this a further step down.  First, F4 does nothing to make the text larger during the initial install process.  And again, you have the highest resolution allowed when you reach the desktop.  But sometimes the mouse does not show up at all, meaning start again, or if you try to use System/Prfeferences/Display to adjust to a lower setting, the screen just goes black until the confirmation period passes.

Third, after the install is all done and you perform a reboot, there is less than a 50% chance that the reboot will work. If you try the recovery mode, you get some choices of what to do on the screen, but even if you  try one or more, there is no option to then continue the boot process,  You have little choice but to force a reboot yourself.

Third, the install process is greatly slowed by repeated actions of the partitioning softwsare. I have three drives attached, total capacity of over 1 TB, and it takes forever for the partitioner software to perform a single scan of each.  Now the only information of importance in a general scan here is to do the following:

(1) Identify all the drives with the drive designations
(2) Check for the presence of partitions and unpartitioned areas, noting the size of each
(3) If formatted, note the type of file system being used there  

It is not necessary to scan each individual partition, or to determine how much of the partition is in use or how much free space remains.  These are not really factors in deciding which partitions will be used for the install process. If someone wants this information, they  should use the separate gparted.iso and create a CD, then run this first.

You see, with the way this partitioner is working, and the fact that every single action taken with regards to any partition means a total rescan of all the drives and all the partitions again, means a very protracted manual process here.  This is an unnecvessary time waster, made much worse when drive capacity is relatively high.

Ubuntu 9.10 shows a real tendancy to just hang.  How can you tell if it is hanging  or not?  Can you move the mouse, or see the little timer that replaces the mouse pointer turning?  If not to either of these questions, you are probably hung.  Will the PC resume working on its own?  Maybe, but it seems to take quite awhile.

i downloaded the Ubuntu 9.10 image three times, and burned four CDs from each image, and keep trying this one or that one as I labor to complete a good install.  Sometimes I seem to hit it right, butwhether it is the image, that CD copy, or some other facctor is very uncertain.  In some cvases I get some lights on the keyboard flashing when no further progress seems to be taking place.

I/m trying something a bit different right now.  I am starting with a clean install of versions 9.04, and the only thing I intend to do there is get a lower screen resolution at the desktop.  Then I will try a version 9.10 install right over that 9.04, and see if that lower resolution setting holds up.  I don't really know what to expect, but I have to try something different.  Otherwise, this is all just a waste of time.

---

### Post by oldefoxx on 2009-11-09
Can't really call this one SOLVED, but there is a way around some of the problems with installing Ubuntu 9.10

After several days of struggling, I decided that both suggested methods of installing Ubuntu 9.10 were just not reliable enough, and different problems would surface at different points.  Some of the symptoms have been mentioned in my other posts, and others have reported their own problems as well in their separate posts.

So what works?  What I found works is to first do a new install of Ubuntu 9.04, then under the Update Manager just pick Upgrade.  Don't worry about any of the fixes or updates listed below that point.  Since this is a raw install of the OS, the partition for / has to be reformatted before doing Ubuntu 9.04, or you can attempt to do an over-install of a previous version by electing not to format.  That way the /home folder and subfolders should be left intact.

This way you don't download and burn the ISO file for 9.10 to CD.  It gets downloaded and replaces the system files of 9.04 as part of the whole upgrade process.  And this works, if imposed over a new install of 9.04.

The second thing to note, is that don't pick the second option during the install of 9.04, which is to go right into the install phase.  Pick the Try, or first option, so that you have a chance to get to the System/Preference/Display in the desktop mode to set an easier-to-read resolution.  Then click on Install on the Desktop, and now going into the install phase, you keep that same resolution.

Your drives are going to get scanned, and then you will be offered three options about where and how to partition Ubuntu.  What has to be done is for the Installer to be told which patition is to serve as root (identified by /), and which should serve as swap.  Swap should be about the size of your RAM, though some like double that.  The installer will warn you if you skip on designating a swap, but go ahead with the install anyway if you say go Forward.  If you pick manual mode for managing the partitions, you have a choice of which file system to use.  Many use Ext3 or the newer Ext4, as these are both based on Ext2, but with added journalling capabilities.  Since installing 9.04, even though treated as a new install, may actually be targeted to replace an existing Ubuntu or Linux install, the manual mode lets you ensure that it goes into the same partition used originally.

As explained elsewhere, there may be a dispute between Windows and Grup over which is the first hard drive, what Windows reports as C: and what Ubuntu sees as /dev/sda or /dev/hda. The system is designed to boot from C:, and if that is not /dev/sda (or /dev/hda), you will have to point to the drive that Windows sees as having partiton C:  (I label my Windows drives as Drive_C, Drive_D, and on up to make it easy to recognize which is which). What makes this important is that for Grub's boot process to be found later, it must to positioned in the C: drive, or sometimes in the first partition of the drive which is seen as having C: within it.  To do this, you may have to take the summary information page (before the actual install), find the Advanced... button at the lower right, click on that, and change (hd0) to reflect the drive number where c: is found. (hd1) would be an example where C: appears on /dev/sdb instead of /dev/sda.

The first install is the most demanding.  The Upgrade step later takes care of itself.  Now let's talk quckly about trying to bring work forward from a previous install:  If you elect not to format the / drive, then whatever is found in /home, which is all the user accounts, data and such, should remain intact.  But if you want to be doublely sure, you can become super user in a terminal and copy your /home folder and all its contents to another partition, then bring it all back after the install.  The command needed will be cp -r <from>* <to>, but other details about from and to depend on factors like which partition and where to copy to.  For the current partion, you only need /home.  For the target partiton, you will need /media/drive/folder.  Media is where most drives appear once mounted in Ubuntu, and the drive is whatever mountpoint is associated with that drive in table /etc/fstab.  Some might use the drive label, others might use the system identifier, such as sdb5, as the mountpoint name.  Then in order to mount the drive, a subfolder of the same name has to be set up manually in /media.  For instance, to check /media for what subfolders are there already, just type dir /media.  If you need to add a subfolder named sdb5, just use mkdir /media/sdb5.

That should be pretty much it.  If you have yet another prior version of Ubuntu that is on a different partition and you want to bring your work over from it, you can again use the super user mode and the cp -r command, where you identify the path to the old /home/* as being the from, then the path to the new /home as the to.  Note that the only mountpoint for the root drive is /, so /home would be the proper designation for this folder.  Also note that /home is the designation for the folder under the current running version of Ubuntu, so whether it is the from or the to varies.

Like I said, not truly SOLVED, but this serves as a workaround.

---

### Post by Bunnybugs on 2009-11-09
Just one question!

Why should you even bother booting 9.10 over 9.04...

Jaunty works fine, and you can still upgrade on the moment that the bugs are fixed!

I've tried 9.10, but I'm back on jaunty again!

All the trouble seems to be non-sense!

Just stick to the trusted, working version!

leave the trouble to people that can fix it, or can diagnose the trouble

---

### Post by jobo1313 on 2009-11-09
Yeah, i upgraded, regretting that now. Im using my Debian partition until bugs are fixed

---

### Post by presence1960 on 2009-11-09
I did a clean install of 9.10 to a new partition and kept 9.04 just in case. But I have has zero problems with 9.10. I just had to study GRUB 2 to become somewhat familiar with it. 

I did this to have my packages on 9.04 installed on 9.10:

To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages

```

This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```

I also backed up my /home so I could place the hidden directories containing the config files in 9.10's /home that way all the software had the same settings as 9.04

I have to say the clean install went smoothly and following the above insured that all my software was installed for me with a couple terminal commands and all the settings for that software remained as it was in 9.04 once I placed those hidden config directories into 9.10's /home.

On a personal note I stay away from upgrades preferring to do a clean install as I just outlined. All packages in 9.04 except those not in 9.10 repositories are installed with the terminal command above.

---

