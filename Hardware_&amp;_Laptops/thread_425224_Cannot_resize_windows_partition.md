---
title: "Cannot resize windows partition"
date: 2007-04-27
forum: Hardware &amp; Laptops
---

### Post by sharperguy on 2007-04-27
I'm trying to install ubuntu on my mums computer.

It is a Dell and for some reason there's is a small FAT16 partition, then the main windows NTFS partition and then a small FAT32 partition and then 8MB of freespace.

I'm not sure what Dell have put on there

Anyways I try to resize the main partition which has about 15GB free, and I shave 10GB off it to install ubuntu.

But for some reason it always fails to resize.

I have tried partition magic also and it fails.

Can anyone help or is Dell locking us to windows?

---

### Post by garlik42 on 2007-04-27
Try defragmenting the partition.
gparted will not resize if there are files in the way, you need to get your free space to the end of the drive.

You can also delete your swap file (or make it smaller) and your hibernation file to make more space.

The fat32 partition at the start of the drive is dell diagnostics.
The fat32 partition at the end is the dell reload partition.

---

### Post by sharperguy on 2007-04-28
what would happen if i deleted the reload partition?

I ask because otherwise I would have to make an extended partition to fit the swap and the main partition's in since you  can only have 4 partitions.

edit: and yeah ill try a defrag

---

### Post by garlik42 on 2007-04-30
I always wipe my dells as soon as I get them, so I can't even tell you what the reload partition gives you. But if it's not there I'm sure it limits your ability to reload without using disks. If you got reinstallation media with the dell (they have the nerve of charging $10 for this, should be included and not even an option) then I think your safe. A reload disk set, includes the OS (green disk for xp, orange disk for media center) and a driver reinstall disk (blue and white). The drivers can all be downloaded from dell, the OS disk obviously cannot. Since windows ALWAYS needs to be reloaded, if you don't have the disks, make a set of install CD's from the reload partition and you can safely wipe it out. I recently made a set of reload disks for my sisters emachine, I assume dell has a similar tool. As I said before I always wipe the machines before reloading from scratch to get rid of all the crap dell fills the hard drive with. (I purchase the media ...)

And the extended partition is a must have as you state, if you need more than 4 you have little choice in the matter.

---

### Post by sharperguy on 2007-04-30
Right so how do I make the reload CD's?

(I'm not sure I we have them I'll ask next time I'm there)

---

### Post by garlik42 on 2007-04-30
As I said, I have never done this on a dell, your going to have to poke around in the programs menu and look for "something" that sounds like create backup disks or something to that order.
I wish I could give you more info, but I can't remember any more detail.

---

### Post by sharperguy on 2007-05-02
hmm ok we have the recovnery disks and have deleted the partition.

WE have also tried a defrag, but its still not resizing.

the exact error that Partition Magic gives out is ""Error 1529: Information mismatch in directory entry"

The site says to run scandisk but it did not fix the error, I will try running fsck from the live CD at some point.

Do you still think that it needs defragged (I have heard it might have to be done a few times) or is it something else?

---

### Post by lukew on 2007-05-02
> **sharperguy said:**
> hmm ok we have the recovnery disks and have deleted the partition.

WE have also tried a defrag, but its still not resizing.

the exact error that Partition Magic gives out is ""Error 1529: Information mismatch in directory entry"

The site says to run scandisk but it did not fix the error, I will try running fsck from the live CD at some point.

Do you still think that it needs defragged (I have heard it might have to be done a few times) or is it something else?

Look at the analysis tool and see if there are any non-continuous sectors. Normally you need to do it a few times; all depends upon how bad it is.

Running fsck from the live cd is a good idea.

---

### Post by garlik42 on 2007-05-02
I would not run fsck from the live cd unless it's a linux partition, you are talking about ntfs partitions here.
They should be fixed with windows.
Not sure why your using partition magic to defragment (I didn't know it could defragment)
I just use the windows defragment tool.
It also sounds like you need a chkdsk from windows also, so here is what I would do.

From a command prompt in windows
chkdsk c: /f
This will ask you if you wish to run the checkdisk on the next reboot, say yes.
Reboot, and let the checkdisk run.
Repeat for any other drives (D: E: etc)
Once this is done, you can use the windows defragger (from the gui or command line)
Command line is 
defrag DRIVE: (defrag c:)

---

### Post by lukew on 2007-05-03
> **garlik42 said:**
> I would not run fsck from the live cd unless it's a linux partition, you are talking about ntfs partitions here.
They should be fixed with windows.
Not sure why your using partition magic to defragment (I didn't know it could defragment)
I just use the windows defragment tool.
It also sounds like you need a chkdsk from windows also, so here is what I would do.

From a command prompt in windows
chkdsk c: /f
This will ask you if you wish to run the checkdisk on the next reboot, say yes.
Reboot, and let the checkdisk run.
Repeat for any other drives (D: E: etc)
Once this is done, you can use the windows defragger (from the gui or command line)
Command line is 
defrag DRIVE: (defrag c:)

fsck is just a dummy package into fsck.<filesystem> you can check windows partitions with it; and I do along with everyone else.
Also if you read the post people were recommending to defrag to remove non-continuous blocks to provide a large enough free space; it was thought that a lack of free space at the start or end of the partition was causing the partition failure.

---

### Post by sharperguy on 2007-05-03
A. I wasn't using Partition Magic to defrag

B. fsck.ntfs fails when I try to run it

C. The windows chkdisk stuff didnt fix it

D. Compiz works from the live cd :D

---

### Post by garlik42 on 2007-05-03
> fsck is just a dummy package into fsck.<filesystem> you can check windows partitions with it; and I do along with everyone else.


I'm aware you can fsck on NTFS, I didn't say you couldn't or that nobody does it. I simply said I would not do it. And everyone does not do it, you may, but I do not, so that does not constitute "everyone".

Now back to the problem.

A. I wasn't using Partition Magic to defrag
Woops my bad, too much reading between the lines.

B. fsck.ntfs fails when I try to run it
I'm not surprised, please read above :-)

C. The windows chkdisk stuff didnt fix it
Did the chkdsk give you any error messages ?? You might need to look in the event log.

D. Compiz works from the live cd 
Sorry I'm not familure with Compwiz

The net result, you need to make some space, you made some by deleting the install partition, now you need to defragment the drive to make space at the end (you can't shrink a partition past the last allocated block) IE you want to push the data as far to the "front" of the drive as possible, so you can shrink the partition and put ubuntu on the "end" of the drive.

What happens when you try to defrag the drive ?

---

### Post by sharperguy on 2007-05-04
we had tried defragging  before but anyway

GREAT NEWS it works now

not sure how lol but I'm guessing multiple defrags (as opposed to the 1 time we did it before)

(i wasn't there at the time)

Not alls i gotta do is make sure they dont go on websites looking to download programs and show them add/remove :P

---

### Post by DragonTU84 on 2007-05-04
----------
Quote:
Look at the analysis tool and see if there are any non-continuous sectors. Normally you need to [defrag] a few times; all depends upon how bad it is.
----------

----------
Quote:
GREAT NEWS it works now
----------


I had no idea that a fragmented Windows partition could mess with a partitioner.  I guess it's something that's easy to overlook.  Good to know.

---

### Post by garlik42 on 2007-05-05
> **DragonTU84 said:**
> ----------
I had no idea that a fragmented Windows partition could mess with a partitioner.  I guess it's something that's easy to overlook.  Good to know.

The partitioner tries to use the unallocated block at the end of the drive, if the drive is fragmented then even though you may have say %50 free, there may be blocks scattered all over the drive. So by defragmenting, you create the space that the partitioner needs.



sharperguy, glad you got things working!

---

