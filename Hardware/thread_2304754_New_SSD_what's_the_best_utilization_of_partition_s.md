---
title: "New SSD what's the best utilization of partition space?"
date: 2015-11-29
forum: Hardware
---

### Post by cybrsaylr on 2015-11-29
Just installed a new 480GB Sandisk SSD. Used Clonezilla-Live to create a dual boot of Ubuntu 12.04 and 14.04 by cloning them off a 128GB SSD. 14.04 is installed on the 51.84 GiB partition, with Swap right next to it. Now I have a lot of extra space since this is a bigger 480GB SSD as shown here:

[IMG]http://s8.postimg.org/lafy7zl11/ssd.png[/IMG]

14.04 is my main OS. 
Question is it best and most efficient to expand the 14.04 partition?
Is it a good idea to use some of that unallocated space for storage, or best to just expand it all out with 14.04 on it?
When trying to convert it as ext4 Gparted marks this 'unallocated space' as a Primary Partition. Is this normal? 

Another option I've seen discussed here is using a separate partition like what I have now, for all your Home Files. Some claim this makes things easier by automatically saving files you want, when upgrading to a newer Ubuntu version. What is your opinion on this?

Never done anything like this before and am afraid of messing it up or doing something that may shorten the life of this SSD.

---

### Post by oldfred on 2015-11-29
While I often suggest separate /home for newer users as you can do that during install without having to create extra partitions separately and editing fstab.
But if dual booting better to have a /mnt/data partition, so you can mount all data in all installs. I then keep /home which is small/tiny inside my / (root) partition but link all the folders in the data partition into /home so it looks like a standard install.

My desktop now has a 120GB SSD and I do not know what to do with all the space. I normally use 25GB for / and have two / on SSD, but have my data on HDD. And even that is not large, so I have more installs on it, some now obsolete.

If not using Windows, I do prefer gpt partitioning, but that is not requried. It just is if drive ever gets moved to a new system with UEFI, then you need UEFI. Windows only boots from gpt with UEFI, but Ubuntu can boot from gpt with BIOS or UEFI. I started converted to gpt with 10.10 booting in BIOS mode.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by weatherman2 on 2015-11-29
I wouldn't worry at all about shortening the life of your SSD.  The technology has come light years ahead in terms of durability of the flash cells. Chances are, unless you intentionally try to write endlessly to the SSD to wear it out, it will be long obsolete before it wears out in normal use.  You can monitor "media wearout" and other Attributes in S.M.A.R.T. if you wish to monitor the status of your SSD over time.  If you're curious, do a web search for real-life tests done to see how long it takes to wear out an SSD.  You might be surprised.

Your general question about using the new space is a preference question - you'll get difference answers from different people.  There is no correct answer.  I've done it both ways.  It doesn't necessarily matter that much is probably the correct answer.  If you make a separate partition for /home and your data, then it would be easier to update your OS later without disturbing your data.  On the other hand, there are other ways to do that without using a separate partition.

But if I were going to have a separate data partition (say on /home), my preference is to have a small OS partition.  64GB is too big for me.  I find that 30GB or even 20GB is more than adequate for a basic OS partition, unless you are planning to do a lot of software development or download/install tons of software.  So - I'd first shrink that 64GB partition down, at least to 30GB, and then add the free space back to your new /home partition later.  This would allow me to use as much of the SSD as possible for data in /home.

Your 14.04 OS partition and the swap are both inside an extended partition (a container - a hack done decades ago to work around limitations of the original MSDOS partition table that allowed only four primary partitions).  You create logical partitions inside of the extended container partition, and you can have as many logicals as you wish.  To do what I suggest above, you'd first need to delete your current swap partition, then grow the extended partition to use all the new free space.  Then, shrink your 14.04 partition down.  I'd probably create the swap - another logical partition - right after the 14.04 OS (another LOGICAL partition inside your extended partition, the container) at whatever size you wish, then use the rest for the new /home .  Someday, if your 14.04 OS partition runsout of space, you'd have the ability to delete the swap, grow the OS partition next to it to use the new space, and create a new swap somewhere else, a fairly quick way to fix the problem.  But I doubt you'll run out of space on the OS partition if you choose the right size now.

(You of course need to do all of this NOT while booted into 14.04.  Don't use your old SSD, either - it's possible Clonezilla created the new drive with the same UUIDs as the old one.  I would use a live Ubuntu CD or USB boot to do everything here.)

Once you've created your new /home partition, you'll need to move everything from the 14.04 partition over to it.  Do it with the live boot.  I guess you could do all of this with your 12.04 install, too, unless it's using the same swap on that SSD...

Finally, edit your 14.04's /etc/fstab partition to mount the new UUIDs: swap has a new UUID after you deleted/created a new one.  And you'll need a new line in fstab to mount the new /home partition you've created.  This is a great time to make these changes, because if you mess up, you still have the old SSD sitting there and you can always go back and do it over again, without having lost anything.

---

### Post by kurt18947 on 2015-11-29
> My desktop now has a 120GB SSD and I do not know what to do with all the space. 

Install Windows :tongue:.

---

### Post by oldfred on 2015-11-29
> Install Windows

I do not think my 120GB SSD is big enough for both Windows & Ubuntu. Windows is a real hog. I have it on on system with a 1TB drive for TV and I shrank it to 50GB thinking I was not going to use it. But to watch some Comcast shows I need Windows, and just updates filled it. I may update to Windows 10 but am a bit concerned on how much more space that will take.

---

### Post by weatherman2 on 2015-11-29
> **oldfred said:**
> I do not think my 120GB SSD is big enough for both Windows & Ubuntu. Windows is a real hog. I have it on on system with a 1TB drive for TV and I shrank it to 50GB thinking I was not going to use it. But to watch some Comcast shows I need Windows, and just updates filled it. I may update to Windows 10 but am a bit concerned on how much more space that will take.

50GB is adequate for Windows if you don't store data on the same partition.  If your partition is filling up, try deleting some/all of your space devoted to system restore.  Use CCleaner to erase old junk files.

---

### Post by cybrsaylr on 2015-11-30
> **oldfred said:**
> I do not think my 120GB SSD is big enough for both Windows & Ubuntu. Windows is a real hog.

Yep.
My i7 just turned 6 yrs old, still runs like a champ. It came with a 1TB HDD and Windows 7. Added only a couple programs and extra browsers, didn't download anything of substance and  really hardly used W7 all those years. Used CCleaner regularly to clean out the junk. Started out with about 35GBs in C-Drive but when checking it today with all the updates, etc., C-Drive is up to a bit over 90GBs on a 2TB HDD that replaced the OEM 1TB HDD that failed right after the warranty run out! This also qualifies for Win10 which I will probably get later. Now that 2TB HDD that was seldom used is showing signs of going.

---

