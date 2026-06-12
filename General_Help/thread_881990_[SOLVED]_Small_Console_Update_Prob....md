---
title: "[SOLVED] Small Console Update Prob..."
date: 2008-08-06
forum: General Help
---

### Post by robelliott2125 on 2008-08-06
Hi guys,

Just tried doing ```
sudo apt-get update
```, and getting the following error...

```
W: Duplicate sources.list entry http://archive.canonical.com gutsy/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_gutsy_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

I've tried ```
apt-get update
``` and get: ```
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

```

Hope someone can help with what to do.

Thank you,

---

### Post by GreenN00b on 2008-08-06
Try 
```
sudo apt-get update 
```
for the second issue.

---

### Post by mikjp on 2008-08-06
How does the file /etc/apt/sources.list look like? 

Comment out the duplicate source entry by adding # to the beginning of line (you can edit the file with sudo gedit /etc/apt/sources.list)

Greetings,

m

---

### Post by robelliott2125 on 2008-08-06
> **GreenN00b said:**
> Try 
```
sudo apt-get update 
```
for the second issue.

I've done that, the second issue comes up when doing ```
sudo apt-get update
```.

mikjp, heres my sources.

```
deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt gutsy main

deb http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

```

Since i'm not sure about editing things, if you could show me what to comment out, I would be grateful, would hate to have my pc not boot or work properly.

Thank you,

---

### Post by mb_webguy on 2008-08-06
Ditto GreenN00b.  Error messages given by programs that must be run as root (such as apt-get) assume you know that they must be run as root, and so leave off the "sudo" when suggesting a fix, especially since the exact method of gaining root access can differ from one distribution to the next.  Ubuntu uses "sudo", while others have you actually change to the root user account using "su".

Any time apt-get or other programs that must be run as root give you an error message telling you to execute a command to fix the problem, stick "sudo" in front of the command.

---

### Post by GreenN00b on 2008-08-06
> **mb_webguy said:**
> Ditto GreenN00b.  Error messages given by programs that must be run as root (such as apt-get) assume you know that they must be run as root, and so leave off the "sudo" when suggesting a fix, especially since the exact method of gaining root access can differ from one distribution to the next.  Ubuntu uses "sudo", while others have you actually change to the root user account using "su".

Any time apt-get or other programs that must be run as root give you an error message telling you to execute a command to fix the problem, stick "sudo" in front of the command.

I suggested using sudo because if you attempt to run apt-get update without sudo you get exactly the same error as the second one posted if you run apt-get update without sudo.

Also you can see this is and ubuntu distribution from the first error.

---

### Post by GreenN00b on 2008-08-06
Seems that you have this line two times in the /etc/apt/sources.list
```
deb http://archive.canonical.com/ubuntu gutsy partner
```
Just remove the last one and the warning should disappear.
Make a backup to the file before editing.

---

### Post by mikjp on 2008-08-06
Automatix has screwn your sources.list. This one is twice on the list:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

So comment the second one out by adding a # (with sudo gedit /etc/apt/sources.list), it is third line from the bottom. Then try again: 

sudo apt-get update

Greetings,

mikko

---

### Post by robelliott2125 on 2008-08-06
Guys, at the minute, scratch all the above out...

While awaiting your replies, i restarted my system, and now when I'm trying to log in, its coming up saying that /home/robert is no longer available and if i log in as root / it'll use its own /home file, so i've just loaded the live disk, gone into filesystem to look at my /home file (which was on a seperate drive) and it seems everything has gone...

Any ideas of how to get my home working again, and if i've lost everything?
I've not formatted anything!

****************************

Right, heres a small update...

Whilst still on the live disk, i've trawled Computer for my real files (forgot that filesystem within live, is the disk, not the hdd filesystem).

I've found my original fstab (which i messed about with), and have pulled it up...

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=701b17f6-0c56-4e57-88f7-35fa036c075f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=146682b2-b0d9-4518-846b-4c8bfdc5b082 /home           ext3    defaults        0       2
# /dev/sda5
UUID=01C8B742D8052701 /media/Downloads ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=4AB810A4B8109095 /media/Downloads2 ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb5
UUID=2AAC0871AC083A39 /media/Music    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdd1
UUID=1425B8213EBA3559 /media/Storage  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=C08C3B748C3B63D6 /media/Uploads  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=e3332e29-a984-4f47-b473-f1fbd0c39351 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

My home drive, I stupidly commented out with '#', and when I tried to remove it and save, its saying:

> Could not save the file /media/disk-2/etc/fstab.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

Is there anyway to get around this quickly, so i can get back?

---

### Post by GreenN00b on 2008-08-06
Do you edit /etc/fstab as root?
Also check the permissions of the file to see if it is writable.

---

### Post by robelliott2125 on 2008-08-06
> **GreenN00b said:**
> Do you edit /etc/fstab as root?
Also check the permissions of the file to see if it is writable.

Yeah, I did gksudo gedit /etc/fstab

I was meant to comment out UUID=01C8B742D8052701 /media/Downloads ntfs    defaults,umask=007,gid=46 0

Not my /home folder...

The drive above is constantly throwing my boot sequence out, since its no longer the drive its titled.

At the minute, its currently saying root access only, which sucks while i'm on as live.

I'm such a n0b with linux (purposefully placed n0b, not n00b although i am a n00b).

If i can reboot and do gksudo again within the console, or whatever ctrl, alt and f1 is, then i've written the command down, so i can do it.

Will that work?

---

### Post by robelliott2125 on 2008-08-06
Help!!!!

---

### Post by robelliott2125 on 2008-08-06
Ok, just found this link:  [http://ubuntuforums.org/archive/index.php/t-70872.html](http://ubuntuforums.org/archive/index.php/t-70872.html)

I do have fstab backup, so just need someone to advise me how to use the backup file.

Any ideas???

---

### Post by mb_webguy on 2008-08-06
If you have a backup of the fstab file, simply rename the current fstab file to something else (like "fstab.bad") and change the name of the backup file to "fstab".  Then reboot.

---

### Post by robelliott2125 on 2008-08-06
Hey guys,

Thanks for the help there...

Luckily, once i'd saved it, Ubuntu automagically saved a backup file.
So I shouted to a friend for help on IRC, and he helped me out with

```
rm /etc/fstab
mv /etc/fstab~ /etc/fstab
```

So i'm back on my pc properly now...

Going to backup a tar of my /etc/ folder, so nothing happens again!

Anyway, back to my original prob, i'll do the sources edit, but i just want to check if i should delete the line, or simply comment it out?

Thanks guys.

---

### Post by mikjp on 2008-08-06
> **robelliott2125 said:**
> 
Anyway, back to my original prob, i'll do the sources edit, but i just want to check if i should delete the line, or simply comment it out?

It is up to you. Both will do the trick.

Greetings,

mikko

---

### Post by robelliott2125 on 2008-08-06
> **mikjp said:**
> It is up to you. Both will do the trick.

Greetings,

mikko

Thanks mikko.

My sources is now looking like:

```

deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

#AUTOMATIX REPOS START

# deb http://www.getautomatix.com/apt gutsy main

# deb http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

```

So hopefully this will solve some probs out.

I think thats really this thread all done, so thank you to everyone who helped sort my initial issue out, then my emergency one out!  :guitar::lolflag::guitar:

---

