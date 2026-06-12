---
title: "RAID and HD Thrashing"
date: 2009-05-21
forum: Hardware
---

### Post by misterfixit on 2009-05-21
RAID 1 set up on AMD 64 system.  There is a lot of thrashing of the HD system when changing from one screen to another.  Also, it is most evident when Firefox is running.  Firefox error log has only comments about various web page construction faults.  System log has lots of comments but I am not sure where to look for specific items which point to HD, RAID and dmraid operation.

FYI, I have never been able to get fstab settings to mount the RAID array and have to use a desktop command widget to do this:

gksu mount /dev/mapper/nvidia_jfgfbeha1 /media/RAID-1


Request assistance.

TIA

Dave

---

### Post by misterfixit on 2009-05-21
Yoo Hoo out there .. Bump Anyone?  Bumpity:D-bump-bump-a-bump:p

---

### Post by unclejac on 2009-05-22
Hi I am in the process of setting up a RAID1 on two seperate disks (non boot) on my Ubuntu 9.04 AMD64 box.

I am just about ready to mount, and was looking for some inspiration as they don't look formated yet. 

When you say there is a lot of thrashing of the HDD system do you mean you can hear the disk writing constantly? I take it this RAID1 is of your Ubuntu boot/filesystem ?  

Ok since dmraid seems to think my raid is active I am going to try putting a line into the FSTAB, I'll let you know how it goes . . . ;)

---

### Post by unclejac on 2009-05-22
Ok I solved my issue and the auto mounting problem too. Maybe you can add a similar line to your fstab?

Have a look at my ramblings here on a separate thread here:

[**Raid Format**]("http://ubuntuforums.org/showthread.php?t=1167307")

It seems sometimes you just need to talk out a problem and you figure it out yourself hehe ;)

---

### Post by misterfixit on 2009-05-22
> **unclejac said:**
> Hi I am in the process of setting up a RAID1 on two seperate disks (non boot) on my Ubuntu 9.04 AMD64 box.

I am just about ready to mount, and was looking for some inspiration as they don't look formated yet. 

When you say there is a lot of thrashing of the HDD system do you mean you can hear the disk writing constantly? I take it this RAID1 is of your Ubuntu boot/filesystem ?  

Ok since dmraid seems to think my raid is active I am going to try putting a line into the FSTAB, I'll let you know how it goes . . . ;)

Yes, writing for several minutes at a time.  I've noticed that when I open Firefox, the thrashing process gets very intense.  The FF error log only shows a bunch of incompatibility errors with the usual culprits -- crappy Windows only web sites.

I did notice on other thing.  I installed Vidalia and tor and when the tor daemon loaded, there was a LOT of activity that went on forever.  I finally KILLed the processes and the noise went away.

---

### Post by unclejac on 2009-05-24
> **misterfixit said:**
>   I've noticed that when I open Firefox, the thrashing process gets very intense.  
 
I installed Vidalia and tor and when the tor daemon loaded, there was a LOT of activity that went on forever.  I finally KILLed the processes and the noise went away.

How long you had the Raid set up for and has it always made so much noise?

I'm guessing if the Raid is a backup of your boot / filsystem, then evertime an app or such is loaded and writing something to disk the raid will be copying it to the other disk. Which I guess for a filesystem could be a fair percentage of the time.

---

### Post by misterfixit on 2009-05-24
> **unclejac said:**
> How long you had the Raid set up for and has it always made so much noise?

I'm guessing if the Raid is a backup of your boot / filsystem, then evertime an app or such is loaded and writing something to disk the raid will be copying it to the other disk. Which I guess for a filesystem could be a fair percentage of the time.

Thanks for the reply.

RAID-1 consists of two 750GB drives which hold the following directories (which should be self-explanatory):

/Documents
/Music
/Video
/Photogaphy
/eBooks
/Linux_References

/home/dave exists on a separate 10K RPM SATA Drive of 36GB.  The rest of the Ubuntu system is installed on that 36GB drive.

The RAID system has been working fine for the past two months with zero downtime and 100% health.

I am now starting to have serious thoughts that perhaps is IS NOT the RAID array which is thrashing, but the 10K RPM drive with /home on it.

If Firefox and Thunderbird both live on /home/dave; and those two are the aps which I use the mot, and must have huge data files with old emails, and all of the usual crap that a web browser collect ... maybe, just maybe, that thrashing noise if coming from the 10K drive trying to do something with FF or TB.

I know for sure that without either FF or TB loaded, the drive is very quiet unless there is some action that I command.  For instance, when I am playing Solitaire, the HD isn't doing anything because the whole Solitaire ap is playing in RAM.  But, when I call Open Office and load a document from the /Documents folder over on the RAID, there is a lot busy sounds from the drive.

My only real complaint is that the access time has become quite slow for TB and FF and for any other application when TB and FF are loaded.  Ordinarily I have 5 or 6 separate screens open, one with TB, one with FF, one with Solitaire, one with a music app and one with the System Monitor open.  That way I just use my middle thumb wheel to glide between screens.

What do you think?

Dave

---

### Post by misterfixit on 2009-05-28
Well, what ever it was that was causing the thrashing, I fixed.  I discovered that it was the 36GB 10,000 rpm SATA drive which was making all the noise.  I reinstalled the HD on a thin rubber mat which I cut to fit.  Noise problem solved.

The 10K RPM drive was still thrashing, but I fixed that too.  I did the usual "when you can't find the answer, Do Like You Do With Windows".  I repartitioned the HD and I did a clean install of Ubuntu.  What ever it was that was causing the problem went away.  See, I did learn something from being a Windows users for years and years!

I suspect that there was a bit of crapware which was causing a load of swapping in and out in spite of my 8GB of RAM.  Anyway, problem solved .. and thanks to all on the forum who helped me out.

---

