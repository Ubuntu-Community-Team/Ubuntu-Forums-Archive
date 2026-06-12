---
title: "Harddisk S.M.A.R.T failed."
date: 2014-12-04
forum: Hardware
---

### Post by Azyx on 2014-12-04
Have a HDD, that have being in a bad ventilated extern disk.

S.M.A.R.T failed because of bad  wentilated air--flow or something and I wonder if there are something to reset or make a forced mart-test, or something.

/Cheers

---

### Post by tgalati4 on 2014-12-04
Your disk has 50 uncorrectable errors.  So back up your files and try using the manufacturer's utility to perform a diagnostic and perhaps a low-level format.  Sometimes external drive errors are caused by lack of power rather than just temperature.  Try putting the drive inside a desktop computer and running the diagnostics including a short and long test.

```
sudo smartctl -t long /dev/sdg
```

To view the results:

```
sudo smartctl -a /dev/sdg
```

Your drive (which is probably not /dev/sdg) can be found with:

```
sudo fdisk -l
```

---

### Post by Azyx on 2014-12-04
Thanks!! I have backed up the drive and empty it and put it into a desktop computer (Ubuntu 14.04LTS) Does Seagate have a tool  for linux? What application does i need for smartctl? smartmontools?  Can't find it in Synaptic.

---

### Post by Mark Phelps on 2014-12-04
> Does Seagate have a tool for linux? I've run SeaTools myself and believe that there is only a Windows version.

But, I've had two hard drives fail me this year, they were both Seagate, and in both cases, they suddenly crashed -- hard!  SeaTools could not find anything on either drive, and I was unable to recover anything from either drive using any data recovery utilities.

So, I would avoid using the Seagate again as it's likely to crash on you without warning at any time.

---

### Post by Azyx on 2014-12-04
J 				 					[ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar311399_2.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=311399") 				 				 					 						 	[**[COLOR=#000000]Mark Phelps[/COLOR]**]("http://ubuntuforums.org/member.php?u=311399") Just woundering if it was Seagate Barracuda ST2000DM001 2TB  7200.12?  Died for me with click of death, and it seems to happend to other also, this year. Not used much at all :(

---

### Post by oldfred on 2014-12-04
Smart tools are is Disk Tools in 12.04, and in Disks in 14.04. 
In 14.04 Disks there is a tiny icon in upper right with more tools and it is there.

---

### Post by tgalati4 on 2014-12-04
```
sudo apt-get install smartmontools
```

Seatools can be found on the Ultimate Boot CD (UBCD)--it boots a mini-DOS session and you can run Seatools from there.

---

### Post by Mark Phelps on 2014-12-05
> Just woundering if it was Seagate Barracuda 

As a matter of fact, they BOTH were!  

Also, I hadn't mentioned that a relative of mine administers a server farm and they had some RAID disks crash on them, and all of them were Seagate Barracuda drives as well.

Seems these have a very limited lifespan and when that's up, they simply crash.

---

### Post by Azyx on 2014-12-08
> **tgalati4 said:**
> ```
sudo apt-get install smartmontools
```

Seatools can be found on the Ultimate Boot CD (UBCD)--it boots a mini-DOS session and you can run Seatools from there.

Thaks tgalati.  UBCD still exist :)

Anyway,  manage to installet on a usb-disk :)

The problem  is that the mouse did notwork  in Seatools 2.23, andI did'n't find how to use keyboard.. Alt and underscored letter?  :( Any way i run Seatools1.x now. .
By the way does this text from Help, this that filling with zeroes are the same as low level format in this app? Try to read the manual now.

[SIZE=2]"Defective drive" can often be revived with a data-destructive zero fill data pattern or a low level format."[/SIZE]

---

### Post by weatherman2 on 2014-12-08
> **Azyx said:**
> [SIZE=2]"Defective drive" can often be revived with a data-destructive zero fill data pattern or a low level format."[/SIZE]

Depends on why the drive has become "defective."  I have found a few cases where, if the drive has some "bad sectors" showing up in S.M.A.R.T. Attributes as "Pending Sectors," then yes, sometimes, zeroing out the whole drive can "revive" it.   In that case, the drive wasn't really "defective."

But many drives simply experience real hardware failures.  In that case - no, you cannot revive them even by zeroing them out.  You have little to lose by trying, however.

---

### Post by Azyx on 2014-12-08
> **weatherman2 said:**
> Depends on why the drive has become "defective."  I have found a few cases where, if the drive has some "bad sectors" showing up in S.M.A.R.T. Attributes as "Pending Sectors," then yes, sometimes, zeroing out the whole drive can "revive" it.   In that case, the drive wasn't really "defective."

But many drives simply experience real hardware failures.  In that case - no, you cannot revive them even by zeroing them out.  You have little to lose by trying, however.

Yes they say also so in Seatools help, some thing like, "if i over write the bad sektor, I may have lesser problems later". The problem was that the mouse-pointer stopped working and I could not select, fix all problems. Then I did not find how to "low level format",  so I run Seatools for Dos v1.12, with 'normal' dos. I don't know if Freedos have bad drivers for usb-mouse or why it does not work in the Seatools 2.23 ?

---

### Post by weatherman2 on 2014-12-08
Don't use Seatools.  Use a boot disk like Parted Magic (still a free version at MajorGeeks), which has disk-erasing tools, or DBAN, a boot disk dedicated to erasing a disk.  (you can do only one pass, not the three passes DBAN does by default for a secure erasure.)

---

### Post by Azyx on 2014-12-10
> **weatherman2 said:**
> Don't use Seatools.  Use a boot disk like Parted Magic (still a free version at MajorGeeks), which has disk-erasing tools, or DBAN, a boot disk dedicated to erasing a disk.  (you can do only one pass, not the three passes DBAN does by default for a secure erasure.)

I still have the problem with SMART, It can't run because it have being to hot, in the past. Failed-self test.  See my thumbnail  in my first post.

Why are not Seatools any good idéa?

---

### Post by weatherman2 on 2014-12-10
If you can get the mouse to work, use Seatools.

If not, try one of the boot disks I suggested.

You won't use S.M.A.R.T. to zero out the drive.

Keep in mind that your disk may in fact be dead - and this is only a last-chance effort to try to save it.

---

### Post by Azyx on 2014-12-10
> **weatherman2 said:**
> If you can get the mouse to work, use Seatools.

If not, try one of the boot disks I suggested.

You won't use S.M.A.R.T. to zero out the drive.

Keep in mind that your disk may in fact be dead - and this is only a last-chance effort to try to save it.

Thanx. It is just under UBCD with FreeDOS and the app SeaTools 2.23 the mouse did not work. SeaTools 1.23 that not demand any mouse work fine. I know that SMART is only test the disk, not format,  but under Ubuntu, the Self-tests stops, with the above message. SeaTools also have rewrite with zoros or low level format, and I wonder why SeaTools  are less good than Parted Magic and  the other boot-disk (DBAN?). Take little time to find a free USB-drive o make a boot-disk.

---

### Post by weatherman2 on 2014-12-10
Use whatever works to write zeros to the disk.  Then check S.M.A.R.T. again.

---

### Post by Azyx on 2014-12-11
Ok. Have fixed problems in SeaTools. After that write zeros to the disk. When I later format and make a new S.M.A.R.T-test in Ubuntu I get, [COLOR=#ff0000]**SELF-TEST FAILED**[/COLOR] And a red flagged post Airflow temperature [COLOR=#ff0000]**Failed in the past.**[/COLOR]  It is also not possible to make a self-test :( and monitor if additional problem get produced. I hade the disk in USB-closer, theg get booth heated AND a glitch in the powersupplie, but have now put it in a desktop with good ventilation.

---

### Post by tgalati4 on 2014-12-11
Perhaps you can upgrade the firmware on the drive, and that would clear out the old SMART parameters.  Or try getting a replacement if it is under warranty.

---

