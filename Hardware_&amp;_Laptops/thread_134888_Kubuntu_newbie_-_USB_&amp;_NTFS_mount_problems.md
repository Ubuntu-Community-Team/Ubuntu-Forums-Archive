---
title: "Kubuntu newbie - USB &amp; NTFS mount problems"
date: 2006-02-22
forum: Hardware &amp; Laptops
---

### Post by Qwertie on 2006-02-22
Hi everybody.  After trying and failing to switch to Linux five years ago, I'm ready for another try.

I just installed Kubuntu on my computer and I'm optimistic that there's a chance it could replace Windows for most tasks. After some huge motherboard-related problems booting from a CD on a P5GD1 motherboard (see [http://qscribble.blogspot.com/2006/01/beware-asus-p5gd1-vm-motherboard.html]("http://qscribble.blogspot.com/2006/01/beware-asus-p5gd1-vm-motherboard.html")). Kubuntu impressed me with its hardware auto-detection prowess:
- The onboard Ethernet connected to the net seemingly all by itself!
- My Radeon X600 Pro automatically worked and used my monitor's maximum resolution!
- My onboard surround sound *just worked*!  Except that all the volume controls were set to 0% and muted.
- The DVD-RW was automatically mounted.
- Maybe the most pleasant surprise was that both kinds of USB gamepads I own were autodetected and what's more, two special buttons on one of the gamepads work in Linux, whereas those buttons were ignored by the Windows driver.

Windows 2000, conversely, required a driver for most of my devices--and a reboot after every single driver installation, of course :).  Meanwhile, when I tried three Linux distros about five years ago, I couldn't get sound to work and I was lucky if either the video or the LAN worked.  Maybe hardware support has improved... or am I just luckier now?

Problem #1

However, the two NTFS and one FAT32 partitions were not detected.  I'm having a little problem mounting the NTFSs in System Settings, because they always have the permissions "r-x------".  I tried "chmod 555 /mnt/hda5" and got this error message:

chmod: changing permissions of `hda5': Read-only file system

Well, I know NTFS is read-only in Linux, but why can't I make it world-readable?

The FAT32 partition has a similar problem except that the permissions start at "rwxr-xr-x".  chmod 777 gives this:

chmod: changing permissions of `hda2': Operation not permitted

Problem #2

My USB MP3 player / flash drive won't mount (it works in Windows with no driver installation.)  When I plug it in, I get a new Conquerer tab that says:

An error occurred while loading media:/sdb1:
The file or folder media:/sdb1 does not exist.

In System Settings | Disk & Filesystems, I tried mounting it as "VFAT" (writeable) and got the following error:

An error occurred while enabling /mnt/usb.
The system reported: mount: wrong fs type, bad option, bad superblock on /dev/sdb,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

dmesg says:

[4313991.230000] FAT: bogus number of reserved sectors
[4313991.230000] VFS: Can't find a valid FAT filesystem on dev sdb.

One more thing, the "PNY Vibe MP3 player" is misidentified in System Settings as an "Optical Disk".

Ideas?

---

### Post by Qwertie on 2006-02-22
A couple corrections: well, my partitions were detected, they just weren't mounted.

I had been trying to change the permissions of the FAT32 drive as a regular user. As root, I get no error message; however, the chmod 777 doesn't seem to do anything.

---

### Post by LordBug on 2006-02-23
FAT/FAT32/NTFS need the "umask" option on mounting to set the permissions correctly.  You'll want to read up on the umask flags so you can set the permissions correctly for what you want.

---

### Post by Sutekh on 2006-02-23
- Windows filesystem do not suport Linux permissions.  So you cannot chmod the mount folders when the partitions are mounted.  (You *can* chmod the folders when the partitions are *unmounted*, but they will change back when the partitions are re-mounted)

 - I think this is a great link for setting up Windows partitions

[Mounting Windows Partitions In Ubuntu - by [URL="http://www.ubuntuforums.org/member.php?u=21941"]aysiu]("http://www.psychocats.net/linux/mountwindows.php")[/URL]

 - As LordBug points out, it will come down to the setting of **umask**

 - **umask** works opposite to chmod, it *removes* permissions from 777.  So if you want the NTFS folder to have 555 permissions, the umask should be 222.  If you want the FAT partition to have 777 permissions, the umask shoud be 000.  All this is covered in the link above.

---

### Post by Qwertie on 2006-03-01
OK, well it worked after a reboot; the article says to use mount -a which doesn't do anything and doesn't give an error either (I hate when Linux does that.)

Also, for anyone else trying this, you must put a 0 right before the umask, or weird things happen, as I learned!

[QUOTE=Sutekh]- Windows filesystem do not suport Linux permissions.  So you cannot chmod the mount folders[/QUOTE]

That's utterly illogical.  I can't use chmod because it's Windows--therefore I must use umask, the "opposite" of normal permissions?  Give me a break!  If there is a good reason we can't use chmod (which I doubt :P), it has nothing to do with Windows vs. Linux.  After all, it's not like the permission information needs to be stored inside the partition itself.

---

### Post by MightyFlea on 2006-03-01
Hi there!

> **Qwertie]OK, well it worked after a reboot said:**
> 
mount -a means "Mount everything that is set to automount in fstab". So if everything is already mounted, nothing needs to be done.

[quote=Qwertie]That's utterly illogical.  I can't use chmod because it's Windows--therefore I must use umask, the "opposite" of normal permissions?  Give me a break!  If there is a good reason we can't use chmod (which I doubt :P), it has nothing to do with Windows vs. Linux.  After all, it's not like the permission information needs to be stored inside the partition itself.
The point here is not so much "Taking away permissions" versus "Giving permissions" as "Setting permissions at mount time" versus "Setting permissions when the file system is already mounted".
Since FAT does not have permissions, changing file permissions in a mounted file system can not work.
What can be done though is to define which permissions should be used (globally; for all files in the file system) when mounting the file system.

I hope this helps with understanding what's going on..

Cheers,

MightyFlea

---

### Post by Qwertie on 2006-03-02
I think you're saying that you can't change the permissions of a mounted fat partition because the change is global to the whole filesystem and for some reason a global change isn't feasible.  Is that right?  But why isn't it feasible? e.g. is it because you might be removing a "write" permission when someone might be writing a file on that partition?

---

### Post by Sutekh on 2006-03-02
What we are both saying is that you can't chmod a mounted FAT partition, you just can't.  Linux (POSIX) style permissions are not supported by FAT32.  FAT32 was made for Windows not Linux, so you can see why it might not work.

[QUOTE=MightyFlea]The point here is not so much "Taking away permissions" versus "Giving permissions" as "Setting permissions at mount time" versus "Setting permissions when the file system is already mounted".
Since FAT does not have permissions, changing file permissions in a mounted file system can not work.
What can be done though is to define which permissions should be used (globally; for all files in the file system) when mounting the file system.
[/QUOTE]
MightyFlea is saying (and quite correctly too) that you *can* set the global permissions for the FAT partition at the time of mounting using umask.  I'm sorry if I confused the matter by saying umask is the opposite of chmod, MightFlea is much more correct.

---

