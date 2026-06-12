---
title: "exfat issues &quot;real size does not equal to size&quot;"
date: 2015-01-22
forum: Hardware
---

### Post by tcll5850 on 2015-01-22
```
Error mounting /dev/sdk1 at /media/tcll/Terabyte Data: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdk1" "/media/tcll/Terabyte Data"' exited with non-zero exit status 1:
stdout: `FUSE exfat 1.0.1
'
stderr: `ERROR: `pagefile.sys' real size does not equal to size (0 != 4025626624).'
```

what can I do to fix??

windows is out because I formatted my windows HDD to install linux.

EDIT:
I have a VM running WinXP...
is there a way I can mount the drive with the VM??

---

### Post by weatherman2 on 2015-01-22
[http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04](http://askubuntu.com/questions/451364/how-to-enable-exfat-in-ubuntu-14-04)

Looks like the poster there with the same problem needed to run the exfatfsck command - you might try that.  (Called "fsck_exfat" on a Mac apparently.)

---

### Post by tcll5850 on 2015-01-22
kk, just tried that... got nowhere... heh

```
tcll@tcll-AY589AAR-ABA-a4317c:~$ sudo exfatfsck -v /dev/sdk1
exfatfsck 1.0.1
Copyright (C) 2011-2013  Andrew Nayenko

tcll@tcll-AY589AAR-ABA-a4317c:~$ sudo mount -t exfat /dev/sdk1 /media/exfat
FUSE exfat 1.0.1
ERROR: `pagefile.sys' real size does not equal to size (0 != 4025626624).

tcll@tcll-AY589AAR-ABA-a4317c:~$ 
```

EDIT:
just read the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/fuse-exfat/+bug/1253582](https://bugs.launchpad.net/ubuntu/+source/fuse-exfat/+bug/1253582)

at least I'm relieved to know it's reported, but now I'm dealing with an impatient family (including myself) who have been waiting over 3 months for something to happen.
I'm a little disappointed this report is almost a year old and still has nobody assigned to it...

I desperately need this because I can't help anyone until I can clear off my main HDD.


reading up on it, that exfatfsck only reports errors... it doesn't fix them...
know of any utilities that that may help??

I havn't found any yet >_>

---

### Post by weatherman2 on 2015-01-22
I'd run chkdsk in Windows then.  You can download a Windows 7 boot disk legally (need a product key to install but you won't be doing that) from Digital River.  (Search the web for "Windows 7 digital river")  You can download and "burn" the big ISO to a large USB thumb drive, then boot that, then dump into a command prompt and you should be able to run chkdsk.  I assume in Windows 7 exFat support is built in even on the boot disk.

Or if you have a Windows 7 boot disk already, just use that if you have a CD/DVD drive.

---

### Post by tcll5850 on 2015-01-23
yea... ChkDsk with Win7 didn't fix... I still get the issue.
for once I'm glad I didn't snap a Win7 disk in half :P
lol
at least it's an early x86 distro so it doesn't come pre-built with the MS RAT... heh

no, in order to do what I wanted, I had to hack and load HxD with CMD by doing:
```

C:/> pagefile.sys

Open With: notepad.exe

open file: browse for HxD.exe and run

open file (multi-select): copy C:/ paste in D:/1TB_exfat2/

```

I tried with xcopy and all that did was nearly break my NTFS drive.
(created directory couldn't be read in linux)


yes, I had another 1TB drive, but never used it because NTFS is worse than ExFAT and kills HDDs.
(I have about 12 out of 17 dead HDDs that died because of NTFS)
^ I broke the rest, except one, which just stopped receiving power entirely... lol

so thanks to that, I can now format both to Ext4 which seems to be recommended in Linux.
though I hear Ext2 is better...


that's pretty sad to have to go to that length with no resolve other than using Windows to transfer your data to another drive.

what's even sadder is that linux is older than windows and still doesn't support it... >3<
... sorry... just blowing off steam to know that filthy MS can do more than sparkly linux in terms of hardware support.

---

### Post by yancek on 2015-01-23
> that's pretty sad to have to go to that length with no resolve other than using Windows to transfer your data to another drive.

You're using microsoft proprietary filesystesms.  Why would you expect Linux to do more than the company which created these proprietary systems?
If you want a Linux system to copy successfully, try using a Linux filesystem.  You do know that a standard windows doesn't even recognize a Linux filesystem much less read or write to it.

> what's even sadder is that linux is older than windows and still doesn't support it... 

What!  I don't know where you get your information.  Linux was first released in 1991, windows first release was 1985!

---

### Post by tcll5850 on 2015-01-23
> **yancek said:**
> You're using microsoft proprietary filesystesms.  Why would you expect Linux to do more than the company which created these proprietary systems?
If you want a Linux system to copy successfully, try using a Linux filesystem.  You do know that a standard windows doesn't even recognize a Linux filesystem much less read or write to it.
nono... I used win7 xcopy which didn't do a good job and nearly broke my HDD...

standard copy/paste actions worked perfectly...

still, my argument is that I was expecting MS file-systems to work perfectly on linux (excluding GPT disks as that's rather new)
why?
because of the wide software support linux already has, which is more than amazing. ;)

> **yancek said:**
> What!  I don't know where you get your information.  Linux was first released in 1991, windows first release was 1985!

I stand corrected... sorry :P

go figure, both of those years have a valid reference XD
1991 - my birth-year
1985 - the song 1985


I'm not mad ok, even though I sound like it.
I am disappointed though... heh

especially by coming into linux after hearing it had a wide user-base.


but hey, nothing bad enough to get on the defensive over, ok. :)

---

### Post by weatherman2 on 2015-01-23
I have found Linux support for Windows NTFS and FAT32 file systems to be outstanding.  exFat is newer and not as well supported in my experience.  But I don't blame "Linux" - I blame Microsoft.  I don't expect any Linux support for weird Windows file system issues such as you encountered.

I prefer ext4 as a native Linux file system.  ext2 has no journaling (ext3 is ext2 with journaling).  Journaling gives you more ability to recover from an error condition.  There are cases you might want to use ext2 (e.g. on a thumbdrive, where journaling would force more reads/writes to the flash cells) but I'm not sure why you would use it on a regular hard drive.

---

### Post by yancek on 2015-01-23
> especially by coming into linux after hearing it had a wide user-base.

It's impossible to know what the actual user-base is as far as personal/home computer for Linux since it is free to download and from so many sources there is no way to keep an accurate count.  One person could download and install on 10 or 100 or more computers.  100 people could download and never get it installed.  No way to get an accurate count.  The people who try to get a count usually estimat from 1-5% of personal computer using some form of Linux.

As far as corporate users, that's a different story.  The link below is just one with some information on which use Linux.

[http://www.tecmint.com/big-companies-and-devices-running-on-gnulinux/](http://www.tecmint.com/big-companies-and-devices-running-on-gnulinux/)

I'd also agree with the statement by weatherman2.  It's amazing what Linux developers have done to allow people to access the proprietary windows systems, and at no or little cost to Linux end users.  Personally, given the hundreds of billions of dollars in income microsoft has made, I would expect their product to be a lot better than it is.

Have fun with your Linux.

---

### Post by tcll5850 on 2015-01-23
thanks chromium for randomly going unresponsive and eating all of my RAM, I just lost my post because I had to force-close...
(this issue happens quite often actually, but this is the first time it's been destructive)
^ usually it eats my RAM and swap (8GB) on startup

anyways... I'll type everything again, but not as detailed 9_9

> **weatherman2 said:**
> exFat is newer and not as well supported in my experience.  But I don't blame "Linux" - I blame Microsoft.

I thought ExFAT was Win95-ish >.>
but if it's XP-ish, I can make an exception...

yes, it's MS's fault for breaking support, but this ExFAT drive in question comes from XP x86.
and with the fact that this has happened to SO MANY PEOPLE, I kinda have to say WTF to the devs.

don't get me wrong, I know coding is hard, especially in C where it's just overwhelmingly hard...

but do consider I'm working on a few projects that are about 3x to 10x harder in a MUCH simpler and cross platform language.
(where I say 10x harder may be a bit light, but that particular project is a recompiler with my own [node-based recompilation language](https://picasaweb.google.com/110263988688421174390/UMCSL))
^ this language is in development for a future project of a [current project](https://picasaweb.google.com/110263988688421174390/UMC)

so yea, do take my griping with a grain of salt, because ExFAT support to me looks extremely simple to add to linux. ;)
do take note, I'm in no position to fill in the position of linux development as I don't know C...
I understand quite a bit (like 75% roughly) of how C works (with a visual understanding of the logic behind the code rather than the code itself)...

no, my area of programming is python27

EDIT:
btw, about UMCSL, those images are EXTREMELY outdated...
I've added much better pointer, function, and all-round updated support here:
[http://tcll5850.proboards.com/thread/271/umcsl](http://tcll5850.proboards.com/thread/271/umcsl)
^note: you don't call a function object directly, you store or reference it and THEN call it.

all I really have left to design on this is class structuring among various C complexities such as structs and enums... heh
(it would fit with the types system for pointers)

---

### Post by tcll5850 on 2015-01-23
> **yancek said:**
> It's impossible to know what the actual user-base is as far as personal/home computer for Linux since it is free to download and from so many sources there is no way to keep an accurate count.  One person could download and install on 10 or 100 or more computers.  100 people could download and never get it installed.  No way to get an accurate count.  The people who try to get a count usually estimat from 1-5% of personal computer using some form of Linux.

As far as corporate users, that's a different story.  The link below is just one with some information on which use Linux.

[http://www.tecmint.com/big-companies-and-devices-running-on-gnulinux/](http://www.tecmint.com/big-companies-and-devices-running-on-gnulinux/)
alright :)

yea, like I said, I was only told about the user base, and considering what I've been hearing recently, I guess I've been over-thinking the size a bit... heh

> **yancek said:**
> I'd also agree with the statement by weatherman2.  It's amazing what Linux developers have done to allow people to access the proprietary windows systems, and at no or little cost to Linux end users.  Personally, given the hundreds of billions of dollars in income microsoft has made, I would expect their product to be a lot better than it is.

Have fun with your Linux.

don't get me wrong, I did call linux "sparkly" and windows (or MS) "filthy" :P

indeed, I love what developers HAVE done, I'll take linux over windows any day ;)
especially now that they've integrated a RAT into their kernels of Vista? through 8 and quite possibly 10 which gives them a big red button to control their users.
I do believe google cracked this RAT as MS seems to be putting up quite a fuss about it XD
MS said they'd fix it, but if it's really the RAT, I highly doubt it'll actually be fixed...
I already know MS wants to control everyone, just look at the initial release of the XBox One.

I only use WinXP64 as my main WinOS if ever needed, and with all the complaints arousing about the new OS's, WinXP might just come back from the dead.
but if MS taints it with their RAT, they can be certain I'm not gonna be testing on it.

yes, I'm a white-hat win hacker if you havn't guessed :P
I just do cool stuff such as DX11 support in WinXP, or make a 3D world out of my desktop environment. ;)
(that's only to give an idea, I'm not at that level of hacking, but I'm getting there)
^ this is MUUUUCH easier to do on linux, so much so that I can do it with PyGLFW =D


so yea, I really have nothing against linux developers ;)
but when nothing's done for a year on something that looks extremely simple to fix, that's when I have to complain... heh
no hard feelings or anything, I'm always a nice guy. :)


EDIT:
btw, I never thanked anyone for there help >.>

major thanks indeed =)
I would've never thought to use my Win7 disk to copy my data with :)

---

