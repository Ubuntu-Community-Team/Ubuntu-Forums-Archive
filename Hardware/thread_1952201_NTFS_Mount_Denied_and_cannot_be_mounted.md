---
title: "NTFS Mount Denied and cannot be mounted"
date: 2012-04-03
forum: Hardware
---

### Post by Tonbo1 on 2012-04-03
Greetings!

I have an issue that I'm hoping someone can help me with.  I have a Windows drive that I cannot access in Windows anymore, and have been trying to access it with Ubuntu (10.10 live CD).  I have the drive in an external enclosure.  When I boot up the external drive, I get the error message:

"Error mounting: mount exited with exit code 16: Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command."

I have done my research and found others with a similar problem, but the post always seems to be closed without anything that has helped me.  I am a semi-literate Linux user (i.e., I can get around ok, but I'm no admin), and have been impressed with what Ubuntu has to offer.  I'm hoping that it can impress me even more by helping me access this drive so I can get my music and other files off of it.  :D

Ok, on to the info that may help:

Results of sudo fdisk -l:
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x630052c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60802   488282112    7  HPFS/NTFS

Disk /dev/sdb: 8006 MB, 8006926336 bytes
39 heads, 39 sectors/track, 10281 cylinders
Units = cylinders of 1521 * 512 = 778752 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           6       10282     7815232    c  W95 FAT32 (LBA)

Disk /dev/sdg: 750.2 GB, 750156371968 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           1       89710   720595543+   7  HPFS/NTFS
/dev/sdg2           89711       91201    11976457+   7  HPFS/NTFS

(my guess is that /dev/sdg is my problem child -- it's the right size, and this entry no longer appears when I shut off the external...)

Results of sudo blkid:

/dev/loop0: TYPE="squashfs" 
/dev/loop1: LABEL="casper-rw" UUID="a6216e0e-bb91-9744-9dd4-043231d2e67e" TYPE="ext2" 
/dev/sda1: LABEL="System Reserved" UUID="AAA444F9A444CA11" TYPE="ntfs" 
/dev/sda2: UUID="B614472F1446F243" TYPE="ntfs" 
/dev/sdb1: LABEL="PENDRIVE" UUID="A018-7584" TYPE="vfat" 
/dev/sdg1: LABEL="HP" UUID="54FA0995FA097490" TYPE="ntfs" 
/dev/sdg2: LABEL="FACTORY_IMAGE" UUID="949CA48C9CA46A86" TYPE="ntfs"

Results of cat /etc/fstab:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

If I try to do a umount on /dev/sdg, /dev/sdg1, or /dev/sdg2, I get the error message:  
"umount: /dev/sdg1 is not mounted (according to mtab)"

Ok, that should do it for now....let me know if I can offer up any more information that can shed light on this issue.  I'm hoping that I can get into the drive and copy off the files I need....if I can do that, I think it may very well become a new Linux drive in honor of the OS that saved it.  :D

Thanks in advance!

---

### Post by Bucky Ball on 2012-04-03
Welcome.

To put it simply, the drive needs to be closed/shut down properly. 

Was it yanked out of a Windows machine without using 'Safely remove drive'???

You need to search for how to safely close it. I don't know but sure someone will. 

Here's a start:

[http://au.search.yahoo.com/search?p=NTFS%20volume%20is%20already%20exclusively%20opened&fr=altavista&fr2=sfp]("http://au.search.yahoo.com/search?p=NTFS%20volume%20is%20already%20exclusively%20opened&fr=altavista&fr2=sfp")

---

### Post by Tonbo1 on 2012-04-03
Thanks for the response, Bucky Ball.

The drive was originally my c: drive in my Windows box.  I wouldn't say it was so much yanked out without being properly closed....it more or less decided that it just didn't want to respond one day.  It was having problems with Windows Vista; I would try to run FireFox, and it would just spin....I would try to run simple apps like notepad, and it would hang and require a reboot.  Finally, after one reboot, I got only a black screen.  No Windows login, no boot, no nothing after the BIOS screens.

If I try to access the drive in Windows 7 (i.e. as a slave or secondary drive), Windows won't even boot up.  Turning on the external enclosure with Windows up doesn't do anything either -- the disk is unrecognizable.

I'll keep looking as well.  Like I said, I did quite a bit of research before I posted.  Most of the posts I had seen ended with something like "never mind, I figured it out" or with the OP never providing requested information and the thread just dying.  I haven't yet found anything that says how to force an unmount or otherwise get into a drive that swears it's mounted.

Anyway, thanks again, and hope the additional insight into this issue might be the spark that touches off the flash of genius!

---

### Post by Tonbo1 on 2012-04-06
Anybody else have any suggestions?  I have tried to do a sudo umount with the -f option (including -t NTFS /dev/sdg* as other options), and all I get back is "device is not mounted".  However, if I try to mount the external drive, the system tells me that it is already mounted.

There has got to be a way to get to this thing and shut it down so I can open it again.  Surely it's not locked up so tight that it is useless?

As I've stated, I've seen other cases where people reported similar circumstances, but there have not been any concrete answers.....if you have a magic trick to help in this situation, please let me know!

Thanks!

---

### Post by mikaelcrocker on 2012-04-06
if you `man umount` you should see a couple of options which may help.  I want to say -l (lower case 'L') or -f.  I believe the -f is force, and the -l is for lazy.  I have had instances where the -f switch won't work but the -l switch will do the job.

---

### Post by mikaelcrocker on 2012-04-06
> **mikaelcrocker said:**
> if you `man umount` you should see a couple of options which may help.  I want to say -l (lower case 'L') or -f.  I believe the -f is force, and the -l is for lazy.  I have had instances where the -f switch won't work but the -l switch will do the job.
Sorry one last thing, try deleting from the mount point from fstab, then doing a mount -a to see if that would perhaps do the trick.

---

### Post by NadirPoint on 2012-04-06
It would seem umount is barking up the wrong tree, since Ubuntu never mounted it.  Vista was the last to have it's way with the disk, so I'd probably be looking at it through Windoze with chkdsk and other such Microsoft-type utilities, like booting into their system restore mode to see if Vista can find and (hopefully) repair itself.

I suspect you are looking at a hardware failure anyway, but it's worth a try.

---

### Post by Bucky Ball on 2012-04-07
> **Tonbo1 said:**
> Thanks for the response, Bucky Ball.

The drive was originally my c: drive in my Windows box.  I wouldn't say it was so much yanked out without being properly closed....it more or less decided that it just didn't want to respond one day.  It was having problems with Windows Vista; I would try to run FireFox, and it would just spin....I would try to run simple apps like notepad, and it would hang and require a reboot.  Finally, after one reboot, I got only a black screen.  No Windows login, no boot, no nothing after the BIOS screens.

If I try to access the drive in Windows 7 (i.e. as a slave or secondary drive), Windows won't even boot up.  Turning on the external enclosure with Windows up doesn't do anything either -- the disk is unrecognizable.



Would have been a good idea to put this information in the first post ...

The disk has a boot sector on it, no doubt, and you would be well advised to wipe it if you want to use it as a data drive. The moment it is turned on it will possibly want to boot, but in this case, it sounds like it might have died anyway. 

The further information you've provided makes it unclear which you want to do:

1/ Get the Vista working on the drive again (sounds like it might be dead anyway and a hardware issue), or;
2/ Wipe Vista and use this drive as a data storage device (sounds like it might be dead anyway and a hardware issue).

?

---

### Post by Tonbo1 on 2012-04-10
First of all, a huge THANK YOU to everyone who has responded with input and suggestions.  I was getting really frustrated with all the things that *wouldn't* work, and finally had to realize (and admit!!) I was more or less overlooking the obvious:  I was trying to mount the drives by using a live distro on a thumb drive.  

I figured that this was a problem when I realized that not only could I not see and mount the external hard drive, I couldn't see or mount the INTERNAL (i.e. Windows "C" ) drive either.  /facepalm

Shifted brain mode into "don't be an idiot" mode and backed up my Windows setup, then installed Ubuntu onto a partition on my HD.  Once that fired up, guess what?  You got it.....my main HD was there, and miracle of miracles, so was the external.  Now I am not only happy that I have my data back (and it will be backed up this time, trust me!!), but I am also the proud owner of a Ubuntu/Windows dual boot system.  Life just got a little bit better.

So, thanks again for all the suggestions and advice.  I think you all pointed me in the direction that I needed to go, I just didn't want to take my Windows blinders off and look for other ways to get at the problem.

To others who have a similar problem, give my fix a try:  back up any Win partitions and install Ubuntu onto a partition on your main drive.  You won't regret it, trust me.  Once you have the partition set up and Ubuntu installed, I'd be willing to bet you a dollar or two that your previously unreachable drive mounts up like a champ.

Time to get a cup of coffee and enjoy my new Ubuntu setup.  :D

---

### Post by Bucky Ball on 2012-04-11
Excellent. Enjoy. 

Please mark thread as 'Solved' from Thread tools ... ;)

---

