---
title: "Recovering Data from a bad drive (Superblocks and other questions)"
date: 2015-02-21
forum: Hardware
---

### Post by Uruz on 2015-02-21
Hallo,

I've got a 1TB drive which served as the main drive for my laptop. It had some problems for a while and then died suddenly and dramatically a few days ago. I've installed Ubuntu on my SSD and am using a 1TB external drive for storage.

Here's some info about the drive:
I dual-booted Windows 8 and Ubuntu 14.10 from it, so there are like, 7 or 8 partitions (the Windows and Ubuntu partitions are 5 and 6, respectively).
When I first started booting to a live CD, the partitions were visible, but could not be mounted. Later, they vanished all together.
When I first booted to the SSD, the partitions were visible and I could browse files, but while I was doing so, Nautilus froze and after rebooting for updates, the partitions were visible, but returned an error when I tried to mount them (and then disappeared).

fsck gives me:
[INDENT]fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda6[/INDENT]

Looking into this turned on Superblock issues. 

I ran "mke2fs" to give me back up Superblock locations

e2fsck gives me:
[INDENT]The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
[/INDENT]
for some of the backup Superblocks, and
[INDENT]e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda6
Could this be a zero-length partition?[/INDENT]
For others.
Note: the ones that give the first message are the 3 or 4 last ones in the list (if that matters)

Testdisk can't find the partition table (possibly because it can't read the drive)
Gddrescue can't read the drive
Spinrite can read the drive, but crashes whenever it tries to recover any bad spots.

All I'm trying to do is get files off of the drive.

Any suggestions?

---

### Post by Ollie30 on 2015-02-21
I think the problem starts when the drive starts working and heating up, so have you tried keeping it in the fridge while extending a sata cable while trying to read it? Keep it in double plastic bag while doing so as you don't want humidity on it.

---

### Post by Uruz on 2015-02-21
That's actually a really interesting theory.

Also, a general update:
I rebooted and the partitions showed up. I got a lot of data copied off of sda5 (the Windows partition), but afterwards I tried to mount sda6 (the Ubuntu partition) and it couldn't do it. After that, sda5 also became inaccessible.

---

### Post by tokyobadger on 2015-02-21
[quote="Uruz"]I've got a 1TB drive which served as the main drive for my laptop.[/quote]
Internal/external?
 [quote="Uruz"]It  had some problems for a while and then died suddenly and dramatically a  few days ago.[/quote]
What kind of problems?
What were you doing when it failed?
Why do you describe it as "dramatically"?
 [quote="Uruz"]I've installed Ubuntu on my SSD and am using a 1TB  external drive for storage.[/quote]
The SSD was already in the laptop?
The external 1TB drive is the same one that died or different?

---

### Post by Uruz on 2015-02-22
Internal harddrive.

Last summer, it started freezing, crashing, not booting, *et cetera*, which went away after some Spinrite and Fscking.
This past time, it froze strangely (I could manipulate opened windows, but not open new ones or start new programs. It crashed twice over the next day, then stopped booting altogether.

The laptop has a 32GB internal SSD which now has 14.10 on it and (usually) boots. The 1TB drive I'm using for storage is a separate, external harddrive attached via usb.

---

### Post by tokyobadger on 2015-02-23
Is the SSD in the laptop connected to the same SATA cable as the misbehaving 1TB drive?

---

### Post by Uruz on 2015-02-23
I don't really know, I'd haven't opened it up. I think it might be on the MB

---

