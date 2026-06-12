---
title: "Now Would You Believe That?"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2009-11-11
Sometimes you just go along on assumptions or working on the premises that were passed to you.  Then something odd is noted in passing, something that doesn't quite fit, but you move on towards your final goal.  And then it l comes back into your head, probably while sleeping, and you something quite different comes to mind, like a puzzle that slowly unfurls itself until you see it from a whole new viewpoint.

Tht hppened last night.  Didn't get a whole lot of sleep as a result.

Let me share what I have so far, and we will see how it goes from there.

If you learned much about Microsoft's approach at assigning drive letters to the drives, it appears that C:, D:, E: and F: might be the consecutive partitions set up on the first drive.  Not necessarily so.  This is only true if each is a primary partition, and you did not use the Disk Manager in Windows to change any of the drive letters.

But there is another way that it would not be true, which is if any of the partitions lie in the Extended Partition, which would make them logical partitions instead.  What Windows does is go through and identify all the primary partitions that are either FAT or NTFS and assign them drive letters first, starting with C:.  Then it goes through again and looks for logical partitions that are also either FAT or NTFS and continues assigning drive letters.  Some PCs that hve USB Controllers activated early in the boot process may have their drives included in this process as well, even to the point of throwing the normal assignment of drive letters off.  How bad or awkward is this?  Well, it depends mostly on the situation you find yourself in and what you can think to do about it.

Now that is all mentioned just for background.  It just shows how things lie in one camp, and you might think of this as a matter of possible shift in drive assignments.  It becomes more of a problem with multiple drives and partitions, a situation made more acute with lower prices and a wider range of selections.

Now the Unix and Linux world came accross as being more consistent.  I mean you might set up seven partition on the first drive, and these would be known as /dev/sda1, /dev/sda2, /dev/sda3, up to /dev/sda7.  The next drive would replace the "a" in sda with a "b". and the third drive with a "c", and so on.  You probably realize that the "s" in sda might be an "h" instead, and refer to the same partition location.

Ah yes, stability.  Assign it once, and don't worry.  Only that is not quite the way it is.  For instance, if you did not create each partition in order, or began from the end of the drive and worked forward, the next digit would be in order of being made, but not from the beginning to the end as /dev/sda1 ... /dev/sda7 would suggest.  Have nou stopped and noted that before?  Or thought of what it indicated down the road?  Probably not.

Now let's assume that the sda1 to sda7 was set up in an orderly sequence, but with changing needs, you decide to scrap partitions sda3 and sda4 and replace them with a single partition.  Using some form of parted (gparted or gtparted or the installer's version), you get rid of both.  Note that none of the other designations change, but both sda3 and sda4 go away.  Then you create one large partition where both had been.  What designation does it get?  No, not sda3 or sda4, but sda8. One is added to the digit of the last partition created, so now your partition sequence is:

sda1
sda2
sda5
sda6
sda7

Later, you decide to combine three partitons and then divide that into two, and you elect to use sda1, sda2, and sda8, because they are consecutive.  So you delete and divide, and guess what?  Your sequence is now this:

sda8
sda6
sda7

Actually, I am just guessing here, as I don't know if there is a special rule for the first partition or not, but I don't know why there would be.

What does this mean?  Well, if you have an install or make use of sda6 or sda7, then you are still fine.  But any grub or fstab reference to the other partitions would now be blown.  So what is the chances of being able to boot up somewhere over there?

With Ubuntu, not too shabby.  See, instead of using the /dev references, Ubuntu relies on the assigned UUID code that is written into the partition, and no matter what it is identified as externally, if the code matches, you are good to go.  Now the bad thing (not really bad, just minor limitations) is that the unique ID is rather long and hard to follow, and each reformat creates a new and different UUID for that partition.  Oh, and one other limitation:  The partitioners only report using the /dev designations, make no reference to the UUIDs in the partitions, and do not relate what UUID is now when they have to change it, like during a format.

Well, that can be dealt with, so down to the command level using a Terminal mode we go.  But wait!  Another limitation creeps in as well:  What do we have that goes out to grup and updates it in cases like this, and does the same for the entries in /etc/fstab?  And our present install is not the only one effected, because each of the /etc/fstab tables for each existing install have to be found and updated as well.  Further, if a grub process exists anywhere else on these drives, it needs to be sought out and cleaned up at the same time.  To not do this means a real risk of finding that one or more of the existing Linux installs will not boot up if called upon to do so.

It can all be done with the right code.  And it can be done manually, but that would involve a fair amount of time and some real effort and a good bit of knowledge.  Maybe there are already some tools in place.  One could hope so.  As we move further into the era of multi-boot, multi-purpose installs on the same box, havng better tools to set up and maintain would be a great help.

So, it is open for discussion now.  Say what you want, add what you can.  We might all benefit from this.

---

### Post by wyliecoyoteuk on 2009-11-11
AFAIK, logical partitions in Linux are assigned from 5 (as there can be only 4 standard partitions per drive).
Thus the first logical partition is, for example, sda5

I have 2 standard partitions on my main drive, sda1 swap, sda2 /, sda3 is an extended partition containing sda5 /usr, and sda6 /home.
Thus the numbering is already wrecked by the limitations of the drive architecture.

---

### Post by audiomick on 2009-11-11
Hallo.
I have 5 or 6 partitions, don't know offhand exactly. I'm not that fussed, because at the moment I have far more disc space than I need, and at least 2 partitions are for a test system that I needed a while back, but haven't looked at for months.

Point is: I noticed after the upgrade to 9.10 that the grub table has gone bush.
It may have been gone earlier even, but I don't see it normally, as the machine is set to show it only on request.

As I said, I'm not that fussed right now. The partions are still there, I can access them in Nautilus from the main install. I just find it interesting that the other install doesn't appear in Grub anymore

Michael

---

### Post by oldefoxx on 2009-11-11
Version 9.10 brings us Grub 1.97 to replace 1.5 and before.  Not mandatory in 9.10 if there is a grub already in place.  But promised that it will take precidence in the future.  It falls into the group identified as Grub2.  Quite different, in fact.

The thing is, to avoid confusion, since 1.5, grub has only shown the current boot offering while it awaits your input or timeout.  But 1.5 also offered you the use of the Esc key to see more.  Haven't tried that with 1.97, or done any real reading on Grub2.

Yes, you are quite right.  All hard drives are restricted to only having up to four partitions, which we call Primary.  The boot partition is also flagged as being Active.  There are many file types that can be designated for the partitions, mut Microsoft just ignores the others.  To have more than four partitions on a hard drive, you have to create first an Extended partition, which is a special partition that allows you to create special file types in it that appear as the logical partitions.  In other words, it has to be a large enough partition to harbor each of the logical partitions created there.  Not sure of what the limit is on number of partitions, except that there are only 24 letters available (C: to Z:).  As a rule, the last primary partition used on a drive is the Extended one.  Tried to test if you could have more than one Extended partition or if it could be put earlier, but the test circumstances were not ideal, so no final determination made at the time.

As a rule, you cannot boot to a logical partition, but the exception was when Windows and Linux both came up with boot loaders that could then redirect the boot process to any partition.  Now only the boot loader (such as grub) had to be installed in the first available partition.

Speaking of the subject of my first posting here, I am wondering if the addition and removal of hard drives also has an impact on the way that Linux (Ubuntu in this case) determines the /dev references.  For instance, by adding a 500 GB to my Gateway, my boot drive is now sdb1 rather than the normal sda1.  So in order to effect a new install of any version of Linux on this machine, I have to use the Advanced ... settings immediately before the final install phase to tell the installer to put or update grub on what it identifies as the second hard drive.  To do this, I just change the (hd0) default to (hd1).

What's going to be interesting is what happens to the designations when I next install another 500 GB in a few days time.  Will sdb now become sdc, so that I have to enter (hd2) next?

Something else I did not bring to light, is that the manual mode of using the partitioner when installing Ubuntu adds another interesting factor to the mix.  You can elect to recreate the partition table.  If that does what I think (or hope) it does, then the normal sequence of identifying the hard drives and consecutive partitons will be restored.

This would be good on one hand, going back to normalcy, but would have an immediate bad effect regarding every /etc/fstab entry that uses the present /dev reference for identifying and mounting a drive.  To avoid that possibility, I will have to manually edit each /etc/fstab and put back the original UUID= identifier in place of the present /dev reference.  Now you can see some of the pathways that my mind had to race along as I tried to get some rest last night.

---

### Post by oldefoxx on 2009-12-23
I've come a ways since my last post on this thread.  Those gains have been largely documented on other threads as part of my general process, but coupled to the subject at hand.

What I want to add there is that you can work along the lines already discussed, but there is something else to add, which is the role that partition labels can play.  You alone control this feature, so you have the option to make use of it to help as well.

Under Windows, it is no big deal to set and change partition labels, which it refers to as volume labels.  I won't explain how, because it is easy enough to find.  You may have to have Administrator rights, but that is something you need for other tasks as well.  If you are not correctly set up to log in with those rights, you may need some help.

With Linux, it is a bit more involved.  That is because Linux is more assertive when it comes to rights, like ownership, right to read, right to write, right to execute.  You log in and go into one of the GUI modes, like GNOME or KDE, you are not entitled to have root or super user rights.  And partitions and drives seen under Linux that are not assigned through the /etc/fstab entries are not accessable to you, unless you zre first asked to enter your password and become super user for that purpose.

But there are some tools that can help,  Three to mention are parted, gparted, and Partition Editor.  One or more of these may show up under System/Administration.  If not, you may still find one or more through the command line interface in the terminal mode.  Can't there either,
then the Synaptec Package Manager under System/Administration my help,
or you can try to use the apt-get install process to fetch one.

These tools let you see and change the labels on any partition that is not presently mounted, and excluding the swap partition.  Since the root partition cannot be unmounted at this point, seen with the / symbol, you cannot rename it at this point.  There is a GParted.ico that can be had that will let you get access from the CD or DVD drive, and that tool will then work for all partitions.

Now how can setting labels help?  Simple.  Pick names that have some meaning to them.  If you want to associate partition /dev/sda1 with a Windows partition, you might select a lable like A1-C, which stands for /dev/sdA1 coupled with Windows seeing it as its "C" drive.  Or you may be more concerned with the file system used with that partition, and decide to name it A1-ntfs instead.  Labels generally can have up to 11 characters, but some characters must be excluded, such as +, /, and \.  It is generally a good idea to avoid spaces as well.

If continued changes to your drives and partitions tend to change their designations outside, such as in /dev or as seen by Windows with a designated letter, you can still relate to the partition then through its label, until you decide to change it.  So this can help in your management of your drives and partitions.

Now you obviously need a slightly different scheme of labelling if you have a number of external drives that are attached at different times and in varying order.  But you can work that out.  I find adding a reference to the drive or partition size to be helpful in that case, like 500G or .5T.  Whatever works best for you.

---

