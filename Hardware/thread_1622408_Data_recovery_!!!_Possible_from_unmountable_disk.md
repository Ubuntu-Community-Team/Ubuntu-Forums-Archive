---
title: "Data recovery !!! Possible from unmountable disk ???"
date: 2010-11-15
forum: Hardware
---

### Post by WinRiddance on 2010-11-15
Alright, I've spent a good amount of intense hours trying to fix my suddenly non-existent access to my USB backup drive, all to no avail (various posts in the forum). It doesn't look like anyone is going to be able to help with a solution either, so here's (hopefully) another way out of my predicament if someone could help me get there ....

Is it possible, **by using a LiveCD**, to recover data from an _unmountable_ external USB drive? There's no doubt in my mind that the drive is still good. I need to find a way to access that drive somehow, followed by retrieving the contents from that drive which consists of lots of backup data (the only thing that I ever used the drive for). **The drive actually shows up** in places, computer, mount utility, disk utility, and gparted ... but all I ever get are exit code 18 messages which eventually turned into exit code 13 after tons of different things were tried.

**Please, can someone help me** ... step by step as I'm not a Linux/Ubuntu expert ... to retrieve the data from my external USB backup drive which only started preventing my access since I upgraded to Ubuntu 10.10 ??? It's an NTFS partitioned drive. _No, I do not have access to Windows_ in order to fix anything. It has to be either directly from the console with the drive hooked up to the running 10.10 system, or from a LiveCD/Recovery CD of sorts ... ??? Thanks in advance.

---

### Post by ajgreeny on 2010-11-15
I am wondering if it was last used on a windows system and unplugged without going through the "Remove safely" routine which would make it apparently unmountable in ubuntu.  If that is the case, you may need to use a manual "force-mount" command, but if you think this could be the reason for your problem come back again and we'll see what can be done.

---

### Post by WinRiddance on 2010-11-15
Thanks. I've had this disk tied permanently to my Ubuntu setup ... no Windows on the computer at all ... consequently it wouldn't have been possible to accidentally unplug the drive from a Windows system. We did move a few weeks ago but I left the drive plugged into the laptop the entire time while the power was off. When I started my system again, it worked just fine (last week). **It's only since I did that 10.10 upgrade** from within the update manager that this disk stopped being accessible. Tried to use it the day after my upgrade and couldn't ...

At this point I'm willing to try just about anything to get my data off that disk (short of swinging a hammer at it). ;)

---

### Post by matt_symes on 2010-11-15
Hi

I dont want to get in the way of this thread but i have never had an unmountable drive before and i was wondering when you plug the drive in what does dmesg | tail return?

If that is too much of an inconvenience then dont bother, i wont be offended.

Kind regards

---

### Post by ppv on 2010-11-15
Can you use a lower version live cd and access the drive.

---

### Post by WinRiddance on 2010-11-15
Thanks for the suggestions. Here are the other two forum threads (first one is mine, with explanetory screenshots) that I've been dealing with, aside from about a couple of dozen other threads in this and other linux/ubuntu related forums which didn't get me anywhere.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1621539](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1621539)

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1602622](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1602622)

At this point I'm pretty much at wits end, figuring that some type of data recovery solution is probably the only thing that's going to be able to help me.

---

### Post by matt_symes on 2010-11-15
Hi

This command is from linux questions as i have never had a problem mounting drives and is a direct result of the earlier posters suggestion. So if it works all kudos goes to him.

You need to do this from the terminal.

Type "sudo mount /dev/src /mnt/dst -o force" while src & dst should be replaced with the device to be mounted and the mount point respectively.

EDIT: Cheers for the links BTW.

Kind regards

---

### Post by WinRiddance on 2010-11-15
> **matt_symes said:**
> Hi
Type "sudo mount /dev/src /mnt/dst -o force" while src & dst should be replaced with the device to be mounted and the mount point respectively.

EDIT: Cheers for the links BTW.
Kind regards

You're welcome. Herein lies the problem though ... Although this external drive shows up VISUALLY in all of the aforementioned locations, I still can't do anything with that drive because the instant that I try to gain any type of access ... the exit code error message as described in above links follows. Aside from visual symbols the only hard links that I can find to that drive are as root with nautilus, by viewing contents of the dev/disk folder. There I can also see references to that external drive by looking at folders such as dev/disk/by-id ... dev/disk/by-uuid ... dev/disk/by-label, and so on. It says the same thing everywhere in the properties though ... VOLUME UNKNOWN.

Granted, I can go as far as sudo mount /dev/sdb1 ... but I can't go beyond that since this external drive _doesn't show up_ in either mnt or the media locations, as it normally would. Least I don't know **how** I would have to finish that command in order to actually make it work. I tried to use just the direct path to the /dev/sdb1 with the force option ... but that generated this error:

> winriddance@winriddance-laptop:~$ sudo mount /dev/sdb1 -o force
[sudo] password for winriddance: 
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab
winriddance@winriddance-laptop:~$ I tried your suggestion earlier by the way (saw that thread too) and ended up with a new folder, entitled sdb1, within my media location. But when I clicked on it there was nothing inside and based on the remaining file space that I saw in nautilus I could tell that it was just an empty folder within my current system, as opposed to linking somehow to that other drive, the one with the data that I can't access. This is driving me batty for sure .... :( :confused: :mad:

---

### Post by matt_symes on 2010-11-15
Hi,

Yes i see the problem. Unfortunately i have never had it so i have never tried to fix it. 

Well quite a number of clever people have had a go at this and no luck so far (Just read all the links you sent from start to finish) and they have exhausted all my suggestions between them and more.

I am at a bit of a loss at the moment. I am very sorry.

I have you considered trying on one of the IRC channels? (#ubuntu on freenode) Someone there might have come across this and fixed it.

Good luck, eh?

Kind regards

---

### Post by ppv on 2010-11-15
> **WinRiddance said:**
> You're welcome. Herein lies the problem though ... Although this external drive shows up VISUALLY in all of the aforementioned locations, I still can't do anything with that drive because the instant that I try to gain any type of access ... the exit code error message as described in above links follows. Aside from visual symbols the only hard links that I can find to that drive are as root with nautilus, by viewing contents of the dev/disk folder. There I can also see references to that external drive by looking at folders such as dev/disk/by-id ... dev/disk/by-uuid ... dev/disk/by-label, and so on. It says the same thing everywhere in the properties though ... VOLUME UNKNOWN.

Granted, I can go as far as sudo mount /dev/sdb1 ... but I can't go beyond that since this external drive _doesn't show up_ in either mnt or the media locations, as it normally would. Least I don't know **how** I would have to finish that command in order to actually make it work. I tried to use just the direct path to the /dev/sdb1 with the force option ... but that generated this error:

I tried your suggestion earlier by the way (saw that thread too) and ended up with a new folder, entitled sdb1, within my media location. But when I clicked on it there was nothing inside and based on the remaining file space that I saw in nautilus I could tell that it was just an empty folder within my current system, as opposed to linking somehow to that other drive, the one with the data that I can't access. This is driving me batty for sure .... :( :confused: :mad:




You can create a dir in /media by a name of your choice and then use that in the mount command.


Are the partitions getting detected properly in the disk utilities and other places.

---

### Post by matt_symes on 2010-11-15
Hi

pvv read the links in his post that had the links. Please dont think i am having a go at you, i am not.

Kind regards

---

### Post by WinRiddance on 2010-11-15
Alright, I went ahead and created a folder in media, entitled:  folder_tosdb1

Then I went ahead and tried using this command here:
> sudo mount /dev/sdb1 /media/folder_tosdb1 -o forceIn return I received the error:
> Failed to open ntfs attribute: No such file or directory
Failed to mount '/dev/sdb1': No such file or directoryNo matter what I do, that's pretty much as far as I can get. I even tried an old 64bit Ubuntu 9.04 LiveCD ... used sudo chown to get access across to all of my files, my WEP key for internet access, and Gparted to view that external drive. I've attached the screenshots that I copied over to my primary system drive.

**At this point I'm going to start looking for some MBR recovery software**. There's got to be something out there that will permit me to restore that entire backup disk back to whatever state it was ... before I did that Ubuntu 10.10 upgrade. I'm certain that I can format and continue to use that drive, but that means losing all of my backup data. Not ready to give everything up though, some files date back almost 10 years ...

.

---

### Post by a quarter past seven on 2010-11-15
have you tried using a live cd and seeing if that gives you access or using testdisk as a live cd?

---

### Post by matt_symes on 2010-11-15
Hi

If it's not mounted to /dev then sysfs cannot read it and it will also be no good under /sys/

. But i have to sleep so....

Unless someone knows better?

Kind regards

---

### Post by WinRiddance on 2010-11-15
> **a quarter past seven said:**
> have you tried using a live cd and seeing if that gives you access or using testdisk as a live cd?

Hi there. Didn't you look at those screenshots or my comments right above your question? Those images were taken directly from the LiveCD after I gave myself access to my system.

@matt_symes

> If it's not mounted to /dev then sysfs cannot read it and it will also be no good under /sys/

Well, I know ... that's kind'a what I've been getting at ... the fact that I can see that external drive in several places without actually ever being able to access anything that might be contained there. That's why I'm thinking that only some kind of MBR recovery software is going to be able to help me access that external drive, once I recover/repair the old records within that drive. Not sure if that's even possible since the drive was never actually used as a boot device, but I'll give it a shot and return back here to let everyone know how it went. Thanks to everyone who tried to help.

---

### Post by Animal X on 2010-11-15
I noticed you wrote "Is it possible to use a Live CD...?"....I would've popped a live cd in there before even posting just to see. Also I noticed you wrote "upgraded" - I hear a fresh install is always best, upgrades often seem to run into snags.

---

### Post by sunnynice on 2010-11-15
> **Animal X said:**
> I noticed you wrote "Is it possible to use a Live CD...?"....I would've popped a live cd in there before even posting just to see. Also I noticed you wrote "upgraded" - I hear a fresh install is always best, upgrades often seem to run into snags.
 really? what about the fresh install?

---

### Post by WinRiddance on 2010-11-17
Eventually I did use the LiveCD which got me nowhere as I can only use Gparted with the LiveCD. I don't have enough knowledge about Linux/Ubuntu to mess around too much with the console. Gparted provided with no additional information that I wasn't able to find here or with the console. (did you notice my LiveCD screenshots?)

As it stands, my problems have gotten significantly worse ... but that's another thread.

YES, I agree, I've always done a fresh install before. This was the first time in 4 versions of Ubuntu that I tried to use the upgrade option directly from the software update manager. And I only did that because some other people whom I knew to have problems before, ended up recently doing their upgrade the same way without any problems (no clean install needed). So I figured that perhaps all of the bugs had been ironed out by now ....

---

### Post by WinRiddance on 2010-12-11
**Final summary ...**

In the end I managed to use [testdisk and photorec (photorec is part of testdisk)]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") to recover some of the data from the previously unmountable disk in question. Photorec restores not only photos, but also various other multimedia files, as well as text, php, and html files. Perhaps others too, but I haven't had time to go through the 200+ restore folders yet (each with 500 files).

[For additional testdisk/photorec information, follow this link!]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") What I really did not like about testdisk at all, is that it is only possible to restore _onto your existing_ home/user drive. The problem with this, in particular for users with partitioned systems, is that such users often keep their system files and home directory on a fairly small partition, with their personal data files such as videos, musik, photo albums, etc. on a separate, larger partition, thereby making a data recovery effort of those files much more daunting.

The disk itself is still fine. Re-formatted the drive and then re-partitioned it. Checking the disk for errors ... revealed none at all. There's still no doubt in my mind that my upgrade from Ubuntu 10.04 to Ubuntu 10.10 had something to do with my problems since the direct upgrade via the Upgrade Manager completely hosed my fstab settings ... which also had references to that particular drive. All in all a horrible experience. **I never plan on upgrading directly from within the Upgrade Manager again** !!! My previous four upgrades (all fresh installs) went flawless !!!

Now I'm using _simple backup_ and _simple restore_ (available from the Ubuntu software center), to keep backups of everything relevant for 7 days, 4 weeks, and once per month for an entire year, all done automatically. Should have looked into that long ago ... as opposed to making my own random backups. **[Detailed info. and screenshots available by clicking right here!]("https://help.ubuntu.com/community/BackupYourSystem/SimpleBackupSuite")**

---

### Post by Animal X on 2011-02-13
> **sunnynice said:**
> really? what about the fresh install?

i thought u said it was a usb backup drive, unless you mean from the disk itself? choose live demo mode(try ubuntu with no changes?) , even a live cd of gparted, the point is to use a different os to try and gain access....i only asked because i jammed up a usb data drive somehow and linux wouldn't mount it or see files on, but it would show up in gparted with errors(the drive was ntfs), but it told me to use windows chckdsk and that eventually fixed mine...hoever i see you're way past that now :/

---

