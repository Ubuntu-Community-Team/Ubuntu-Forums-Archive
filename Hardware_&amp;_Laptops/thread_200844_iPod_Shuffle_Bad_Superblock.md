---
title: "iPod Shuffle: Bad Superblock?"
date: 2006-06-20
forum: Hardware &amp; Laptops
---

### Post by hizaguchi on 2006-06-20
This morning I added some music to my iPod Shuffle with iTunes on my wife's Mac.  Evidently something went wrong, because I took it to work with me and when I tried to play music I just got blinking lights.

Plugged it into my Windows PC at work (it's fat32 formatted) and it recognized the drive but not that it was my iPod like it normally does.  It said there was an I/O error.  I also couldn't get to the "properties" dialog to format the Shuffle or anything.

Brought it home and stuck it back in my wife's Mac.  Didn't mount.  Dmesg complained about an error, but I don't remember what it said and she gets nervous when I use the terminal, so I didn't check again.

Stuck it in my FreeBSD machine, dmesg said there was an error and the USB hub had been disabled.

Stuck it in my Linux machine and tried to mount.  (Didn't show up on fdisk -l, so I guessed /dev/sda, which was right.)  Wouldn't mount.  Tried fdisk and cfdisk, both complained they couldn't read the drive.  Tried fsck (I think... I'm getting confused by all I've gone though at this point) and it (or whatever program that was) said there was a bad superblock at 0 and told me where some alternatives were located.  So finally I tried mkfs.vfat and it said "read 512kb, failed at 0" or something to further rub in the fact that something's wrong with the first sector of the disk, and that it wasn't going to do jack about it.

So here I am.  What can I do from here?  I don't care about any of the information on the iPod.  I just want to get it working again.  Any ideas?  Maybe some of Windows' tools can fix it?  If not, what can I do?

---

### Post by hizaguchi on 2006-06-21
Update:  Downloaded the iPod updater for Windows.  It can't mount the iPod (shocker, I know), so it can't fix it.  None of the Windows utilities will scan, repair, or format the disk.  chkdsk says "cannot open volume for direct access", and format says "error in IOCTL call".  I'm about ready to rub it down with a magnet. :)

---

### Post by hizaguchi on 2006-07-16
Hah, I took it to the local Mac store and told them what was going on.  A "Genius" took my iPod and plugged it into her Mac and said, "Hmm, it doesn't recognize it." ](*,)   Then she took it in the back and plugged it into a Windows machine.  (Gee, why do they need Windows comptuers?)  She came back in a few minutes and said that none of their computers would recognize it, so it couldn't be fixed.

Why do they call these people Geniuses?  How intelligent do you have to be to plug something into your computer and *not* get it to work?  Especially after someone just told you it didn't work!

Ehem, anyhow, I brought it home and tried parted on it (why didn't I think of that before?).  It complains of an unrecognized disk label, so I tried "mklabel msdos" and it gave me an Input/Output error similar to what Windows said.  So something must be physically wrong with the iPod.

The lesson?  Despite being a simple USB memory stick encased in plastic and sold for $140, iPod Shuffles can randomly fail after being used for just a year and treated with extreme care.  When this happens, taking it to a Mac Genius is about as productive as using it to clean your ear canals.

---

### Post by pgabriel on 2006-07-24
A "me too" experience with an iPod shuffle of 1 GB size.

The updater does not work, i tried with WinXP SP2 and Win2K with SP4. On the XP it stops halfway with a write error.

I tried everything from chkdsk, to repartition, format, mkfs.vfat on this device without success.
Here is one of the messages that show up in dmesg:
> 
[17186268.424000] sda: Unit Not Ready, sense:
[17186268.424000] : Current: sense key: Unit Attention
[17186268.424000]     Additional sense: Medium format corrupted
[17186268.428000] sda : READ CAPACITY failed.
[17186268.428000] sda : status=1, message=00, host=0, driver=08
[17186268.428000] sd: Current: sense key: Unit Attention
[17186268.428000]     Additional sense: Medium format corrupted
[17186268.432000] sda: test WP failed, assume Write Enabled
[17186268.432000] sda: assuming drive cache: write through
[17186268.432000]  sda: unable to read partition table

This device is [COLOR="Red"]**one unreliable piece of SHIT**[/COLOR] (Apple may quote me on that) !

---

### Post by gkane on 2006-07-25
Had the same damn experience, except my last Ipod shuffle has been the fourth. The 3 before had been within the 1 year gurantee period, so they gave a "new" for free.

Now I'm done with apple ipods for quiet some time.

Greez,

gkane

---

### Post by pgabriel on 2007-02-10
After I anounced a RIP for my iPod Shuffle (1st gen) Apple published on Dec 2006 a new utility on their website the [iPod Shuffle Reset utility 1.01 for Windows]("http://www.apple.com/support/downloads/ipodshuffleresetutility101forwindows.html") that solved it.
Now I'm able to use it in Ubuntu Linux with gtkpod.

---

