---
title: "Issues shrinking D: drive where I want Ubuntu"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by Pott on 2009-10-22
Hey all,

I got the 9.04 ISO image, burnt it to a CD and I'm now trying to create a seperate partitition where to install Ubuntu. 
So I did the Disk Management method where I Shrink my D drive, then assign the new free space a partition formatting etc...

My D has 47GB free out of 66.27GB. I try to shrink 15GB from it, and it tells me there is "not enough available space on the disk(s) to complete this operation"

Well there clearly is... I have 47GB free, I want to seperate 15GB from it...
[IMG]http://i7.photobucket.com/albums/y300/PierreEmmanuel/screenshot.jpg[/IMG]
Here's a screenshot of the shrinking window just in case. 

My C drive only has about 10GB left out of the original 70GB so there's no shrinking there either. I have an external HDD but I don't want to either shrink it nor to install Ubuntu on it...

Any ideas...? Thanks!

---

### Post by Mark Phelps on 2009-10-22
Your screenshot doesn't match what you're saying ...

According to the screenshot, you're trying to shrink 30+GB from the 60+GB partition -- and from the looks of it, that appears to be OK because Vista indicates that you're allowed to do that.

But, your comments say you're trying to shrink 15GB.

So, what are you really trying to do?

---

### Post by Pott on 2009-10-22
Ah sorry, I actually tried both. The screenshot is the default value. This doesn't work. I also tried with shrinking 10 and 15GB out of it, and it didn't work either. I always get the same messages.

---

### Post by John Bean on 2009-10-22
Try:
disable swap
disable hibernate
reboot
defrag
defrag again... ;-)
Finally shrink partition.

Or... boot the Ubuntu live CD and do it with Gparted instead.

---

### Post by Pott on 2009-10-22
Thanks... no idea how to disable swap to be honest, or if it'd be bad for my PC?

I may try from the Linux CD then. Thanks!

Ah another thing... if I do manage to part it, would I need to format the new partition/space as FAT32 and not NTFS? Thanks!

---

### Post by BigCajun on 2009-10-22
Is your Windows install Windows Vista? If so, you may fins this article helpful. I used it to recover most of the free space from Vista to install Ubuntu on my laptop.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")

Not sure how well it works for XP.

---

### Post by Pott on 2009-10-22
Thanks! Working on it now... I do use Vista. I can find no option to disable Hibernate however. I can only set it after so many minutes...

EDIT: 
I figured it may be easier to use gparted instead. I booted in from the CD and working on it now... I HOPE it won't mess anything else on Vista... I'm crossing my fingers.

It's on my D drive I'm parting though, not Data (C: ) and I have the whole partition backed up. So worse to come, it's tedious to restore but my laptop keeps on working...

---

### Post by John Bean on 2009-10-22
> **Pott said:**
> Thanks... no idea how to disable swap to be honest, or if it'd be bad for my PC?

You can turn it back on after you've shrunk the partition. Disabling swap allows the defragger to get move what was the paging file, which otherwise might be left strewn all over the disk making it impossible to shrink the partition from inside the working OS. Using GParted is no problem since it can move whatever it likes - I've found it to be safe and simple to do on both XP and Vista systems, probably safer than Microsoft's Disk Manager.

> Ah another thing... if I do manage to part it, would I need to format the new partition/space as FAT32 and not NTFS? Thanks!Leave all that to the OS you install, just leave it as free space for now.

---

### Post by Pott on 2009-10-22
Brilliant thanks! Running Gparted now, it's moving all the files, should take about an hour and a half. I have only about 20GB of data on it, and 40GB of free space but it's still taking ages... 
Then I guess I just reboot, check everything's ok on Vista, reboot from the CD and install it onto the free space. Sounds easy enough. Which means something, somewhere will mess up :popcorn:

---

### Post by John Bean on 2009-10-22
> **Pott said:**
> Brilliant thanks! Running Gparted now, it's moving all the files, should take about an hour and a half. I have only about 20GB of data on it, and 40GB of free space but it's still taking ages...  That's because GParted is quite careful about how it does its job. This is definitely A Good Thing.

> Then I guess I just reboot, check everything's ok on Vista, reboot from the CD and install it onto the free space.Yep, that's what I always do. One step at a time is the order of the day.

---

### Post by dkknight593 on 2009-10-22
Yup the problem is in Vista some of its files are not moveable while the OS is working.  

Besides windows tends to be such a hog for space  it thinks 60 gig ain't good enough.

gparted will work as long as there are no bad sectors on your disk.

---

### Post by Pott on 2009-10-22
Yep it worked just fine! Vista is seeing the new space ok as well. Now I put in the Ubuntu CD, do a reboot et voila... off I go. :popcorn:

Thanks for the help guys. This is a real nice place.

---

### Post by Pott on 2009-10-22
Ok running into some more issues...

I got to the partition screen with my new 15GB free space. Now I could either create a new partition from it, but I don't know what formatting to use. This would greatly simplify my problem though.

As it is those 15GB are unassigned. 
But when I got to the partition screen, it didn't seem to want to install there. It wanted to install on the main HDD, regardless of partitions.
I want this 15GB to be DEDICATED to Ubuntu. 

Especially I do not want to lose any files already on the system, Vista or personal. Just want Ubuntu to go on those 15GB with no surprises...

Should I simply assign it a drive letter and format it NTFS like all others and install on top...? Or is this a bad idea? 

Thanks y'all...

EDIT:
The install doesn't even give me the option to 'Use biggest free space' at all. So it leaves me no choice but to use one of the already used partitions, which is NOT what I want to do at all. I have 15GB freed up, why won't it see it..? 
If I go to manual mode and select those 15GB, it tells me it's not useable and that I need to edit the partition. However I do not get the partition menu for this particular free space as it's not actually one...

---

### Post by Pott on 2009-10-22
[IMG]http://i7.photobucket.com/albums/y300/PierreEmmanuel/DSCF0436.jpg[/IMG]
Here's a screenshot of my partitioner screen on the Ubuntu install...

---

### Post by John Bean on 2009-10-22
> **Pott said:**
> The install doesn't even give me the option to 'Use biggest free space' at all. So it leaves me no choice but to use one of the already used partitions, which is NOT what I want to do at all. I have 15GB freed up, why won't it see it..?
Good question.

I'm a bit unclear about your disk layout. How many physical disks are in use? Perhaps you could boot the live CD and post the output from```
sudo fdisk -l
```(that's a lower-case "L" in "-l") and see if that sheds some light on the matter.

---

### Post by Pott on 2009-10-22
Will do...

I have a single HDD, 160GB.

It's partitioned into C: ACER (system and programs) (69GB) and D: DATA (Documents and not much else) (51GB)

I also seem to have two minor partitions... not sure what these are, I'm not touching it. 

Will post the results of this command, thanks!

---

### Post by mechro on 2009-10-22
You seem to have 4 partitions. If they are all Primary then you need to do a fair bit of work to create an Extended partition where you can put some more Logical partitions.

I'll see if I can find a link to explain.

---

### Post by Pott on 2009-10-22
Thanks. This is how the PC was originally. All I did was create those free 15GB today, as of now unassigned and not parted/named.

Here are the results from the fdisk command. I have all external memory disconnected.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x007e7baf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       10383    73162752    6  FAT16
/dev/sda3           10384       17076    53761522+   7  HPFS/NTFS
/dev/sda4           19034       19458     3398656   12  Compaq diagnostics
ubuntu@ubuntu:~$

---

### Post by mechro on 2009-10-22
You have 4 Primary partitions.

In Gparted, you can only create an extended partition from free space if you have less than 4 Primary partitions. This means you would have to back up and then delete one of your partitions (possibly sda4).

---

### Post by Pott on 2009-10-22
Ah... I'll be honest I have no idea how to do this... I wouldn't mind getting rid of sd4a but I need to know 100% it's safe... I have about 30GB left on my external HDD I could use to back it up but I don't know if 1) it'd be enough and 2) everything would still work 100% after all this...

Thanks for the help. It simply looks like it's not happening. 

Unless, if I format the new 15GB as standard, to FAT32 or NTFS, would it still turn it into a primary..? I did create this space using Gparted. If it doesn't then I can select this partition for the install surely..?

---

### Post by mechro on 2009-10-22
You've already got 4 Primary partitions. That's the maximum. You can't create a 5th Primary partition.

With 4 Primary partitions you can move or resize them (which is what you did). You would have to delete one of the operating systems to free up a partition for Ubuntu.

---

### Post by Pott on 2009-10-22
Ah sorry I didn't get I needed the partition to be primary... 

Why did Ubuntu tell me I have 'several' OS?

On all other examples I just saw it detect 'Vista/Longhorn'. Mine's got three different ones... Vista bootloader, Vista and XP Embedded... Is it safe to remove them..? I'm not even sure I can though...

---

### Post by mechro on 2009-10-22
It doesn't need to be Primary. But to have more than 4 partitions you have to make one of the 4 an Extended partition in which you can then have lots of Logical partitions.

I've already explained how you would make an Extended partition.

---

### Post by Pott on 2009-10-22
Ok... I'm a bit slow, I have no idea what a primary partition is, I've never done much like this before.


EDIT: I had a look at that XP Embedded drive. I can't even edit it. I'm guessing with Gparted I could format it, but I don't know how that'd affect my Vista system. Best leave it alone for now. I guess I won't be able to get Ubuntu at all for now...

Both my extra two partitions aren't accessible from Windows. No way I can look at what's into them. I also don't know if the system needs them or if they're sitting there for nothing. I did a search on how to create an Extended partition on Vista and it's not possible anymore (though I could use Gparted of course anyway)

---

### Post by John Bean on 2009-10-23
> **Pott said:**
> Ok... I'm a bit slow, I have no idea what a primary partition is, I've never done much like this before.
A disk can contain only four primary partitions - partitions used to directly store data - but one of them can be used instead as a sort of "folder" to allow the creation of other partitions within it, thus extending the number of available partitions beyond the maximum allowed as primary.

This means in reality that you can have a maximum of three primary partitions, the fourth becomes an extended partition within which you can create as many others as you need.

> EDIT: I had a look at that XP Embedded drive. I can't even edit it. I'm guessing with Gparted I could format it, but I don't know how that'd affect my Vista system. Best leave it alone for now. I guess I won't be able to get Ubuntu at all for now...

Both my extra two partitions aren't accessible from Windows. No way I can look at what's into them. I also don't know if the system needs them or if they're sitting there for nothing. I did a search on how to create an Extended partition on Vista and it's not possible anymore (though I could use Gparted of course anyway)

I have some as well, they're usually "recovery" partitions to re-install/fix the standard OS and/or related to the BIOS or something specific to the hardware manufacturer. My HP has both but I had no "data" partition so I didn't have the problem you have since I had space for a new extended partition.

This is what I would do:

1. Copy the contents of your "data" disk to external storage.
2. Remove the partition that was your "data" disk and merge the free space.
3. Create a new extended partition using all available free space.
4. Create/format a new data partition equivalent to the old "data" disk.
5. Restore the saved data back to it.

Then go back to installing Ubuntu and all will be well.

---

### Post by Pott on 2009-10-23
OH! I see what you mean. Get rid of D, create a 'new' D as an extended partition, create a sub-partition (logic partition I think) in it for my data and keep the rest for Ubuntu! Great idea! I'll use Gparted since it seems not only a lot safer but also a lot more straightforward. Thanks!



EDIT: OOOPS... ah well lesson learnt for the day... I'd forgotten that my D: drive had the 'Documents' folders... when I erased it all (after a backup...) I accidentally got rid of pretty much everything... desktop icons etc... Thankfully I had it backed up. Restoring now, then I'll manually move the Documents folder to its original location...

---

### Post by John Bean on 2009-10-23
> **Pott said:**
> OH! I see what you mean. Get rid of D, create a 'new' D as an extended partition, create a sub-partition (logic partition I think) in it for my data and keep the rest for Ubuntu! Great idea! I'll use Gparted since it seems not only a lot safer but also a lot more straightforward. Thanks!

You got it, more or less. The old "D" becomes an extended partition (which is just a wrapper) but the new "D" will actually be a logical partition inside the new extended partition and not the extended partition itself. You'll see what I mean when you do it - Gparted will show both the extended and any enclosed logical partitions as separate entities; an extended partition never contains user data, only other partitions.

I'd be inclined do everything from the live CD including the saving/restoring of the contents of your existing partition. How you copy the data is up to you, just make sure you really do get everything.

Afterwards you can do a Ubuntu install using the "use largest free space" option and that should be it.

---

### Post by Pott on 2009-10-23
ARGH!!!!!!


I'd restored D on my external HDD... But for some reason now when I do the restore it's restoring C and all my program files!! D is gone! What the hell happened???

The whole 'Documents' folder is erased. It's still in my external HDD but not as 'Documents', just as a copy.

CRAAAAAAAAAP...

---

### Post by John Bean on 2009-10-23
> **Pott said:**
> ARGH!!!!!!That sounds like you were using Windows tools...

I don't want to add to your pain but you'll need to explain exactly what you did if we're to try to make sense of what's happening.

>  The whole 'Documents' folder is erased. It's still in my external HDD but not as 'Documents', just as a copy.

I don't understand what you mean I'm afraid. Are the documents there or not? If they are then all you need do is replace the special "My Documents" (whatever) folder in its new home on the new partition then copy the files back into it.

---

### Post by Pott on 2009-10-23
Ah no I managed to solve this... let me explain:

I had all my personal folders moved to a location in D (to save space in C). When I deleted D to re-part it, I forgot about this.
So I googled a bunch of things, and managed to edit (with regedit) the Personal folder details and re-create the missing ones. Then I copied/pasted the contents from the manual backup I did on my external HDD (basically a copy/paste just so I had it available when needed). Everything works just fine now and D is totally empty and ready for Ubuntu.

:D

Thanks!

---

### Post by Pott on 2009-10-23
Ok... Went into Ubuntu (live) and used Gparted. It took all of about to seconds to delete the old (now empty) D:, create an Extended partition and 2 logical partitions, one 15GB (for Ubuntu) and the other 51GB (for files).
Now back onto Windows to do a last check and then, install time.

EDIT: posting from Ubuntu, installed :D :D 

Now a few things to do...

1) Tweak the settings for my PC (hotkeys on the right are not acting right on this model
2) I get offered two Vista choices at startup, I'm not sure which is which. If I go in order of partitioning it'd be the second one but I need to make sure
3) Change GRUB to set the correct vista by default
4) mess around! 

Thanks for the help everyone. This is truly a nice place.

---

### Post by John Bean on 2009-10-23
> **Pott said:**
> 2) I get offered two Vista choices at startup, I'm not sure which is which. If I go in order of partitioning it'd be the second one but I need to make sure
One of them is probably the recovery partition normally accessible from the BIOS or a special boot disk. My Ubuntu install on a HP laptop (with Vista) offering similar choices.

Boot the installed Ubuntu and you'll probably see it listed in "Places" and you can look at what's in it. On mine the label says "HP_TOOLS" and if booted it loads a program to take the whole machine back to factory install state. It does ask first though.

Have a look in /boot/grub/menu.lst and you'll see which is which if you compare the entries with your partition list. In my case Vista is on /dev/sda1 and the other one on /dev/sda3. My default boots neither of them of course... ;-)

Anyway, glad to have helped. Enjoy :-)

---

