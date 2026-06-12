---
title: "[SOLVED] Hard Drive Problems in Ubuntu 7.1"
date: 2007-12-15
forum: Hardware &amp; Laptops
---

### Post by dplecto on 2007-12-15
I am running Ubuntu 7.1 with three internal SATA seagate hard drives. I have the first (sda) with 160 Gb as my primary hard drive housing all the essential OS files. The second (sdb) is my primary data drive (320 Gb) containing all movies/music and is the most accessed drive in my system.

I haven't have any problems with the first two drives.

But, the third drive, which I use to store my documents is having problems.

For the first few hours after the system boots up, everything is fine. But, after about an hour or so, I start getting problems. The third drive is still mounted and seems to be fine though I can't access any files on it. When I cd to the mount point of the drive and try to list the files, I just get an error message saying that  it can't list the contents - sometimes it does so to the whole drive and at other times, it shows the directories but, fails to list the contents of some directories. Also, at this point, when I try to check the tempreature with hddtemp, i get an error message saying "S.M.A.R.T not available".

Once I reboot, the problem disappears only to comeback after a sometime - within an hour or so.

And, the more funny thing is that, if I use only two hard drive at  a time (remove either the third or the second), this problem doesn't show up. So, this rules out hardware problems with the drive.

What do I do to avoid this problem ? Is this a bug in ubuntu ? I am pretty sure I didn't have this problem with Ubuntu 7.04.................

---

### Post by Jose Catre-Vandis on 2007-12-15
If you swap the connections for your 2nd and 3rd drives, does the problem arise with the "2nd" drive? This would point to your SATA/IDE connections. How are 1,2,3 all connected up? Check your bios for settings, and perhaps the cables and the  connections. Sorry I am still on PATA drives, but as you say the problem seems to point to motherboard/cables rather than software or the drives. ( i have a Gutsy machine with 4 HHD and a CDrom working with no problems.

If you think it is Ubuntu, how are you mounting / what filesystems are in use / did you have this setup when using Feisty / has anything else changed. Check your logs to see if anything is coming up about this problem.

---

### Post by dplecto on 2007-12-15
sda is connected to SATA port 0 in my motherboard
sdb is connected to SATA port 4
sdc is connected to SATA port 5
DVD-ROM is connected to SATA port 2
I port 1 is blocked and 3 is not available.

The filesystems are all ext3. The mount is done using the defaults in fstab .... 
My fstab is fine and it has the same setup as it was on before i changed to ubuntu 7.1 from fiesty (a complete reinstallation
- wiped my primary drive clean)

I swapped the connections between the second and the third drive (and the SATA cables too) but, the problem is the same:
What the third drive (now is mounted from /dev/sdb), went down after 33 minutes of system uptime. 
The only difference is that now,instead of giving the SMART error now, it has vanished from /dev - the /dev contains
only /dev/sda (1 to 6) and /dev/sdc. 

Note, I didn't swap the actual location of hd in the chasis - just the connection from SATA 4 to SATA 5.

When I try to ls it at its mount point, /media/sdc1, i get the error: "ls: reading directory .: Input/output error"

previously, I was getting the following error when i did hdtemp to that drive -  S.M.A.R.T not available
now, it simply states that the drive is not there. ls was giving the same error - though it would be within some directories
 of the drive.

*********************
My solution (hopefully)
*********************************
Finally, I have now gone with adding errors=remount-ro, users option in fstab (the users option is not really necessary).
And, I have the drive out of the drive bay (to help with the cooling) into open with a fan running.

So the problem hasn't come up again (uptime is now 2 hrs 36 min). Hopefully it won't come again.

There has been no remount events for sdc1 since the last boot - so i think it has something to do with the tempreature.
Though when there is no active write events, both sdb and sdc are at equal temp, since sdc is in the floppy bay, it hasn't 
got much of air flow which probably was causing it to heat quickly and hence the errors. (the stupid dell system I am running
has only two hd bay so i had to use the floppy bay for my extra hd.

I will probably keep an eye on number of mount events of this hd and the tempreatures so that I can make a correct assesment
for future.

I am not sure what the exact problem is but, if it comes again, I will test the system with some other linux (SE linux) and
knoppix see what happens - then if it comes again, return the hd to my seller.

Thanks

---

### Post by Jose Catre-Vandis on 2007-12-16
You might want to try editing your hdparm config file so that the drive only spins up when needed. See this thread for how to

[http://ubuntuforums.org/showthread.php?t=308962](http://ubuntuforums.org/showthread.php?t=308962)

'tis odd though that it worked fine before with a previous install, and does point towards a HDD failure/problem of some kind

---

### Post by dplecto on 2007-12-16
Thanks man. I just hope the problem won't arise again .............. otherwise I will simply return the drive to my supplier..........

your suggestion works great.

---

