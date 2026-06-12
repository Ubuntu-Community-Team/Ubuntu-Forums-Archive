---
title: "problems in Ubuntu new install"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by dreamer565 on 2009-05-16
Having issues with a new install of 9.04.  I'm new to this.
Ubuntu is installed to a external USB drive (have issue no longer being able to boot to windows xp which is a separate issue).  

Ubuntu installed to a 2.5GB media partition that it created, and also have just under 1 terabyte available on the new hard drive.  Windows is installed on a 80gb internal drive which had over 60% free, and have a 2nd 120gb internal drive used inside windows.  I can see the 2nd 120gb drive in ubuntu and access the files but not the internal 80 gb drive. When I first installed ubuntu, it recognized i had xp and pulled in my documents from the 80gb drive.  However, I no longer see them.  That's minor - i have a backup.

My main complaint is that the web browser doesn't work.
Firefox crashes on me if i click tools - addons (haven't tried to install anything other than flash).

Any changes i make inside firefox aren't persistent.  If i close firefox and reopen it any changes are lost.  This is without a reboot. 

If i try to download a file it will tell me i'm out of space.  If i open options to have it ask me where to save documents and try to download something - the window that would allow me to browse to a new location pops up but is behind the error window that says i can't download.

Also can't fill out forms - for example can't login to this forum, enter user name and password and click login and nothing happens.  Same thing occurs if trying to register at a new site, etc.

Also, don't have any back buttons in firefox - can't go back to preceding webpage.

This was all working initially when first installed ubuntu.

If i need to reinstall - how do i install over top of the existing install without wiping out my windows install (that is already not booting correctly)?  i don't want to do any more damage than already's been done.

any help would be appreciated.

---

### Post by mikewhatever on 2009-05-16
A 2.5 GB partition is really barely enough for Ubuntu. Can you post the output of **df -h** command from Applications->Accessories->Terminal to verify the size.

---

### Post by dreamer565 on 2009-05-16
ok... more things that don't work in the new install -
downloaded the copy of ubuntupocketguide-v1-1.pdf and can't open it.  It doesn't give an error just doesn't do squat.

also can't open openoffic - get fatal error - the application cannot be started. an internal error occurred.

So it appears my working install of ubuntu 9.04 decided to crap itself.

Sometimes also get random errors saying cannot create folder '/home/user/....' no space left on drive.

so my file structure might also be hosed.  I went basically with defaults when i installed instead of selecting the "advanced" option to manually adjust - silly me, guess i thought it would know more about how to allocate space than me, a newbie.

So... looking more and more like i need to reinstall it.  

So, next question is what is the easiest way then to either a) correct this install. b) install a clean (and workable) new install over top of this one (or how to remove this one and start again.)

I also have a windows xp drive that apparently the mbr is hosed - it won't boot to windows. If i select that option from grub it tells me invalid device. So also would like that fixed, and/or don't want to make it any worse by reinstalling the ubuntu.

For now, i've switched back to my winxp laptop.  least it runs.

my only (workable)option for now to boot my desktop is to put the live cd in and use the bios boot menu to select boot from cd

that sux.

Anyone out there that could point me in a direction? besides just reformatting and reinstalling windows from the original cd's and giving up on running linux?

---

### Post by Idlerwheel on 2009-05-16
I can't get any of my settings to persist either and i have a 250 gig hard drive devoted to 9.04 internally. This is my third install and even after updating the system it would not save any settings. Any ideas?

---

### Post by dreamer565 on 2009-05-18
@Mikewhatever - I agree that 2.5 gb is not a very large partition.  So most likely that is the problem.  My complaint then would be why does the default install set that up?  I pointed it at the external drive that is just under 1 terabyte.  I did not adjust partition sizes, did not click on advanced during the install.  Apparently i should have.  I made the assumption that it would create the partitions the sizes they should be.
 
----------------------------------------
 
Strangely enough I have been running on the live cd and don't have near the problems even though i would expect that to have even less space to "save" anything since you can't write to a CD.  I then tried another approach by selecting the option to create a bootable USB drive - from within the Live session.  Once again, I was very disappointed to see that it doesn't turn the entire drive into a bootable partition, it once again carved out a tiny 2.5gb partition.  This time however, it allowed me to select the size, and I chose 200gb for the size of the partition to save changes.  For whatever reason, it appears to have ignored that.
 
Looks like i will have to go into gpart and manually delete the tiny partitions and create my own.  My guess is that i will then have to install ubuntu and create the partitions by using the advanced install and make a "best" guess as to what each partition size should be.  
 
If the objective of this version of Linux is ease of use for non-technical people, it isn't too successful.  I'll be ok, and will figure it out, but then I am a technical person - i'm just not a pro with linux.  oh well maybe the best way to learn something is to break it over and over in the process of trying to get it to run correctly.
 
I'll post the results from the **df -h **next time i'm in front of the machine.

---

### Post by dreamer565 on 2009-05-19
@Mikewhatever -
Here's the df -h (didn't run it in sudo so don't know if that matters, also ran it from the live-cd version that is currently running from my external usb drive, it might be different if i ran it from the copy of ubuntu i installed, but that one isn't usable to get online):

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  200K  1.5G   1% /dev
tmpfs                 1.5G  652K  1.5G   1% /dev/shm
rootfs                1.5G   31M  1.5G   3% /
/dev/sdc1             927G  1.1G  926G   1% /cdrom
/dev/loop0            676M  676M     0 100% /rofs
tmpfs                 1.5G   12K  1.5G   1% /tmp
/dev/sdc5             2.3G  2.3G     0 100% /media/disk
/dev/sdc7             2.3G  2.0G  257M  89% /media/disk-1
ubuntu@ubuntu:~$

---

### Post by dreamer565 on 2009-05-19
@idlerwheel -
I never got an actual answer, but it appears that if you install ubuntu without resizing partitions (done inside advanced options) then it goes with some sort of default that appears to be way too small to be functional.  I have a 1 terrabyte usb drive, and wanted to use all of it for ubuntu.  Somehow, ubuntu installed with only a 2.5gb media partition.  which since it is too small, none of the setting changes can be saved or updated.  Currently I"m running a live-cd version i saved to the usb drive following directions i found on this forum.  It works well, and i can actually update settings but they won't persist if i reboot.

my next step is to reinstall again and resize the partitions.  I was just hoping that i could use a default install and let it adjust partitions or at least provide guidelines. but looks like i need to do a little more work to on my end.

I will say that ubuntu didn't have any problems with any of my hardware.  It recognized my network cards, (wireless and lan), and my graphics cards etc.  only thing so far that it can't do anything with is our lexmark wifi printer/scanner/fax.  That one it sees as a network device but has no clue.  which i guess is more a lexmark issue than a ubuntu issue.

---

### Post by mikewhatever on 2009-05-23
> **dreamer565 said:**
> @Mikewhatever - I agree that 2.5 gb is not a very large partition.  So most likely that is the problem.  My complaint then would be why does the default install set that up?  I pointed it at the external drive that is just under 1 terabyte.  I did not adjust partition sizes, did not click on advanced during the install.  Apparently i should have.  I made the assumption that it would create the partitions the sizes they should be.

Actually, a 2.5 GB partition is very very small. I'm not sure what's the minimal requirement, but a guess would put it in the vicinity of 3 GB. It's even hard to beleive the system finished installing.
As for the complain, I am not affiliated with Ubuntu devs, and have never had that problem, so I don't know.
The output of df -h run from the Ubuntu installation should have shown the state of the system partition, its size and fullness. Since it was run from a live cd session, the output is rather useless. I am also in favor of reinstalling and making sure the root partition is at least 5, preferably 10 GB.

---

### Post by dreamer565 on 2009-05-24
For what its worth, I did reinstall.  I tried several things, but found what worked for me was i had to manually re-partition the 1 terabyte usb drive myself in order to get ubuntu to get it to be a usable os.  i was disappointed, since i felt the automatic install should have sized the partitions in such a way to be usable, or at least give an error warning that it couldn't.

But this issue is now resolved.  The key was to use gparted to look at and resize all the partitions manually, then use the advanced install to install to what was now the free space on the spare drive.  The automatic install might have worked better if i was installing it to the internal drive and not the external usb.

In any case, i now have a working ubuntu on the usb, a working xp on the 1st internal drive, and only issue now is that i can't use grub to boot to xp.  The XP drive boots fine using bios to switch the drive order (selecting first internal drive as boot).  Ubuntu boots fine from Grub (leaving the usb drive as the first boot device).  If i select the Other - XP from Grub i get a error 12... invalid device.  Since the drive does boot from bios, that tells me it is just something wrong with how grub sees the boot device.  I won't go into more details here, there is another thread @ [http://ubuntuforums.org/showthread.php?t=1161187](http://ubuntuforums.org/showthread.php?t=1161187) for that issue.

---

