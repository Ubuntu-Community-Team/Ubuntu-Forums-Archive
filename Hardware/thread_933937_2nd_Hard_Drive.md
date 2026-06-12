---
title: "2nd Hard Drive"
date: 2008-09-30
forum: Hardware
---

### Post by lolmike on 2008-09-30
Okay so, i just installed a second hard drive into my computer as a slave drive.

It was an "old" 120gb (dont remember the make, but if necessary i can go back into the case to find it) from my previous computer. It has windows XP installed on it. The hard drive i use as my master is a sataII and this older one is IDE. Im pretty sure my mobo is compatible to run both at the same time.

My system booted up fine, and I see the hard drive in Places. The old hard drive was partitioned with 5GB recovery space, so I see "114.6 GB Media" and "5.4 GB Media" and im able to open the 5.4 GB and browse around. However when I try to open the 114.6 GB media, an error message displays:
> 
Cannot mount volume.
Unable to mount the volume.

Details
$LogFile indicates and unclean shutdown (0, 0( Failed to mount.dev/sdb2': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: if you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g/dev/sdb2/media/disk-1 -o force    Or add the option to the relevant row in the stc/stab file:  /dev/sdb2/media/disk-1 ntfs-3g force 0 0

(I just typed all that out by hand, there may or may not be typos)

Just so it's made known, the last time the computer was shut down, it was not a "proper" shut down because I had come home from college and smelt a burning in my room, the computer wouldn't turn on, i didn't bother trying to diagnose it since I wanted a new computer anyway (i believe it was just the power supply though).

Anyway, i tried the command in choice 2 of the error message but this came up:

> 
$ mount -t ntfs-3g /dev/sdb2/media/disk-1 -o forcemount: only root can do that


I'm also brand new to Ubuntu (fell in love with it the first day i was on it), this will be my fourth day running it, so im not too familiar with some of the command line scripts, etc..

Any help is much appreciated!

---

### Post by jmate24 on 2008-09-30
Use sudo in front of the mount command. That error is because Windows did not shutdowm the hard drive properly. and if you have a windows machine available you need to run Check Disk on it.

---

### Post by lolmike on 2008-09-30
Thanks for getting the command to work! Like i said, im new to Ubuntu and linux in general. Ive used the sudo command quite a few times in other command line endeavors trying to fix other parts of my system, but never grasped what it was used for.


Anyway, it took the command line, but im still getting the same error when i try to open the volume.

Unfortunately, i dont have a usable windows system available. Is there any way i can run a check disk of any sort on ubuntu?

---

### Post by lolmike on 2008-09-30
bump?

---

### Post by vanadium on 2008-09-30
ntfsfix, part of the ntfsprogs, can fix basic issues with ntfs. (install ntfsprogs using Synaptic Package Manager or, faster, with the command "sudo apt-get install ntfsprogs"). Use "man ntfsfix" to learn about the utility (and its limitations).

If you do not have a Windows system anymore, you should consider reformatting the drive to a linux file format, typically ext3. Make sure you have a backup of the data first. If there are still files you need to recover, you can force -mount the disk, preferably in read-only mode (using the ntfs driver instead of ntfs-3g). It is not at all recommended to just continue using an ntfs disk with the force-mount option. That option is just there for an emergency, to be able to read from a corrupted drive anyway.

---

