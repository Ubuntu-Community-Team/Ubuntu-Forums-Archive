---
title: "Upgrade from Ubuntu 8.04 to 10.04 Loses DVD/RW and CD-ROM Drives"
date: 2011-03-06
forum: Hardware
---

### Post by StewartM on 2011-03-06
Hello,

I am helping some friends either try Ubuntu, or use Ubuntu. Despite my limited experience (Ubuntu user since 2007) I help these people with their machines. For one family that's a bit computer-challenged, I perform the updates and upgrades. Yesterday, I finally found the time to upgrade their machine from 8.04 LTS to 10.04 LTS.

To speed things along, I decided to burn the Alternate CD of 10.04.2 and perform the upgrade from the CD (their broadband connection's not particularly fast). However, when I did so, I got messages prompting for a partial upgrade that bombed out whenever one tried to follow through. So I removed the Alternate CD and instead tried the upgrade from the internet. 

That didn't quite work either--it downloaded a little over 600 of the 1892 packages needed for the upgrade, and then prompted me for the Alternate CD--but it would not see the CD when one inserted it and would not proceed further after pressing 'Cancel' (I think this problem could have been as simple as the upgrade was asking for 'cdrom' in the stated path,  while their DVD/CD drives are found under  'cdrom1' and 'cdrom2' respectively). So, thinking that I could restore the directories from the trash bin, I did a $gksudo nautilus and deleted the folders 'cdrom1' and 'cdrom2' (there was a 'cdrom0' as well) as well as the link 'cdrom0' under '/media'. The upgrade ceased to ask for the CD at that point and proceeded to fetch the remaining files from the internet. The remainder of the upgrade proceeded normally.

(Of course, deleting these folders under '/media' as root did not send them to the recycle bin where they could be restored). 

When the machine rebooted, it did not 'see' the DVD/RW and CD-ROM drives. (There was another little problem, with it not detecting the wired connection unless you restarted the DSL modem, but two reboots seemed to fix that, at least for now). I immediately set upon finding out how to get Ubuntu to see the two media drives.

I found several threads with people having similar problems:

[http://ubuntuforums.org/showthread.php?t=1468035](http://ubuntuforums.org/showthread.php?t=1468035)

With various ideas. I recreated the directories in /media as /media/cdrom1 and /media cdrom2 and made sure that they had root as the owner and were in the group 'cdrom'. I checked the etc/fstab file and the /dev folder and looking to see if the device names (/dev/sr0 and /dev/sr1) were properly linked to the readings in fstab (/scd0 and /scd/1, and to the directories /media/cdrom1 and /media/cdrom2) and they were. I tried to mount the directories from the command line with to no avail. I should point out that the DVD drive is now 'stuck' closed and the light on it is flashing furiously, as if it were trying to do *something* which it can't.

When I got home, however (where I am now) I checked the setup on my machine, which has two perfectly functioning DVD/RW drives. I found that are *no* entries under etc/fstab and *no* folders for the CD/DVD drives under /media and yet the system works perfectly! Moreover, when I insert a CD or DVD into them, no folder appears under /media. So my 10.04 system seems to be handling DVD/CDs in a different fashion than does theirs.

In fact, some commentators in the above thread and others I have found  suggest commenting the lines out (#) in /etc/fstab, while others suggest doing the opposite, of making sure that a clear link is established via the files and folders in /dev, in /cdrom, and in /fstab. So I have two paths to explore. 

But I'm a bit flummoxed, and having problems understanding how all this is supposed to work. At some point did Ubuntu/Linux start handling DVD/CD drives differently? Is that the root of the problem?

I'm going back there today and will try a few things. If I continue to have problems, there I will be able to post the contents of the files on their machine. Right now I'm searching for ideas.

StewartM

---

