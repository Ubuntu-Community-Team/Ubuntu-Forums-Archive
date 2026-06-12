---
title: "newbie help: partition size, uninstall / re-install"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by equiplist on 2009-05-08
Hello All, 
 
 Thanks, in advance for reading, or replying to, this post.  
 
 I am using an Acer Laptop running on Windows Vista Home Premium.  It has a 120 gb drive, but was only advertised as 100 gb.   There is a 10 gb hidden partition with the Windows Vista factory image on it, and is further divided into 2 'disks' a C:\ drive and a D:\ drive.  I have had to reload Windows Vista more than once, for various reasons.  The C:\ drive gets formatted, but the data on the D:\ drive remains untouched.  
 
 Am new with Linux.   I tried 'portable Ubuntu' but is was acting very buggy, so I tried Wubi as a Windows program. I liked it enough that I decided to go ahead with installing to the hard drive.  The installation went fine.  I was able to switch back and forth from Windows to Linux okay.  And then I went to update Linux, and I received the error message 'not enough disk space'
 
 When installing, I opted for the 'side by side with Windows' option. The install program selected 2.5 gb for the partition size, most of this is taken by the operating system.  Leaves little or no room for much else.  That's where things got sticky.  In checking the options in Ubuntu, I don't see a way to alter the partition size.  Going back to Windows in Disk Management, I can't do anything with the 2.5 gb Linux partition.  I can't change the size.  I can decrease the size of the C:\ or D:\ partitions, but afterwards I still can't change the size of the Linux partition.  
 
 Next, I went online searching for help.  But all I could find were mentions of Wubi's uninstall, which is meant for when it is installed as a Windows program.  Frustrated, I just removed the Linux partition. When I went to reboot, the Grub loader failed, just hung, I couldn't even get Windows to load.  But the computer was still looking to boot off of the CD, and I still had the Ubuntu CD in it, which was loading okay, so I re-installed Linux.  

This time I started to play with the installation partition settings.  When I thought it was set the way I wanted, there was an error message about root directories.  I felt I was in over my head.  Did not want to take a chance of losing the Windows partition, having to re-install that as well.  (I do have good backups of my data).  So, I re-installed Linux again, with the same options as the previous time: 'side by side' with Windows, and no special partitioning instructions.  

Previously, when I looked at the hard drive in Windows Disk Management, I saw a 180 mb partition, that had me scratching my head.  Turns out it was a swap file for Linux/Windows.  Now, there are 2 swap files showing.  

Okay, apologies for the long write, but I was motivated, and wanted to get all the details correct.  At this point, I guess I will have to re-install Windows, unless someone can provide me with an alternative.  Also, I will need advice on how to properly set up the Linux partitions, so that I can have both systems available.  With this small hard drive, as Windows is a space hog, I won't have a lot of space for Linux, but am hoping 10 gb should be sufficient.  

All the best, Barry
Equipment Recyclers

---

### Post by Mark Phelps on 2009-05-08
If the Vista partition is still there, to be able to boot back into it, all you have to do is boot from the Vista DVD and run Startup Repair a few times (once is usually not enough).

In future, if you want to dual-boot with Ubuntu in a separate partition, don't let the Ubuntu installer shrink the Vista OS partition; instead, boot into Vista and use the Disk Management tool to do the shrink.  The Ubuntu installer (and GParted) has a history of SOMETIMES corrupting the Vista OS as a sideffect of shrinking it.

---

### Post by equiplist on 2009-05-09
Hello Mark, thanks for the prompt reply.  

Now I am completely down.  I reloaded Windows.  On reboot, I started getting a Grub 22 error.  Do you think the 2 swap partitions was a factor?  

The Ubuntu disk won't even load, just gives me a 'operating system not found' error.  The Windows disks loads & runs, but on the subsequent reboots, the Grub 22 error shows.  

I was able to get the Windows disks to start in Safe Mode, but the option to repair startup doesn't show.  The option for the command prompt doesn't work, just takes me back to a strange version of Safe Mode.  There is no task bar, I can't do anything with it.  I also tried Ctrl-C when Safe Mode is loading, with no effect at all, in hopes of getting to a command prompt.  

I am writing this message from my cell phone.  Now I need to get to another computer to make a CD boot disk.  I hope that works, so I can repair the Grub error.  If not, I guess I'll have to reformat the entire disk.  

I don't have a ready copy of Dos on  CD, but I should have an old copy of WinXP stored on a usb drive.  Any suggestions would be greatly appreciated.

All the best, Barry

---

### Post by caljohnsmith on 2009-05-09
Hi Barry, are you still able to boot the Ubuntu Live CD on that computer? If yes, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by peacen1k on 2009-05-09
This sounds like almost exactly the same issue I have.
   
I installed side y side and couldn't adjust partition size from 2.5gig with gparted.

I ran the install CD again and this gave me the option to use all the disc space or manually configure partitions.

I didn't want either option so I downloaded a free partition editor... thinking to resize xp partition and then try again with gparted. 

This didn't work...... so I deleted the Ubuntu partition and prepared to install again.

Only now I have a Grub error 22.

---

### Post by equiplist on 2009-05-11
Hello All, 

Problem solved ... I think, I hope.  

Obviously, the Grub file was corrupted, which caused the problem.  Apparently the Ubuntu Live CD I had was no longer any good.  A new Live CD booted with no problems.  When I first used Ubuntu, the option to check the CD on the Live CD ran okay.  I did not check the file for MD5sum.  

I decided not to try and repair the Grub error, to go 'cold turkey' on Windows Vista.  So, I went ahead with a full install of Ubuntu 9.04, formatting the entire disk drive.  This worked flawlessly.  So far, so good.

Now I have 2 hardware issues I need to solve.  The printer at work is an old Canon multi function (copier/printer), the driver software is Win98.  At one earlier point, I tried Windows 7, but could not print.  I could not get the printer drivers on the Canon factory CD to work, and nothing was available yet for Windows 7.  So, I had to revert back to Vista.  But I should be okay here, even though I have not yet checked driver availability for Linux.

A little bit stickier however, is my internet connection.  I use Xohm/WiMax (soon to be ClearWire).  I have 2 modems, a 'home-based' (120 VAC), and an ExpressCard for when I am on the go.  The home modem plugs into the ethernet, and I also have it connected to a wireless router.  The home modem/wireless router combination was a bit buggy when using wireless with Live CD, is now working perfectly.  I have not yet to tried the ethernet cable.  Xohm's 'Connection Manager' is Windows software, and they do not support Linux.  

If I cannot find 'native' Linux solutions for these hardware issues, hopefully Wine will do the trick.  

All the best, Barry, Equipment Recyclers

---

### Post by peacen1k on 2009-05-11
Well done.
 
I re-installed too which fixed gru8 now I can access xp and U8untu.
 
I'm gonna slowly work up to a full install..... as long as all my essential programs work.
 
;o)

---

### Post by bmfc187 on 2009-05-17
hi, i have the same problem, only i havent done anything brash yet.  I had JUST NOW installed ubuntu with the "side-by-side" option and left it at 2.5g...and i came looking to reformat it.  I havent yet deleted anything or even gone back to windows yet to know wether its working or not...i came straight here.  so i guess MY problem is that yours got solved without figuring out how to resize the partiotion.  anybody know how i can do that effectively?  Everything else seems to be working great but i wanna make sure before i go doing anything crazy like deleting Windows.  so i just need to figure out how to resize my ext3 partition.  thanks in advance...

wait, am i correct in assuming a reinstall of ubuntu clears that up?

-BMFC

---

### Post by equiplist on 2009-05-18
Hello, 

I hope you have good backups of your data.  What I did was a fresh install from the Live CD, selecting the option to install on the entire disk, as opposed to side-by-side.  Hope this helps.  

All the best, Barry, Equipment Recyclers

---

### Post by bmfc187 on 2009-05-18
> **equiplist said:**
> Hello, 

I hope you have good backups of your data.  What I did was a fresh install from the Live CD, selecting the option to install on the entire disk, as opposed to side-by-side.  Hope this helps.  

All the best, Barry, Equipment Recyclers


thanks but im kind of avoiding wiping Windows completely just yet...i still wanna make sure everything works before i go doing anything like that...i know my wireless works, but in answer to your questio, no i dont have good backups of everything yet, thats what my today is consisting of...its still not a problem, i seem to have both OS booting and running and working just fine, only thing is that i only alotted it the 2.5GB partition that it defaulted to, which apparently isnt enough to hold the whole system?  i dont remember how i got to it but it told me that the system was larger than 2.5GB or something...it told me not enough space...so anyways i dont have enough space on ubuntu to even make a recycle bin directory...but my W indows Partition Manager is telling me i can only shrink my windows partition by about 1.5-2GB, when i know i have like 49GB free space on my Cdrive.  any ideas?  Thanks in advance....

-BMFC

---

