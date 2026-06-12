---
title: "USB Hard Drive looses partition after connecting to Ubuntu 12.04"
date: 2014-03-27
forum: Hardware
---

### Post by Agent-M on 2014-03-27
I have a 1TB WD drive ( connected via a USB enclosure ), which was encrypted using truecrypt. at some point I noticed there was an issue with the reported "free space", long story short, I lost the partition, which isn't a big deal as its my back up drive, and I have all the data elsewhere ( although currently not backed up, obviously). 


I tried re-encrypting with truecrypt, but it failed at the very end, so I decided to forget the encryption and just format the drive. Unfortunately regardless of whether I used ext2, ext3, ext4, or NTFS it failed, and I even had issues just creating the MBR. I don't have the exact errors that I got for that drive but could plug it in and screenshot them if needed. I do recall some input/output errors though. 


So I thought the drive possibly had died ( its only a couple of years old and hasn't been used much ).
So I bought a new 1TB Seagate, and put it in the USB enclosure.


I tried encrypting with Truecrypt again, and again it failed at the very end. So again I decided to just format, and again it got delay error messages and really didn't format it. I was trying all this with "Disk Utility", so thought I would try GParted instead, and again had problems, and wouldn't format properly.


I tried using a windows xp VM to format it, which it did no problem, could copy files to it fine, but then when I connected it to Ubuntu ( 12.04 ), it may read it ok the first time, but if I disconnect and reconnect, bang, partition was gone.


I then tried on a netbook with an install of windows 7 ( not a VM ). Again, I could format it, write to it, unplug it, plug it back in again, and all was fine...Until I plug it in to the Ubuntu Laptop, it would see it fine, even disconnected and reconnected it, and could still see the files, tried writing files to the drive using nautilus, and no problem, but then if I disconnect it, and reconnect it to either the ubuntu or win7 PC the partition is gone, and comes up as RAW in windows, and prompting me to format it.


So I thought maybe it is something with my Ubuntu installation, so again I formatted the drive in windows 7, copied a couple of files onto it, unplugged the drive and re-connected it a couple of times to make sure it was fine, then rebooted the netbook and booted up off of an ubuntu 12.04 flash drive, connected the drive, and the same thing happened, so I don't think it is my installation of Ubuntu.


I have downloaded and ran seatools for windows ( long test and DST ), and it passes the test no problem.


I have done chkdsk /f <drive letter>: a couple of times, one time it did fix some errors, but the drive still had the same issue.


I also ran a full chkdsk scan to check for bad sectors, and it found no problems.


I have 2 USB enclosures that I have just recently bought, and have tried both of them ( they are exactly the same though ), and it makes no difference.


Everytime I plug it into Ubuntu and write data it will loose the partition. I have never come across a problem like this before and it seems quite bizarre, 2 drives, 1 old, 1 new doing the exact same thing.


I would normally try connecting directly to SATA in a desktop PC to see what happens, but am away for an extended time in Africa, and don't have access to a desktop PC at the moment.


Any help at all would be apprectiated.


I have included 2 images below, the cropped one is from the Ubuntu Laptop, the uncropped one is from the netbook running Ubuntu just through a flash drive.

[IMG]http://ubuntu.5.x6.nabble.com/file/n5061660/03-cropped.png[/IMG]




[IMG]http://ubuntu.5.x6.nabble.com/file/n5061660/42.png[/IMG]



In windows as mentioned before it just shows up as RAW in computer management and prompts you to format.

---

### Post by ajgreeny on 2014-03-27
I suggest you start from scratch and use **gparted ->Device ->Create partition table**, then make and format the partitions you need in the unallocated space that will be made, to see if to see if you can get the drive(s) working properly.

I can't help with encryption as I have never used it.

---

### Post by Agent-M on 2014-03-27
> **ajgreeny said:**
> I suggest you start from scratch and use **gparted ->Device ->Create partition table**, then make and format the partitions you need in the unallocated space that will be made, to see if to see if you can get the drive(s) working properly.

I can't help with encryption as I have never used it.


Already tried that.

> .....[COLOR=#000000]I was trying all this with "Disk Utility", so thought I would try GParted instead, and again had problems, and wouldn't format properly.[/COLOR]

I'm not really worried about the encryption at this stage, I am sure that will work itself out when I manage to resolve the other issue.

---

### Post by Agent-M on 2014-03-27
Does anybody know if its possible for the USB HDD Enclosures to cause such an issue? ( i.e. could they be compatible with windows, but not 100% with Ubuntu? ).

---

### Post by houstonbofh on 2014-03-28
Yes, your USB adapter can start to go bad and cause drops and missconnects.  Different systems are more or less resiliant to this.  (FreeBSD is VERY unforgiving of this!)  I would try another enclosure, and another USB port just to eliminate external issues.

---

### Post by Agent-M on 2014-03-29
***SOLVED***

Ok, so today I went to the computer store where I bought both the 2 enclosures and the new Seagate drive.

We used a Sata HDD Docking thingo to test, and voila!!!...it worked perfectly. I could write to the drive in Ubuntu without losing the partition, and even format in Ubuntu if I wanted. I showed them what the enclosures where doing, and so they are going to get some different model / brand enclosures in on Monday from another store and then we will test those in store before I take them away.

Downside is I didn't need to buy the Seagate in the first place, as it wasn't a HDD issue.
Good news is the WD drive I was replacing is probably all OK, and so now I have 2 x 1TB drives instead of just 1
Also I am very luck that I only 'read from' and did not 'write to' the 500GB drive that I had in the other enclosure, otherwise I probably would of lost everything on that drive.

Very odd problem, and one of the guys in the store even refused that it would be the enclosures, until we tested the theory.
But glad it is resolved, or at least will be on Monday when I get my new enclosures. 

Thought I would just post how it ended in case anyone else has a similar issue.

Thanks [COLOR=#000000]ajgreeny and [/COLOR][COLOR=#000000]houstonbofh for weighing in. Appreciate the effort :)


[/COLOR]

---

### Post by houstonbofh on 2014-03-29
I have had many people show absolute moral certainty that it can not be their hardware and must be Linux, in spite of all the evidence to the contrary.  However, they are generally not paid for their technical expertise either. :)

---

