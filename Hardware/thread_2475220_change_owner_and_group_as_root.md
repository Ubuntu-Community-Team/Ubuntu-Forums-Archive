---
title: "change owner and group as root"
date: 2022-05-19
forum: Hardware
---

### Post by jgw on 2022-05-19
I have a little usb stick (17gb) that I have been trying to change the owner and group on.  I have read and tried all sorts of stuff to no avail.  Tells me the operation is not permitted.  I started this by going to disks, plugging in the stick, and formatting the stick in drive options.  No problem worked fine.  Then I check the owner and group and they were both root.  I would prefer that to be me and not root.  So I thought I could just use chown to do the job.  Nope, not possible.  I have tried all sorts of things and nothing seems to work (re-formatting after every failure).

I then did a search in this forum and failed to find any info (search chown, etc)   I apparently am blind as I figured somebody must have had this one but, maybe not.

Anyway, any help would be appreciated.

---

### Post by oldfred on 2022-05-19
What format is USB drive's partition?
If Windows type like NTFS or FAT32, you cannot change ownership & permissions as those file systems do not support those settings.
You set defaults when you mount partition and root with open permissions is common.

---

### Post by TheFu on 2022-05-19
The file system used matters.  Most USB thumbdrives come with either FAT32 or exFAT formats. Neither of those file systems support standard POSIX users, groups, permissions.  

There are 2 workarounds.

a) use a native Linux file system. For flash media, the one to use is called **f2fs**. It is specifically designed for use on flash storage.  But it is Android/Linux only.  f2fs requires installing the f2fs package. Then it will work. I don't recall the exact name. Use **apt search** to find it or tab completion.

b) use mount options to force a specific user, group and permissions for any non-native file system.  This can get ugly, but we don't always have choices. There are at least 50 posts in these forums with example fstab and mount commands for NTFS and/or FAT32 and/or exFAT storage.  There might be a way to add the necessary mount options using gnome-disks, but that tool doesn't really do anything besides have text entry boxes to be filled in. I find it faster to use sudoedit on the /etc/fstab and just enter the desired options there.

---

### Post by jgw on 2022-05-20
Thank you for the replies!

this is pretty strange.  What I am trying to do is to get these things back to where they were when I bought them.  As far as I can tell, when I put them in for the first time I become the owner and the group so, whatever they are before that who knows?  Apparently they figure out who has the computer or something like that.  I have been messing with this stuff for years, just never thought about it.  

Maybe somebody knows how to get one of these back to their new state.  I no longer try to do anything with them as they always change to root.  when that happens they are, pretty much, useless.

---

### Post by #&amp;thj^% on 2022-05-20
Without a Windows system, I have used this method more than once.
[https://linuxhint.com/format-usb-drive-linux/](https://linuxhint.com/format-usb-drive-linux/)
It's as close as we can get in Linux to near new state

---

### Post by The Cog on 2022-05-20
I suggest you format it to either exFAT or FAT as they are the most likely filesystems for it to have had originally. Probably exFAT would be better. But as TheFu says, they don't support Linux ownership or permissions properties.

---

### Post by jgw on 2022-05-20
Thanks for all the replies!

The problem remains.  The owner and the group is ROOT.  This happened when I used Discs to format a stick.  There seems to be no way to change that no matter what I have tried so far.  I have tried re-formatting, etc.  to no avail.

---

### Post by TheFu on 2022-05-20
> **jgw said:**
> Thanks for all the replies!

The problem remains.  The owner and the group is ROOT.  This happened when I used Discs to format a stick.  There seems to be no way to change that no matter what I have tried so far.  I have tried re-formatting, etc.  to no avail.

The issue cannot be fixed by reformatting.  

My post above provides the 2 options that will work today and forever, regardless of the DE you run. I'm sorry they aren't automagic. To my knowledge, that has never been the situation.  There may be some settings spelled out in the mount commands for different file systems to accomplish what you'd ultimately like. I don't know those.  

I'm a control freak. I want to control when and how storage is mounted to all my systems to avoid some nasty attack vectors. To each their own.

---

### Post by Morbius1 on 2022-05-21
NOTE: I try to avoid at all costs using the Disks utility but I can reproduce your issue using it - but only under one condition.

If I reformat a partition to FAT32 and then mount it still within the Disks utility it calls the normal udisks2 process and mounts the partition to /media/$USER/XXXX with the expected permissions:
> tester@vub2004:~$ ls -l /media/tester
total 4
drwxr-xr-x 2 tester tester 4096 Dec 31  1969 DataF
If however I select the option to have it automount like this:
[ATTACH=CONFIG]290505[/ATTACH]

Then it will mount with owner=group=root because the mount statement is incorrect:
> tester@vub2004:~$ ls -l /mnt
total 8
drwxr-xr-x 2 root root 4096 Dec 31  1969 D062-974A

Either:

Don't use Disks to automount the partition. [COLOR="#B22222"]This would be my recommendation[/COLOR]. 

Or add two more options to the mount statement:
[ATTACH=CONFIG]290506[/ATTACH]
Then unmount and remount and you will get the expected permissions.

> tester@vub2004:~$ ls -l /mnt
total 8
drwxr-xr-x 2 tester tester 4096 Dec 31  1969 D062-974A

Disks has weird default mounting properties. When you format something to ext4 for example it automatically does a chown to the user that invoked Disks. And it doesn't mount FAT32 or NTFS correctly at all. As Nancy once said "Just say no to Disks".

---

### Post by jgw on 2022-05-23
Thank you for all the help!

Here is what I did.  I went to Disks and did the format thing on Disks from the three dots on the upper right thing.  Then, still in disks, I clicked on the gear thing at the bottom left of the Disks screen and formatted the stick again .   The last thing let me give the stick a name.  I then tested the Stick and I can read and write it and I am the owner and group!  Success!  Oh, on one of them it had several partitions which I deleted with Disks.  I have now fixed two sticks.  They each have names and a single partition which can be read and written to.  

I am a happy camper and its because of the help so, again, THANK YOU!

---

### Post by TheFu on 2022-05-23
Look at the /etc/fstab file.  See the lines for your flash drives?  That's what my posts option "b" said. Sorry if it wasn't helpful.

---

