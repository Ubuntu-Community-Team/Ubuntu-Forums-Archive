---
title: "Setting &quot;Removable&quot; flag on an external USB hard drive"
date: 2009-12-19
forum: Hardware
---

### Post by turvyc on 2009-12-19
Hi all,

I recently reformatted my external HDD from ext3 to ext4 (mainly because it had become corrupted ... a long story, and not the point of this thread). Unfortunately, it doesn't automount anymore. 

Eventually, after much poking around and googling, I learned that the problem is because the drive's "removable" flag has been set to zero.

I can't for the life of me find a way to edit this flag. Gparted has a few flag options, but not "removable." The great Google came up empty. Fdisk has nothing, even in expert mode.

For now I have put it into my fstab, but it really is a removable drive, and *used* to be recognized as such.

Hope somebody can shed some light on this one ...

---

### Post by sligobiker on 2009-12-19
Not sure what, if any help this is, but I got the exact problem in reverse! I have a 2nd hard drive being shown on the desktop as removeable, which I don't want.

A little research led to looking in fstab, and then the [/etc/passwd]("http://en.wikipedia.org/wiki//etc/passwd") and [/etc/group]("http://en.wikipedia.org/w/index.php?title=/etc/group&action=edit&redlink=1") files.

It appears that the 2nd drive I have is in group 46, listed as a removeable group in the group files thingy. I'd hazard a guess you want it this way (I don't, obviously).

Now the down side. Fiddling with fstab didn't work, and I don't suggest fiddling with things you don't know about. If you do - for goodness sake, keep a working back up! I didn't, luckily I didn't do too much before undoing it all.

Look up fstab, umask, gid on yahoo, these *seem* to have some bearing on this. Sadly, I can't offer a more constructive or definitive answer than that, but hopefully that points you in the right direction.

Good luck!

---

### Post by turvyc on 2009-12-19
Hi sligobiker, thanks for the reply.

I'm not sure /etc/group and /etc/passwd are the way to solve this problem ... they seem to do more with managing multiple users and permissions, etc. The "removable" I need to edit is a partition flag, not a group attribute (or whatever it's called).

I'm pretty sure that a removable drive shouldn't have to be listed in /etc/fstab to work. A removable drive should automount when plugged in, and drives listed in the fstab still need to be manually mounted (unless you specify the 'auto' option, which will cause it to be automounted when the system boots up). 

The reason I'm sure it's a partition flag is because my little thumb drive automounts just fine (and it's not in the fstab), and the media type (found by right-clicking desktop icon of the mounted partition -> Properties -> Volume tab) is listed as "Removable Hard Drive." Checking the media type of my main external drive in the same way reveals it to be a "Hard Drive."

Here's the clincher, the bit that needs to change:

For my little thumb drive, the value of /sys/block/sd*/removable is 1.
For my main external drive, the value of /sys/block/sd*/removable is 0.

However, it's not so simple as opening the "removable" file with gedit and changing the number. This number is assigned by the drive itself. Or the partition. I'm not sure. What I am sure of is that this is the magic value ... and that it remains immutable despite my geekiest endeavors.

---

### Post by sligobiker on 2009-12-19
Agreed, removeable drives oughtn't be listed in fstab, they just work. But neither should fixed drives be listed as removeable!

This is from the groups file: plugdev:x:46:harley 

and it's listed in fstab as being gid 46, which I take to be (un)pluggable devices.

I guess you got some similar entry in yours, or, rather, you don't, but you do want it.

Fiddling with the fstab file did get the drive no longer listed as removeable but then it wouldn't mount.

I'm hazarding a guess you want to the opposite, have a plugdev group with your drive listed. But I could be - and probably am! - wrong, but given the exact opposite problems we have I'd be surprised if the solutions weren't similar.

---

### Post by turvyc on 2009-12-19
I think fiddling with the fstab, as well as the /etc/group file, is barking up the wrong tree. /etc/group defines user groups, used for file permissions, and plugdev is a group assigned to removable media. Adding a device to the plugdev group won't make it removable, rather, the "removable" partition flag must be set to 1.

See:
[URL="http://www.cyberciti.biz/faq/understanding-etcgroup-file/"]
http://www.cyberciti.biz/faq/understanding-etcgroup-file/[/URL]
[http://ubuntuforums.org/showthread.php?t=753931]("http://ubuntuforums.org/showthread.php?t=753931")

Also, I shouldn't have to go into fstab at all. fstab is for static file partitions already on your internal hard drive.

Does anyone out there know how to change the partition flag in /sys/block/sd*/removable from 0 to 1?

---

### Post by turvyc on 2009-12-22
*Le bump ...*

Anybody? Anybody? Ferris Beuler?

---

### Post by arnasd on 2011-05-01
Hi,

What's about this issue? Was it solved? I'm having my hdd being recognized as removable media.
I have found more related info here:
[http://ubuntuforums.org/showthread.php?t=1020293]("http://ubuntuforums.org/showthread.php?t=1020293")

---

