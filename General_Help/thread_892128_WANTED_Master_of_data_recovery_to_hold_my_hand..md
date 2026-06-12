---
title: "WANTED: Master of data recovery to hold my hand."
date: 2008-08-16
forum: General Help
---

### Post by Biggerbean on 2008-08-16
A young guy is 'helping' me out --and just informed me that he has just formatted a couple of Harddrives with Ubuntu for me.  

ME: "Where'd you get the drives?"

Him: "From your old computer."

Me: "Of %&^* -- those drives weren't empty. They had everything else on them."

I'm going to go find somebody to give me a smoke.

And...I'm really going to need some help now. All my work, my backups, everything was on these THREE newly formatted drives. I have nothing left. 

How's that for 'user error'?

I've been playing with testdisk for a bit but not grabbing anything useful...having never done it before. 

*Signs-- and searches for gun with one bullet in it*

---

### Post by az on 2008-08-16
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Forget about testdisk.  You cannot restore the filesystem on those drives.

You need to file carve the data out.  Use photorec and/or foremost.

---

### Post by aysiu on 2008-08-16
> **az said:**
> [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Forget about testdisk.  You cannot restore the filesystem on those drives.

You need to file carve the data out.  Use photorec and/or foremost.
Don't you need to install *testdisk* to use *photorec*, though?

To the OP, this link should help you out:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

---

### Post by az on 2008-08-16
> **aysiu said:**
> Don't you need to install *testdisk* to use *photorec*, though?

To the OP, this link should help you out:
[http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/](http://www.psychocats.net/ubuntucat/recovering-windows-files-with-a-ubuntu-cd-iii-deleted-files/)

Yes, Mr. smarty-pants.  However, the original poster has already been "playing around" with testdisk, and therefore already has photorec.  Anyhow, that's covered in the DataRecovery page.  Not with endless screenshots and step-by-step detail, of course, but whatever...

---

### Post by aysiu on 2008-08-16
When someone with 12 posts asks for help after someone else has installed Ubuntu and messed things up, I think step-by-step instructions with screenshots are absolutely appropriate.

The only instruction on the wiki with regard to using *photorec* is to run the command ```
sudo photorec
``` That's pretty much the complete opposite of step-by-step.

---

### Post by Biggerbean on 2008-08-17
I gotta say, I'm so impressed with what I've seen of Ubuntu and it's a relief to know that there's help in community out there as I don't think I'd be able to handle this alone.

Especially being totally new to the OS -- an unfamiliar feeling from someone who grew up programming and using dos. 

I'm hesitant to do anything that will write over any of the data that's already been overwritten once. Geez, I have software in Windows that handles file recovery that I've used enough to be comfortable but 1) I want to learn Ubuntu and 2) I don't currently have a wording Windows system 3) I've heard for years that Linux FAR is superior for file recovery and why not put ALL my files, my digital life for 10 years, on the line to check? 

I'm nuts. I have to admit, it being a Saturday night when the "wiping" happened, I've been indulging in the drink to ease the pain.

I'll be sober and on this full force tomorrow. 

Thanks again...

and... I got Photorec up and running but I can't seem to select a directory. I can see the key files I want to recover...but how do I get it to action it? Right off the bat I enter the file system no problem... but every file has a .  or a  .. option... but no actual file names to recover, just folders. Can you recover folders?

What's the deal?

---

### Post by aysiu on 2008-08-17
If your drive has been reformatted, you won't be able to see by browsing what files to recover.

Photorec looks at all the bits and bytes and tries to figure out where the files used to be and then recover them and copy them to a new location.

So you set the recovery drive as the one that's been formatted (yes, Photorec should scan the entire drive) and then you need a backup medium (external hard drive of some kind, even an iPod would work).

Photorec will not do anything else to your already wiped out drive, so you're not putting anything on the line. The only files that will be written will be the recovered files copied to an external drive. The external drive or backup medium is the only thing that will be written to or have changes made to it by Photorec.

See my link above for more details on the process. Let us know if you have any more questions.

---

### Post by Biggerbean on 2008-08-17
Considering I now have 4, yes,**FOUR** drives I need to recover (what Karmic-data-god did I offend?) I am going out to buy a 500GB drive and external enclosure, USB, so I have a place to put all the recovered files. 

I'll be back later tonight!

Oh, and thanks for the description of why I can't see the file names...eases my mind. Phew.

---

### Post by aysiu on 2008-08-17
If you're nervous about any step, please post back here with questions before you execute it. Better to be overly cautious than overly hasty.

---

### Post by candy on 2008-08-18
Hi,
I suggest that you can use some data recovery software to get your dta back!:guitar: I know a safe and wonderful one: EASEUS Data recovery wizard. It can help you to recover you data bact from the fomatted disk:popcorn:. Here is the links:
[http://www.easeus.com/datarecoverywizard/](http://www.easeus.com/datarecoverywizard/)
[http://www.tucows.com/preview/418418](http://www.tucows.com/preview/418418)  

> **Biggerbean said:**
> A young guy is 'helping' me out --and just informed me that he has just formatted a couple of Harddrives with Ubuntu for me.  

ME: "Where'd you get the drives?"

Him: "From your old computer."

Me: "Of %&^* -- those drives weren't empty. They had everything else on them."

I'm going to go find somebody to give me a smoke.

And...I'm really going to need some help now. All my work, my backups, everything was on these THREE newly formatted drives. I have nothing left. 

How's that for 'user error'?

I've been playing with testdisk for a bit but not grabbing anything useful...having never done it before. 

*Signs-- and searches for gun with one bullet in it*

---

### Post by comer on 2008-08-18
Hi,
:popcorn:I think a data recovery software can help you to get your data back. I am just using one, Easeus Data Recovery Wizard. It is safe and easy to use. I used it to get the data I wanted back successfully from the formatted disk.


> **Biggerbean said:**
> A young guy is 'helping' me out --and just informed me that he has just formatted a couple of Harddrives with Ubuntu for me.  

ME: "Where'd you get the drives?"

Him: "From your old computer."

Me: "Of %&^* -- those drives weren't empty. They had everything else on them."

I'm going to go find somebody to give me a smoke.

And...I'm really going to need some help now. All my work, my backups, everything was on these THREE newly formatted drives. I have nothing left. 

How's that for 'user error'?

I've been playing with testdisk for a bit but not grabbing anything useful...having never done it before. 

*Signs-- and searches for gun with one bullet in it*

---

### Post by Biggerbean on 2008-08-18
> **aysiu said:**
> If you're nervous about any step, please post back here with questions before you execute it. Better to be overly cautious than overly hasty.

Thanks! That's much appreciated.  I was unsuccessful at acquiring a Hardrive enclosure today as, being Sunday, the good computer shops were closed and FutureShop wanted, get this, $79 for an enclosure!!! (No, not one with a drive in it, just for the box...sorry, no. I'll wait till tomorrow and pick one up for $15, thank you very much.)

And did I ever have an awesome day! I went out and ran into Brazilian drummers at a street party and danced up a storm during the day. Then I went to a friend's house for a BBQ and ended up on the room watching two hot 20 year old girls make out and grind! Ha ha ha...There's more details but this is a PG forum...but life is good --despite bad-data-karma. :)) 

So let's just say my batteries are recharged and I'm up for the task of getting my data back.  (I was kinda depressed about it when it first happened.)

---

### Post by Loaded.len on 2008-08-18
IMPORTANT STEP: Before you do anything with Photorec or Testdisk, I would recommend doing 

```
dd if=sd(whatever your drive is) of=imagename
```

then mount the image to play with.

More important to do this (or use dd_rescue) if you think there are physical defects with the drive, but all the same - I'd rather have the security of knowing that I can't mess it up anymore than it already is.

---

### Post by az on 2008-08-18
> **Loaded.len said:**
> 
More important to do this (or use dd_rescue) if you think there are physical defects with the drive, 

I recommend gddrescue instead of dd_rescue.  It's faster and better supported.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by benner on 2008-08-18
if you have access to another machine, you may want to download a copy of 'hiren's boot disk' (from mininova or one of the other torrent sites out there). it comes with a million recovery tools and all you have to do is stick the disk into the troubled machine and reboot. if there is one 'safe' hard disk to save to, you should find a number of programs on there to help you. there are also recovery disks out there that are open source and free but not always as easy to use.

---

### Post by Biggerbean on 2008-08-19
My life is too crazy right now. It's been raining like mad here and I attempted to format my new 500GB target drive for all the data. It seems to take forever...and the power went off most of the way through. Twice. 

(Really, is there a goat I can sacrifice to someone to appease them???)

Finally got the drive formatted...and tried to label it. You all probably know what that did. I'm now sitting here waiting for the reformat of that drive to complete. Unreal.

:popcorn:

---

### Post by Biggerbean on 2008-08-19
> **Loaded.len said:**
> IMPORTANT STEP: Before you do anything with Photorec or Testdisk, I would recommend doing 

```
dd if=sd(whatever your drive is) of=imagename
```

then mount the image to play with.

More important to do this (or use dd_rescue) if you think there are physical defects with the drive, but all the same - I'd rather have the security of knowing that I can't mess it up anymore than it already is.

Now that's how this all got started, trying to write an image of a damaged Harddrive. I'm uber nervous about using something like dd again. And I'm not sure exactly *how* I'd *play* with the image after I got it written.

---

### Post by ingeva on 2008-08-19
> **Biggerbean said:**
> Now that's how this all got started, trying to write an image of a damaged Harddrive. I'm uber nervous about using something like dd again. And I'm not sure exactly *how* I'd *play* with the image after I got it written.

My experience will probably discourage you, but here goes:

I tried using photorec to restore files from a disk image.
The files were deleted under Windows, and the disk was repartitioned to the ext3 filesystem, and formatted.

photorec could recover most of the files, but if you'd like to manually inspect 200,000 files with names like "f294380.dll", be my guest.

I think this is more like creating a new problem, than actually and really recovering files. Even their directory is unknown. You could spend the rest of your life figuring it out.

I would either leave this job to someone who had real working tools, or forget about the lost files and start again.

Many years ago, before I learnt how vulnerable the FAT file system was, I tried to repair files from a crashed filesystem. All my attempts only made it worse.
I reckon I lost two week's work. Not really that much, but instead of recovering the files I started programming from scratch (more or less)

After three days the programs were not only restored, but they were better structured and more secure than before, because I had learnt.

Of course, that experience taught me to make backups. I've taken backups nearly every day since then - but never actually needing to restore.

LATEST:
I let the recovery finish in case the situation would look a little better. It took more than an hour, but it did not.
Most of the files were only fragments. For the text files (some of them were actually readable) it looked like each file contained only one disk sector. Some icons were fully recovered, and their file type had been changed to "gif".

I may have missed something but according to this I'd say that recovery from a formatted disk is NOT feasible without MUCH more advanced tools than this.

---

### Post by az on 2008-08-19
> **Biggerbean said:**
> Now that's how this all got started, trying to write an image of a damaged Harddrive. I'm uber nervous about using something like dd again. And I'm not sure exactly *how* I'd *play* with the image after I got it written.

I usually use ddrescue and only ever write to an image.  That way, I don't confuse the source drive with the destiation drive.  Ex:

sudo ddrescue /dev/whatever-the-bad-drive-is destinationimage log

So I never-ever use a device as the second argument.

As for the image, well, the first thing you would want to try is mounting it:

mkdir source
sudo mount -r -o loop image source

If that doesn't throw an error, the image is mounted as the subdirectory in the current directory named "source".  You can name than whatever you like - it's only temporary.  Copy the files you need from that or do whatever else you like.

If the filesystem does not mount, you can copy it and try to repair it.
Use NTFSfix 
or 
try to repair the boot sector:
[http://ubuntu-rescue-remix.org/node/57](http://ubuntu-rescue-remix.org/node/57)

If you can't fix it, you can use file-carving to extract the files.  Now for the four drives that were accidentally formatted, you would skip to this step, since we are not dealing with a hardware problem but a reformatting and the filesystem that you would mount will be empty.

Yes, file-carving produces a lot of files.  No, you cannot use the recovered files as a drop-in replacement for a running system - In any case of data loss, the system should not be put back into production without a reinstallation.  But most of the data you would need to recover should be there.

You can automate the organization of the outputted files by eliminating small sized digital images, renaming the files according to metadata, etc.

What kinds of files do you need to recover from those four formatted drives?

---

### Post by Biggerbean on 2008-08-20
There are a ton of actual files on the disks I want to recover...many many image files --as I was working as a photographer. Also, a bunch of script files (also a professional screenwriter) and some Wordperfect documents I'd really like to get my hands on.

Ok, here's the latest...on one of the drives that I 'carved' I ended up with 714 folders names  recup_dir.1 through recup_dir.714 ...all of which have that box with an x through it and when I try to open it, it says, "The folder contents could not be displayed. You do not have permissions necessary to view the contents of "recup_dir.XXX"."

In the Properties box, it says that I'm not the owner so I can't change these permissions... I tried telling it that, technically, I am the owner as I purchased the drive and still have the receipt, but it was like a stubborn bouncer.

What's the best way to actually view these files?

---

### Post by ingeva on 2008-08-20
> **Biggerbean said:**
> Ok, here's the latest...on one of the drives that I 'carved' I ended up with 714 folders names  recup_dir.1 through recup_dir.714 ...all of which have that box with an x through it and when I try to open it, it says, "The folder contents could not be displayed. You do not have permissions necessary to view the contents of "recup_dir.XXX"."

Same here. I selected the directory containin the "recup" files and typed something like this from terminal:

sudo chown -R inge recup*

Of course, you would replace "inge" with your own username.
This set you as the owner and you'll be able to read the files.
Maybe you're more lucky than me: If the files were not deleted before the formatting, you may be able to see their filenames, and you may be able to see complete files and not only fragments.

---

### Post by Biggerbean on 2008-08-20
Can nothing be easy? Grrrrr. I'm running off a Live CD...so I have to figure out how what the username & password are set to by default.

---

### Post by jerome1232 on 2008-08-20
You can use $USER to own them as the current user
```
sudo chown -R $USER:$USER /<path to folders>/recup*
```

---

### Post by Biggerbean on 2008-08-20
> root@dave-desktop:/home/dave# sudo chown -R dave recup_dir.1
chown: cannot access `recup_dir.1': No such file or directory
root@dave-desktop:/home/dave# sudo su
root@dave-desktop:/home/dave# /dev/sdb1
bash: /dev/sdb1: Permission denied
root@dave-desktop:/home/dave# 


What am I doing wrong now??? And please, please please tell me that once I figure out change the permissions that I won't have to do it manually to all 715 folders. That's about 700 more than I want to do.

---

### Post by Biggerbean on 2008-08-20
> bash: /dev/sdb1: Permission denied
root@dave-desktop:/home/dave# sudo chown -R $dave:$dave /dev/sdb1/photorec*chown: cannot access `/dev/sdb1/photorec*': Not a directory
root@dave-desktop:/home/dave# sudo chown -R $dave:$dave /dev/sdb1/
chown: cannot access `/dev/sdb1/': Not a directory
root@dave-desktop:/home/dave#

I'm feeling like a total moron.

:((

(I switched off of a desktop to a much slower laptop...hoping that would help.) 

The disk I want to recover is sdb1 on this computer (but sdc1 on the desktop...I thought that would be a standard code...shows what I know. Oh wait, that's what this post does.)

I think the suggest code assumed I put the files in a 'photorec' directory but I put it in the root directory...all 715 unopenable, unmoveable (?) files.

---

### Post by jerome1232 on 2008-08-20
actually I just forgot the directories were named recup_dir.xxx and thought they were photorec.xxx

and you would literally type $USER, it's a variable that represents the current user. you could just type dave. 

Well normally you would refer to it by it's mount point not device
the command mount will tell you where sdb1 is mounted at.

```
mount
```
then you would replace the <path to folders> with the mount path.

ie for me (this will be different for you)
```
mount
/dev/sda1 on / type jfs (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type jfs (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jeremy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jeremy)
/dev/sdc1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sdb2 on /media/disk-1 type jfs (rw,nosuid,nodev,uhelper=hal)
**/dev/sdb1 on /media/disk-2 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)**

```
ok so that bold part is sdb1 it's mounted at /media/disk-2 so the code to own it is:

```
sudo chown -R $USER:$USER /media/disk-2/recup_dir*

or

sudo chown -R dave:dave /media/disk-2/recup_dir*
```

edit: once again I missread, sdb1 is the drive to recover not where you put the recovery folders, where did you put the folders at?

---

### Post by Biggerbean on 2008-08-20
> root@dave-desktop:/home/dave# mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/dave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dave)
/dev/sdb1 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)


Here's what happens when I type mount (sorry about the delay, I felt overwhelmed and took a nap!)

And sdb1 is the location where I placed the files that I recovered from photorec and I believe all the files are to be found here: /media/disk/recup_dir.1  through /media/disk/recup_dir.715

I punched in the code that you entered and for the past 5 minutes the Harddrive has been busy flashing away...I'm assuming it's changing the permissions! Yay!

---

### Post by jerome1232 on 2008-08-20
I notice you are running as root, in that case using $USER will just give root ownership again.

Being root you could have browsed through the folders without chown'ing them, but this task doesn't require root so it's best temporarily assume root privileges to give your regular user ownership and run as a regular user while manipulating those files.

---

### Post by Biggerbean on 2008-08-20
OK, it finished. But I still can't view a single file! I'm going through Places--> 500 GB Media --> and seeing all the file folders in the root directory, but all have those permission denied boxes with an 'X' in it.

I'm retrying the chown command using dave:dave instead of $USER:$USER...thought I am wondering why it takes so long to change the permissions!

And yeah, I tried switching to root to see if I could open the files that way...but no, access DE-NIED.

---

### Post by jerome1232 on 2008-08-20
Can you post the output of

```
ls -la /media/disk/
```

---

### Post by Biggerbean on 2008-08-21
BINGO! I'm in! Wonderful. :)

Now, I can see the files and open them! Yay!

Yet...

Dir 1
...it seems that they are almost all text files (f234265.txt) and when I open them, they have pieces of system information (code) in them (in this case, about using phone lines). No files nor names I recognize. Other files have gibberish in them. 

There are also two .gz files that are large (1.5GB & 1MB) but I can't extract the (compressed??) files nor view anything useful here. 

Dir 2
Empty. No files.

Dir 3. 
More txt files of code. Many many of them. One .png file! Opened it and it took forever because it was 18MB and then, it was an image as small as an emoticion :confused:

Dir 4.
500 txt files of code.


Dir 5.
500 txt files of code.


Dir 6
500 txt files of code.


Dir 7
446 txt files of code. 54 Html files! My favorites? No, Linux documentation. 

Dir 8
500 files, mostly text, some .h  or .c --also containing code. I'm starting to see a pattern here.

Dir 9
500 files, mostly text, 10X .h and 2X .c --also containing code. One .pm file 

Dir 10
495 .txt files. 4X .h  and one 10MB .elf file.

I'm going to keep searching but I'm kinda bewildered and wondering how any of this is helpful. What am I even looking for -- I was hoping to get something that remotely resembled the files I had on disk. None of this is familliar at all.

---

### Post by jerome1232 on 2008-08-21
No they will be reneamed in the order they were found

a few tips on organizing the files, of course you'd have to adjust the commands to look in /media/disk and adjust them to search for the types of files your looking for.
from [https://help.ubuntu.com/community/DataRecovery#Cleaning%20up](https://help.ubuntu.com/community/DataRecovery#Cleaning%20up)

> Cleaning up

from:How to recover lost files after you accidentally wipe your hard drive

Sort certain types of files:

sudo mkdir recovery/VID recovery/JPG

find recovery/ -name "*.avi" | xargs -i mv {} recovery/VID/

find recovery/ -name "*.mpg" | xargs -i mv {} recovery/VID/

find recovery/ -name "*.jpg" | xargs -i mv {} recovery/JPG/ 

Eliminate small photos:

sudo mkdir recovery/SMALL

find recovery/JPG/ -name "*.jpg" -size -1024k | xargs -i mv {} recovery/SMALL/ 

Rename jpegs according to exif data:

jhead -n%Y%m%d-%H%M%S *.jpg

Then, remove duplicates.

find /var/recovery/JPG/ -name "*a.jpg" | xargs -i mv {} /var/recovery/JPG/DUPS/



---

### Post by Biggerbean on 2008-08-21
Dir 12
Had an 236MB Mpeg file...'couldnt open data stream'

Dir 24
A 203MB Mpeg...'couldn't determine data stream'

Dir 33
A bunch of large gz files that I couldn't extract. Some html pages of some websites I visited with .jpg thumbnails from the site --sites on data recovery. lol.


There seems to png files that are 10-20MB in size (which seems way too big) and other files that are 10MB with an displayed image of 27X27pixels.

If this is data carving, can I get a piece with some more meat?

---

### Post by ingeva on 2008-08-21
> **Biggerbean said:**
> Can nothing be easy? Grrrrr. I'm running off a Live CD...so I have to figure out how what the username & password are set to by default.

No, evidently it's not supposed to be easy. :)

To the previous poster: When using sudo you still need to know the user password.

Someone will know, for sure! :)

---

### Post by ingeva on 2008-08-21
> **Biggerbean said:**
> What am I doing wrong now??? And please, please please tell me that once I figure out change the permissions that I won't have to do it manually to all 715 folders. That's about 700 more than I want to do.

Read post #19 again.
You don't have to change permissions. All you need to do is change the owner,
and that's done for all the folders and all the files with the ONE command I gave you. You might use $USER as the user name, as stated previously.

Before you write that command, navigate to the directory that contains the recup* directories, and make sure you know the user password. I can't help you there.

---

### Post by ingeva on 2008-08-21
> **Biggerbean said:**
> I'm going to keep searching but I'm kinda bewildered and wondering how any of this is helpful. What am I even looking for -- I was hoping to get something that remotely resembled the files I had on disk. None of this is familliar at all.

Exactly my conclusion. I did this job to check if it would be possible to recover a disk like this. I concluded that it's not. Not with these tools.

If this is very important to you I would send the disks to a well-reputed recovery company and pay the price to have them properly restored.

Of course, the person who did this to you should have to pay you back .... :)

---

### Post by Biggerbean on 2008-08-21
Thanks for the last post on sorting JPGs out of this mess of files!  Will the same process work for OpenOffice files? (What kind of file extension?)

Ok, so I tried out the code and thought it was working but the file directories /recovery/JPG & /recovery/VID remain empty.  

Here's what I did (somewhat edited down...oh, and I had to go install jhead too):

> 
root@dave-desktop:/home/dave# sudo mkdir /recovery/VID recovery/JPG
root@dave-desktop:/home/dave# find recovery/ -name "*.avi |xargs -i mv {} recovery/VD
> find recovery/ -name "*.mpg |xargs -i mv {} recovery/VID
find: warning: Unix filenames usually don't contain slashes (though pathnames do).  That means that '-name *.avi |xargs -i mv {} recovery/VD
find recovery/ -name *.mpg' will probably evaluate to false all the time on this system.  You might find the '-wholename' test more useful, or perhaps '-samefile'.  Alternatively, if you are using GNU grep, you could use 'find ... -print0 | grep -FzZ *.avi |xargs -i mv {} recovery/VD
find recovery/ -name *.mpg'.
root@dave-desktop:/home/dave# find recovery/ -name "*.jpg" | xargs -i mv {} recovery/JPG/ 
root@dave-desktop:/home/dave# find recovery/ -name "*.mpg" | xargs -i mv {} recovery/VID/
root@dave-desktop:/home/dave# find recovery/ -name "*.avi" | xargs -i mv {} recovery/VID/
root@dave-desktop:/home/dave# sudo mkdir recovery/SMALL
root@dave-desktop:/home/dave# find recovery/JPG/ -name "*.jpg" -size -1024k | xargs -i mv {} recovery/SMALL/ 
root@dave-desktop:/home/dave# jhead -n%Y%m%d-%H%M%S *.jpg
The program 'jhead' is currently not installed.  You can install it by typing:
apt-get install jhead
bash: jhead: command not found
root@dave-desktop:/home/dave# sudo apt-get install jhead
Reading package lists... Done
##Yada yada...installed##
root@dave-desktop:/home/dave# jhead -n%Y%m%d-%H%M%S *.jpg
Error : No such file
in file '*.jpg'
root@dave-desktop:~# cd /recovery/JPG
root@dave-desktop:/recovery/JPG# jhead -n%Y%m%d-%H%M%S *.jpg
Error : No such file
in file '*.jpg'


I didn't do the find dubplicates part because I looked at the folders and they were empty.

---

### Post by pacificial on 2008-08-21
Hi, 
Don't panic. I have been faced same problem. You can download demo version of Stellar Phoenix [Linux recovery]("http://www.data-recovery-linux.com") software without any cost. With the help of this you can see preview of recovered files. If you get satisfied in preview then only purchase the software. It will cost few dollars but i am sure you'll get your files back.

Download demo:[http://data-recovery-linux.com/download-linux-data-recovery-software.php](http://data-recovery-linux.com/download-linux-data-recovery-software.php)

---

### Post by az on 2008-08-21
> **Biggerbean said:**
> Thanks for the last post on sorting JPGs out of this mess of files!  Will the same process work for OpenOffice files? (What kind of file extension?)

Openoffice files are zipped xml files.  So in the absence of any filesystem information, they will be recovered as zip files.

If you have a large amount of them you can use some xml tools (xml2 ooo2dbk) and scripting to sort them out.

I have gotten excellent results at finding files using both photorec and foremost.  On a drive with a significant number of jpeg files, you can expect to recover almost all of them.  Even if your filesystem was on the full side, only a handful of them should have been fragmented and therefore not recovered by photorec.  

The fact that your recovery folder does not contain JPEGs doesn't seem typical.  Did you read from the correct device?

Also, if you are dealing with a folder full of small files, it may be quicker to sort through them using a reiser filesystem.  Reiserfs deals with directories filled with thousands of small files better than ext3.  You may find than browsing or changing permissions within a folder with 80k files takes a long time.

It's easy to format your external device to reiserfs before starting the recovery.

As for using proprietary software, my experience is that it sometimes works as well as the free software that is available.  But it usually is not as thorough.  And most of the software ignores non-windows maintream formats like openoffice files and ogg.

---

### Post by Biggerbean on 2008-08-21
So what are these .gz files I see but can't extract?

And for the openoffice files, will they appear as .zip files then?

Yeah, and I'm sure I did something wrong with the sort commands to get files into the JPG directory as nothing appeared there nor did the mpg files, of which I found two manually, appear in the VIDS folder. 

I gotta be honest, I thought Linux was supposed to be the best place for free software and data recovery so there's no way I'm buying anything. I have used software for free that recovers data (and gives them their original file names and folders even!) on both Windows and Mac and I'd do that again WAY before buying some new software for Ubuntu.

From what I've seen, the programs available for Mac & Windows are **far** superior to these Ubuntu offerings. Sorry, I don't mean to bitch, so on with the battle...

It's like pulling teeth.

---

### Post by az on 2008-08-21
> **Biggerbean said:**
> So what are these .gz files I see but can't extract?

Probably garbage.  A false positive.


> **Biggerbean said:**
> 
And for the openoffice files, will they appear as .zip files then?

Yes.

> **Biggerbean said:**
> 

I gotta be honest, I thought Linux was supposed to be the best place for free software and data recovery so there's no way I'm buying anything. I have used software for free that recovers data (and gives them their original file names and folders even!) on both Windows and Mac and I'd do that again WAY before buying some new software for Ubuntu.

From what I've seen, the programs available for Mac & Windows are **far** superior to these Ubuntu offerings. Sorry, I don't mean to bitch, so on with the battle...

It's like pulling teeth.

Using f/loss data recovery tools is not for you.  I would encourage you to find software with a GUI that you can use.  Use what works for you!

From my experience, I seem to have more success using the f/loss tools with a Unix command line than what any of the proprietary tools seems to offer me.   The non-free tools seem to recover only some of what I can get "by hand".

I am not at all opposed to someone writing a GUI for these tools for Ubuntu, and I may even use it if one is written.  But I wouldn't want such a GUI to hold back the amount of data I am able to recover.  So the current state of the software is my preference, but I can understand that it isn't your's.

---

### Post by jerome1232 on 2008-08-21
I think your sort commands should have been (if pwd is /media/disk)
```
find -name "*.jpg" | xargs -i mv {} recovery/jpg
```

That's one thing I liked about foremost is it sorted them by file type for you.

---

