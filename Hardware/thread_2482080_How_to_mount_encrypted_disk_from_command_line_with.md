---
title: "How to mount encrypted disk from command line with remembered passphrase"
date: 2022-12-19
forum: Hardware
---

### Post by rybodium on 2022-12-19
I need to mount an encrypted (LUKS) USB drive when the system boots. I found this nice article explaining how to do it and it works great.

[https://necromuralist.github.io/posts/mounting-an-encrypted-usb-drive/](https://necromuralist.github.io/posts/mounting-an-encrypted-usb-drive/)

But "udisksctl unlock" requires me to enter the disk passphrase and both commands require my system password. When I log in graphically, gnome is able to remember the passphrase and automount the drive without asking me. I think gnome is just using udisksctl under the hood like the commands in that article. Is it possible to automatically do the thing that gnome does (mount it without asking for passwords) on boot?

---

### Post by TheFu on 2022-12-19
All my LUKS storage require entering either a passphrase or using a challenge/response hardware token.  This is by design.  I'd never look to the Gnome team for anything security related. Call it a bias.

So, the commands to open a LUKS container in cryptsetup, mkdir, mount.  I've only used LVM2 storage, never direct partitions, so I always need to know the LV name.

My notes:
```
# How-to mount my old C720 Luks encrypted storage
# Assume: sdf5 is the partition to be opened (usually logical partition)
# Assume: LVM is used
# sdf                               8:80   0 119.2G  0 disk  
# &#9500;&#9472;sdf1                            8:81   0   243M  0 part  
# &#9500;&#9472;sdf2                            8:82   0     1K  0 part  
# &#9492;&#9472;sdf5                            8:85   0   119G  0 part  
#   &#9492;&#9472;c720 (dm-4)                 252:4    0   119G  0 crypt 
#     &#9500;&#9472;c720--vg-root (dm-5)      252:5    0  51.9G  0 lvm   /mnt/root
#     &#9500;&#9472;c720--vg-lv--swap (dm-6)  252:6    0   4.1G  0 lvm   
#     &#9492;&#9472;c720--vg-lv--Stuff (dm-7) 252:7    0    50G  0 lvm   /mnt/Stuff
# 
# sudo cryptsetup luksOpen /dev/sdf5 c720
# sudo mkdir /mnt/root /mnt/Stuff
# sudo mount /dev/mapper/c720--vg-lv--Stuff /mnt/Stuff
# sudo mount /dev/mapper/c720--vg-root /mnt/root

or

# sudo mount /dev/c720--vg/lv--Stuff /mnt/Stuff
# sudo mount /dev/c720--vg/root /mnt/root

```
Your partition, names, VGs and LVs **will** have different names.  The bad part of my example is that it uses device names, not UUIDs or LABELs which are unique, so there is a manual step to gather the correct information before the 'cryptsetup' open can happen.

There is a crypttab file that get's setup if whole drive encryption is used.  It seems to connect a UUID and LUKS container name together.  I've never added multiple devices to that file, but it would be my guess for how to automate the connection.  But I really don't know.  For me, I don't want encrypted storage unlocked automatically unless I'm specifically entering something to make that happen.  

Of course, there are lots of other good reasons to have storage encrypted, but let it automatically mount if connected on a specific hardware.  ... hummmm.  I vaguely remember the Bald Nerd setting up a LUKS encrypted flash drive that would mount automatically when connected to his laptop, but not to any other system.   

Two videos and 1 text location
* Creating Part1: [Https://youtu.be/vk9Z2_rEUak](Https://youtu.be/vk9Z2_rEUak) (nerds should find this very funny)
* Accessing Part2: [Https://youtu.be/ELEVo6SbYl0](Https://youtu.be/ELEVo6SbYl0) seems to be it.                 
* Text version: [Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it](Https://baldnerd.com/add-a-drive-to-linux-and-encrypt-it)

I haven't looked at them recently, so my memory could be wrong that these are the links. He definitely did do LUKS decryption for a specific system.

---

### Post by rybodium on 2022-12-19
Thanks! That's helpful. In my case I'm just setting up a backup drive and I don't mind it being automatically accessed by the device it's intended to back up.

It just seems like there ought to be a really easy way. Out of the box, if I log into gnome with the USB drive plugged in, it will automatically unlock and mount it using the "remembered" passphrase. I feel like I ought to be able to make that same code run when the system boots without asking for the passphrase by putting a @reboot command in my crontab or something like that. But apparently not with udisksctl.

Either way, the method in the video you shared will work so that solved my problem. Thanks again!

---

### Post by TheFu on 2022-12-19
Remembering the passphrase sorta defeats the purpose for having encrypted storage, doesn't it?  It does for 90% of users.

If you want less good encryption, there are lots of those methods too.

Having backup storage connected to the system all the time is a backup and security failure due to malware these days.  All you need is for all the storage connected to the system or available via CIFS/NFS mounts to be crypto-locked.  This is why my backup server "pulls" backups, never do the clients "push" the data.  This is also why versioned backups are so important.  If one of my clients does 20G of backups over night, I know there's a huge issue and too many files changed, likely due to malware.  I expect 50-500MB of changes a day, unless I did something specific.  My daily backup reports tell me how long a backup took and how much data was changed.

Some examples from last night:
```

=== Time for Backups to regulus === 
StartTime 1671426283.00 (Mon Dec 19 00:04:43 2022)
EndTime 1671426335.20 (Mon Dec 19 00:05:35 2022)
ElapsedTime 52.20 (52.20 seconds)
TotalDestinationSizeChange 10602231 (10.1 MB)


=== Time for Backups to nextcloud === 
StartTime 1671426355.00 (Mon Dec 19 00:05:55 2022)
EndTime 1671426438.52 (Mon Dec 19 00:07:18 2022)
ElapsedTime 83.52 (1 minute 23.52 seconds)
TotalDestinationSizeChange 94263170 (89.9 MB)


=== Time for Backups to pi3 === 
StartTime 1671426445.00 (Mon Dec 19 00:07:25 2022)
EndTime 1671426470.74 (Mon Dec 19 00:07:50 2022)
ElapsedTime 25.74 (25.74 seconds)
TotalDestinationSizeChange 1498469 (1.43 MB)

```
Did I mention that versioned backups are fast?  Obviously, some systems with lots and lots of data take longer, just checking which files changed takes some time ... like my communications server took 23 minutes to backup last night.
```

=== Time for Backups to comm45 === 
StartTime 1671436905.00 (Mon Dec 19 03:01:45 2022)
EndTime 1671438239.58 (Mon Dec 19 03:23:59 2022)
ElapsedTime 1334.58 (22 minutes 14.58 seconds)
TotalDestinationSizeChange 90909771 (86.7 MB)

```
It has lots and lots of files and some are "sparse" files which makes things complicated. I really need to convert that sparse file into a regular file with plenty of space. The project team behind the communications program were being too slick and wanted to break backup tools except their own. They make some files that are 10MB really sparse files of 50GB. You can look up what that does. Basically, accessing the file at almost any level will expand it to 50GB.

---

### Post by Skaperen on 2022-12-19
> Remembering the passphrase sorta defeats the purpose for having encrypted storage, doesn't it?  It does for 90% of users.

indeed!  but if it is a host that remembers it, the "security" (*the quotes here mean it is not true security*) is in making it non-trivial to mount that storage device on other systems, depending on how easy non-trusted users can get the saved passphrase or wedge its automated entry.

i think we need to ask the OP what his/her goal is for having encryption.  if the answer is to make the content unreadable elsewhere then perhaps this is something to do.  maybe he/she has a server app in a container, the only place that can read this mount, that serves restricted access to this data.

if i need to do automated data entry to a program that insists on reading it from [FONT=courier new]/dev/tty[/FONT],  my usual workaround is to run it under [FONT=courier new]screen[/FONT].  if you have never used [FONT=courier new]screen[/FONT] like this, before, all that you need to know is in its man pages.

as to security, be sure you thoroughly understand the big picture and all the fine details of what you are trying to accomplish.  TheFu's point is spot-on.

---

### Post by rybodium on 2022-12-19
I appreciate the higher-security advice but my situation is less critical. I have an older machine running some stuff that it would be inconvenient but not detrimental if we lost. The reason for encrypting it is just so that if someone got physical access to the USB drive they can't get the data. The host machine's main drive is also encrypted so unless they can guess the login password they shouldn't be able to access it. I agree this doesn't protect against malware. This was more of a, hey let's throw a USB drive on there to back up anything important in case the hard drive gets corrupted, and we might as well encrypt it because it's easy to do and offers some limited level of security.

---

### Post by TheFu on 2022-12-19
There's something to be said about encrypting anything portable or any storage that might need warranty returns too.

I'm uncomfortable having different levels of security that can be bypassed by a human mistake just because I'm in a hurry.  I'd rather have no security than fake security, so I'm not confused into a false belief of having more security than I really do.  But everyone needs to decide that for their own situation.

There are many stories of people doing things that remove security or completely defeat the extra hassles for what security they've added.  
I always laugh a little when I hear about someone having an external "backup drive" ... they work on a document for a few hours and email it off to some when it is complete. Then they dutifully "backup" the file to the backup drive.  Excellent, right?   Then they delete the file from the internal disk, because they've "backed it up", so it is safe now.   :|   See the flaw in the method?

---

