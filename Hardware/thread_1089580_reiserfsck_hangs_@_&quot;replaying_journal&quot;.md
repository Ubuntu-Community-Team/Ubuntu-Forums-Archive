---
title: "reiserfsck hangs @ &quot;replaying journal&quot;"
date: 2009-03-07
forum: Hardware
---

### Post by muszek on 2009-03-07
Hi,

My father owns jukeboxes that run in pubs.  It's basically a PC running some ancient version of SuSE.  A hdd in one of them just died and I need to recover it.  It has two partitions - swap and the other one, using reiserfs.

I have a little USB thingy that lets me hook up HDDs via USB to my lappy.  This drive becomes /dev/sdb .  When I do it while running GNOME, it tries to mount the disk, displays the following error and apparently makes the drive unavailable for anything (even other devices don't automount when plugged in during that time, but it's irrelevant).

```

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

So I get out of gnome, switch to a "regular console" (ctrl+f1) and then fsck the *******.
I tried reiserfsck with various options, all of them end up right after they start with a flashing cursor after "Replaying journal..".  The longest I ran the command was approx 5 hours and nothing changed.
Example command I ran:
```

sudo reiserfsck --check --logfile fsck.log /dev/sdb2

```

How should I proceed?

---

### Post by Herman on 2009-03-07
If your hard drive has any serious problems, a file system check may or may not be able to fix anything. 

You should use a 'dd' command to make a carbon copy of the hard drive's partition(s) to another blank drive that's larger than the one you're working on first, then work on the good hard disk.
Keep the damaged or worn out hard disk as a backup and preserve it. 
Further writing to it (such as running another file system check), may do more damage and it's unlikely it will improve with use, but rather it's likely to deteriorate even further.
That depends on what's wrong with it, I'm presuming it has some bad blocks? 
```
sudo dd if=/dev/sdb2 of=/dev/sd<whatever> bs=4096 conv=notrunc,noerror
```Where: '<whatever> is an empty partition in another hard drive which is at least a little bit larger then the partition you're trying to copy. (To recover data from).

If it's only a file system problem, and not problems with the actual hard drive, you should be able to fix it with a file system check.
Or if it is the hard drive, and you have copied the partition to a hard drive that doesn't have any problems, then you can run a file system check to recover your data.

There are basically three main kinds of file system check for reiserfs.
You should start with the gentlest one and progress to the most powerful, (only if you need it).

**--check --logfile**
You might begin with something like,
```
sudo reiserfsck --check --logfile check.log /dev/sdb2
```Where: /dev/sdb2 is the partition which contains the reiser file system to be checked.
**NOTE:** After you press 'enter', you will see a message to let you know what reiserfsck will do for you and asking you to confirm.
Make sure you type 'Yes', (with a capital 'Y') after the prompt, or nothing will happen.

This runs a quick check (takes a look around), and tells you if anything is wrong. 
This is a safe command for anyone to run at any time you like. 
It doesn't fix anything, but you can use this whenever you want to perform a routine disk check or  any time you think something might be wrong with a reiser file system.

The feedback from this quick check will tell you if any more work is needed.

_Exit status _[FONT=Bitstream Vera Sans Mono]_0_[/FONT] means no errors were discovered, (you can relax and be happy).

_Exit status 1_ (and a report about fixable corruptions) means that you should run reiserfsck again with the [--fix-fixable]("http://users.bigpond.net.au/hermanzone/p10.htm#--fix-fixable") option.

_Exit status 2_ (and a report about fatal corruptions) means that you need to run reiserfsck again with the [--rebuild-tree]("http://users.bigpond.net.au/hermanzone/p10.htm#--rebuild-tree") option. 

If reiserfsck --check fails in some other way you should also run reiserfsck again with the [--rebuild-tree]("http://users.bigpond.net.au/hermanzone/p10.htm#--rebuild-tree") option. 

[B]
--fix-fixable[/B]
If 'reiserfs --check' reports back that something needs fixing, (or exit status 1), you need to run reiserfsck again with the **--fix-fixable **option.
```
sudo reiserfsck --fix-fixable --logfile fixable.log /dev/sdb2
```Where: /dev/sdb2 is the partition which contains the reiser file system to be fixed.
**NOTE:** After you press 'enter', you will see a message to let you know what reiserfsck will do for you and asking you to confirm.
Make sure you type 'Yes', (with a capital 'Y') after the prompt, or nothing will happen.

The above command should fix most problems the average user will ever have with the reiser file system.


**--rebuild-tree**
If 'reiserfs --check' reports back that it found some fatal corruptions, (or exit status 2), that's a little bit more serious, and the **--rebuild-tree**option will be necessary.
You really should make a backup of you data first (if you haven't done so already), as this command may unlink some data to the lost+found directory, see [Recovering files from lost+found.]("http://users.bigpond.net.au/hermanzone/p10.htm#Recovering_files_from_lostfound")
This may not be a safe option for new users, you might want to seek advice from more experienced Linux users before using it. 
Here it is anyway,
```
sudo reiserfsck --rebuild-tree --logfile rebuild.log /dev/sdb2
```Where: /dev/sdb2 is the partition which contains the reiser file system to be fixed.
**NOTE:** After you press 'enter', you will see a message to let you know what reiserfsck will do for you and asking you to confirm.
Make sure you type 'Yes', (with a capital 'Y') after the prompt, or nothing will happen.

If that doesn't fix it I don't know what will.

Good luck with it, I hope something here will fix it for you.
Regards, Herman :D

---

