---
title: "Looking for ew laptop with 3 or less primary factory partitions."
date: 2010-12-15
forum: Hardware
---

### Post by hpng on 2010-12-15
Hello:
 

 I currently have a laptop: HP DV7-4173us.
 AMD Phenom II Quad, Win 7 & 64 bits.
 Here is the problem:
 The partitions on the hard drive already has 4 (maximum allowable) factory  
 primary partitions, namely:
 
[LIST=1]Partition #1)  SYSTEM where all 	systems files resides  	
Partition #2) (C:)  where Win7 resides
Partition #3) RECOVERY   	
Partition #3) HP_Tools ( I assume 	where HP has all it recovery and diagnostic tools)  	
[/LIST]
  I cannot create another partition for Linux due to disk drive primary partition limitations.
 However, I can install Linux via Wubi onto the C: partition where Win 7 resides.
 

 I do not want to mix Linux and Win7 on same partition.
 I can however get a 2 nd hard drive for the HP laptop.
 But getting help from HP is like pulling teeth without anesthesia.
Tried talking with them for over 3+ hours.... NOT joking......

 

 So I am looking at other laptops.  If any have this information, I would appreciate it:
 
[LIST=1]
[*]If your  laptop is new with Win 7, 	let me know if your Laptop has 3 or less factory primary partitions. 	 Look ad “Disk Management” app to display all partitions on your 	drive.  Thanks
 	Remember, I need another empty 	partition for Linux.
 	Please provide laptop manufacturer 	name and model #
[/LIST]
 

 Thanks.

---

### Post by akand074 on 2010-12-15
You can install Ubuntu as an "Extended" partition. It won't make any difference. Weird that there is so much partitions in the first place by default. I don't know why theres a C: drive and a system partition, and a Recovery partition and a HP-Tools partition. I'm sure they could have cut that down.

---

### Post by hpng on 2010-12-15
> **akand074 said:**
> You can install Ubuntu as an "Extended" partition. It won't make any difference. Weird that there is so much partitions in the first place by default. I don't know why theres a C: drive and a system partition, and a Recovery partition and a HP-Tools partition. I'm sure they could have cut that down.


Thanks for the reply, but I am still confused.  I am new to Linux.
Since I already have 4 factory default PRIMARY partitions on the hard drive,
and I cannot create another primary partition on the same drive,
how do I create an extended partition on the same drive?

I mean can one insert an extended partition in the "C" partittion?

I assume you mean to create an extended partition on partition labeled C ( where win 7 resides and it has 400+ GB), right?
and how do yoiu go about creating an extended partition on C partition?

---

### Post by coffeecat on 2010-12-15
You have to delete a primary partition before you can create an extended partition. You can't create an extended partition on C: because that is already a primary partition. In the mbr/ms-dos partition table scheme you can have a maximum of four primary partitions, one of which can be replaced by an extended for holding logical partitions.

Anyway, to your problem. This is common with HP machines in particular. What you will have to do is to delete either the recovery partition or the HP tools partition. So make sure you make a set of HP recovery DVDs before you do anything. The so-called SYSTEM partition is really the Windows boot partition. If you examine it you'll see that it is only about 100-200MB in size. You must not delete that.

**EDIT:** You might find this useful. One for your bookmarks.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by hpng on 2010-12-15
> **coffeecat said:**
> You have to delete a primary partition before you can create an extended partition. You can't create an extended partition on C: because that is already a primary partition. In the mbr/ms-dos partition table scheme you can have a maximum of four primary partitions, one of which can be replaced by an extended for holding logical partitions.

Anyway, to your problem. This is common with HP machines in particular. What you will have to do is to delete either the recovery partition or the HP tools partition. So make sure you make a set of HP recovery DVDs before you do anything. The so-called SYSTEM partition is really the Windows boot partition. If you examine it you'll see that it is only about 100-200MB in size. You must not delete that.

**EDIT:** You might find this useful. One for your bookmarks.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Thanks.
Sounds like you have used a HP laptop before.
My HP_Tools partition has only 103 MB, and my RECOVERY partition has 21GB.

Instead of deleting the RECOVERY partition, can I install Linux into RECOVERY partition
in a seperate directory?  ( I do not know how to do this... but may be GRUB can do it...)
Do you know what is in the Recovery partition?
I am worried if it has files sued by HP during drive diagnostics and clean-up.


Q

---

### Post by coffeecat on 2010-12-15
> **hpng said:**
> Sounds like you have used a HP laptop before.

I've simply helped on enough threads to know what to expect with HP.

> **hpng said:**
> Instead of deleting the RECOVERY partition, can I install Linux into RECOVERY partition
in a seperate directory?

NO! This is essentially the same question you posed about installing an extended partition in the "C: drive". You seem to be confused between the differences between partition, filesystems and directories. I suggest you read through the link I posted including the links in it. If you do you will see that Ubuntu needs at least two partitions - hence the need for an extended partition in which you can create a number of logical partitions.

I repeat - you have to *delete* a primary partition before you can create an extended one.

> **hpng said:**
> but may be GRUB can do it...)

Grub is a bootloader. It has nothing to do with creating partitions and flesystems.

> **hpng said:**
> Do you know what is in the Recovery partition?

A recovery partition of 20GB would have all the files needed to do an operating system restore and probably all the "free" software (i.e. bloatware) that came with a factory install as well. It is designed to reset your machine to its factory default if you need to reinstall Windows. If you use it your will lose all your installed apps, settings and personal files in Windows, but it is essential for restoring Windows if you need to. Different manufacturers' restore utilities vary in their flexibility over how much control you have. Some will simply wipe the drive and start over so that you lose Ubuntu. Some will allow you to restore Windows into a shrunken C: partition. I don't know how flexible the HP restore utility is.

Since the recovery partition is used for reinstalling Windows, this is why I asked you whether you had prepared a set of restore DVDs. There will be a HP utility to enable you to do this. the DVDs act as a backup or alternative to the restore partition. If you haven't created a set of DVDs, **do it now**. And while you're about it, create a Windows 7 repair disc from within Windows. Do not leave it to later. You may need it.

> **hpng said:**
> I am worried if it has files sued by HP during drive diagnostics and clean-up.

Perhaps they are in the HP tools partition. Check in the documentation.

---

### Post by hpng on 2010-12-15
Thanks.
I already created a 5 DVD system recovery disk before.
Just did the system repair disk.
I will go read your recommendations.

---

### Post by MSPdwalt on 2010-12-15
Another simpler option for you hpng may be to use a virtual machine.  If you 're just looking to try out linux it's a quick way to do it without having to fully understand the hardware implications.  I recommend vmware player or oracle (sun) virtualbox.

But, if you're serious about learning anything and everything defiantly go with coffeecat

---

### Post by hpng on 2010-12-15
> **coffeecat said:**
> I've simply helped on enough threads to know what to expect with HP.
.....
Perhaps they are in the HP tools partition. Check in the documentation.....

I cannot seems to access the HP_TOOLS partition from Win 7.
I can use Disk Management to display all the partitions, but not what inside 
the partitions.

Does anyone know how to display files inside each partition when Win 7 is running?

---

### Post by pricetech on 2010-12-15
If you still want a brand and model, I have a Dell Latitude E5500 that came with 2 partitions.  One was a diagnostic partition and the other was the OS.  Granted mine had XP and was licensed for Vista, but since Dell included media and the diags are a breeze to find and download, I wiped the whole drive and put Hardy on it.

It has since had Windows 7, which created 2 partitions, and now Lucid on a single partition.

Install media is the key, along with support from the manufacturer.  You'll probably have to insist on media when you purchase it, and don't purchase without it, but support is a website away with Dell.

---

### Post by akand074 on 2010-12-15
I've seen plenty of HP systems that only came with two partitions, the odd time three. Never seen more personally and I worked in retail for over a year until I left for school in September. So I'm sure there are others.. go look at laptops in stores and then get a similar model.

By the way, do you use all those HP stuff? With the 4 partitions and all I assume it has HP Quickweb installed. If not and you can get your hands on a Windows 7 disk you could just wipe all the partitions except the recovery partition and reinstall a clean Windows partition. Now your down to two partitions. I'm sure you can then install any HP stuff you want back (HP generally has all of their software/drivers they provide you in their support page for your model).

---

### Post by hpng on 2010-12-15
> **pricetech said:**
> If you still want a brand and model, I have a Dell Latitude E5500 that came with 2 partitions.  One was a diagnostic partition and the other was the OS.  Granted mine had XP and was licensed for Vista, but since Dell included media and the diags are a breeze to find and download, I wiped the whole drive and _**put Hardy on it.**_

It has since had Windows 7, which created 2 partitions, and now Lucid on a single partition.

Install media is the key, along with support from the manufacturer.  You'll probably have to insist on media when you purchase it, and don't purchase without it, but support is a website away with Dell.

thanks.
What do you mean "... put Hardy on it?"......
too cryptic for me.....thanks.

---

### Post by akand074 on 2010-12-16
> **hpng said:**
> thanks.
What do you mean "... put Hardy on it?"......
too cryptic for me.....thanks.

Hardy is an old version of Ubuntu (Hardy Heron). Version 8.04 to be exact.

---

### Post by MSPdwalt on 2010-12-16
> **hpng said:**
> I cannot seems to access the HP_TOOLS partition from Win 7.
I can use Disk Management to display all the partitions, but not what inside 
the partitions.

Does anyone know how to display files inside each partition when Win 7 is running?

Do the partitions have drive letters associated with them?  If not they won't show in windows explorer.  You should be able to go into disk management and add a drive letter to any partition accessible by windows.

---

### Post by pricetech on 2010-12-17
> **hpng said:**
> thanks.
What do you mean "... put Hardy on it?"......
too cryptic for me.....thanks.

Ubuntu 8.04 Hardy Heron.  It was the last LTS release.

Sorry, I got carried away there and wasn't thinking.



Thanks for jumping in there in my absence akand074.

---

