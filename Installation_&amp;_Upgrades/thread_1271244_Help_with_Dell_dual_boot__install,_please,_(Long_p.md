---
title: "Help with Dell dual boot  install, please, (Long post!)"
date: 2009-09-20
forum: Installation &amp; Upgrades
---

### Post by profozone on 2009-09-20
Ok, I apologize if this has been answered before.  I'm certain it has from my searches, but I think I'm just too stupid to understand the answers.  Here's the situation:

Hardware:  6 month old Dell Studio 15 laptop, 250GB HDD
Software: Vista 64 home premium.


I would like to install Ubuntu Ultimate Edition 2.3 on this computer as a dual boot.  Following a guide I found, I went into Windows disk manager and shrank the drive with Vista on it, which created about 63 GB of space.  Then I booted off of the CD, went to install and was presented with two options that looked possible (only one of those options was available in the guide I was following).  The first option was to put Ubuntu on the computer alongside Vista and choose between the two at boot up.  That sounded perfect.  The other option was the one in the guide that said put it in the largest available space.  Not knowing what to do, I figured that the first one was the best option and that the edition of Ubuntu was probably newer than the one in the guide.  So far so good. . . I think.

The next stumbling block was when it asked if I wanted to unmount my drives.  Even after reading the description, I wasn't sure if I did or not.  But after thinking about it for a while (and searching without finding much help), I decided to unmount them.  Mistake?

I continued on with the install.  It looked to be going well until it said that some of the partitions were too small and that continuing might cause the install to fail and that the drives needed to be what looked like 6.5GB in size minimum (it was a seriously long number without any commas).  Well that didn't sound good, so I figured I better check this out.  It sent me to the partitioning portion of the install which definitely confused me more.  First, there was some other partition in there that I didn't recognize and then it also seemed to be asking me to partition the drives, which I didn't think should be necessary because I cleared space before starting, which did show up as available during the install.  Since the space was available, shouldn't it just install there?  Why does it care that some unused drive is too small?  Anyway, I thought, no big deal, I'll go back into windows and make them all at least 6.5G.  I might be wasting space, but I though I could live with that.

Are you still with me?  If you are, you certainly have a lot of patience.

So once in windows I saw the nature of the third drive.  In total there were 3.  The first  and tiny one was for some IDE controller thingy (31MB).  The second one was the OS.  And the third one was a backup (~16Gb).  When I selected the 31 MB drive to increase it's size, assuming I could even do that, it essentially gave me no options.  I also noticed that the "shrinking" I had done before was un-done by Linux.  So I re-shrunk it and tried again.

Hang in there, just a little more to go.  I apologize.

So I decided to try again, but this time I would try the other option, to install in the largest available space.  I got essentially the same result.

Then it occurred to me that maybe I should not have selected to unmount the drives.  So I decided to go back in and select the other option and see if that helped.  This time the install did not even give me the option and hasn't since then.  After a few more tries, I decided that maybe the problem was that I only cleared the space but did not actually create a new partition.  So I went back into Vista, shrank, created a "volume" and tried again.  This time I first got an error that said I couldn't use that area until I rebooted (even though I already had before starting).  I noticed that it had created a 2.5GB swap area for itself, though.  When I clicked out of that it seemed to want to proceed, but gave me the same and by now frustrating story about having some partitions that were too ef'ing small.

So now that you have hung in here all the way to the end, I present you with the question.

It is:  WTF?

I'm sorry that I don't understand why I'm partitioning at all in Ubuntu, what will be erased when I do, why this little partition bothers Ubuntu so much, how many "primary" drives I am allowed to have or why it matters to Ubuntu or why it asks me about resizing instead of something like, "Hey, I found a huge portion of your hard drive sitting there all empty and everything. How about I install Linux up in there for you without messing up your Vista at all?  Would that be cool with you?"

Finally one other question.  During my searches I saw something about using 3 partitions just for Ubuntu to make it easier to update the OS without losing settings.  Can anyone explain in simple terms how I can load this fine operating system onto my Dell in a dual boot with Vista 64, without hosing up Vista, so that it primarily boots into Ubuntu and allows me to select Vista if I want to and to do so in a way that will make it easy to update?  An additional question would be, and I know I'm being pretty demanding here, is to explain it as though I was a 10 year old?  Ok, maybe a 12 year old?

Thank you so much for enduring this hideously long post and for any forthcoming help.  I am anxious to break the chains that bind me to Microsoft and despite my inability to load on the OS I do believe I can live with Ubuntu, since I already use a lot of the programs I would be using if I switch (Mozilla, VLC, Open Office, etc.).

Ok, just give me a second to put on my flame proof suit and I'll be ready to return to this forum to see what little gems may await.

---

### Post by mikewhatever on 2009-09-20
I am not at all familiar with Ubuntu ultimate, and whether or not its installer is the same or similar to the original one, but from what you describe, it seems that the automated partitioning doesn't work because there are too many primary partitions on the disk.

> I'm sorry that I don't understand why I'm partitioning at all in Ubuntu, what will be erased when I do, why this little partition bothers Ubuntu so much, how many "primary" drives I am allowed to have or why it matters to Ubuntu or why it asks me about resizing instead of something like, "Hey, I found a huge portion of your hard drive sitting there all empty and everything. How about I install Linux up in there for you without messing up your Vista at all? Would that be cool with you?"

Why partition?
Ubuntu can't be installed on an ntfs partition, it needs a linux file system such as ext3.

How many primary partition?
There is a limit of up to 4 primary partitions per hdd. In case you already have 4 primary partitions, you'll have to delete one before creating new partition. You'd have to do it manually.

Why resize?
If the isk is unallocated, there is no need resizing, but usually, that isn't the case. Usually, there is a bunch of ntfs partitions on the hdd, and whoever did the partitioning, ha not planned for you to install Ubuntu at a later point.

> Finally one other question. During my searches I saw something about using 3 partitions just for Ubuntu to make it easier to update the OS without losing settings. Can anyone explain in simple terms how I can load this fine operating system onto my Dell in a dual boot with Vista 64, without hosing up Vista, so that it primarily boots into Ubuntu and allows me to select Vista if I want to and to do so in a way that will make it easy to update? An additional question would be, and I know I'm being pretty demanding here, is to explain it as though I was a 10 year old? Ok, maybe a 12 year old?

Having three partitions, root, home and swap, makes it somewhat easier to reinstall, but doesn't affect updating in the least. I'd love to help, but you'd need to post more info about the current state of your hdd. Again, I am not familiar with U Ultimate's interface, but fine a program called Terminal or Console, and post the output of the following command:
sudo fdisk -l.

---

### Post by profozone on 2009-09-20
As a newb to Ubuntu, I don't know if the installer is different either.  I know it asked the same questions as the one in the guide I downloaded, but I don't know if that indicates anything.  Do you think installing a standard 9.04 version would solve my problem?

Ok, I get that only 4 primary partitions are allowed, but why does Ubuntu care?  Is it because it needs more than one partition and it's not good to have one a primary and one a logical?  Because as far as I can tell, I have 3 allocated at the moment, so I presume they are all primaries.  That would leave me 1 more primary but Ubuntu needs at least 2, right?

Can you elaborate on the Console or Terminal program.  Searches revealed programs that appear to be communications related, like networking.  Also, can I assume these programs use windows or can I just do this by booting off of the Ubuntu disk and running that command somewhere?

---

### Post by mikewhatever on 2009-09-20
By default, two partitions are created, one primary, called root is for the system, and one logical, called swap. Logical partitions are located inside an extended partitions, which in turn is a primary one. If the partitioner is trying to create these partitions, it will obviously hit the primary partitions limit. The solution to that is creating partitions manually, and making both root and swap logical partition.

Terminal is a program to run commands that looks like an empty window. In Ubuntu proper, it is located under Application->Accessories->Terminal.

---

### Post by profozone on 2009-09-20
Ok, here's what I got:

Disk / dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5532fb32

Device Boot Start End Blocks Id System
/dev/sda1 1 5 40131 de Dell Utility
/dev/sda2 6 1918 15360000 7 HPFS/NTFS
/dev/sda3 * 1918 21756 159348509 7 HPFS/NTFS
/dev/sda4 22082 30402 66829312+ f W95 Ext'd (LBA)
/dev/sda5 22082 30402 66829312  6 FAT16

This was taken after the last time I tried to install and it created the 2.5 GB of space for itself before erroring.

Hope this makes sense to you and thanks for the help.

---

### Post by mikewhatever on 2009-09-20
OK, thanks. What you have is three primary partitions, sda1, sda2, sda3, and one extended, sda4, containing a logical partition, for some reason formatted as fat16, which is an older MS file system. I am no expert, but it looks like there is no unallocated space. Now, the question is, where do you want to install Ubuntu? 
If the three primary partitions are there to stay, you'd have to resize (shrink) one of them to get unallocated space, then create an extended partition, and then create root and swap as logical for Ubuntu. Unfortunately, there is no automation for all of that.

---

### Post by profozone on 2009-09-20
The three are definitely there to stay unless I want to eliminate Vista altogether.  I don't think I'm ready to remove the training wheels just yet.

I already shrank one of the partitions to get, I believe, the extended one that you see there.  The 5th one that says FAT16, I think was created by Ubuntu as swap space.  Not sure why it is FAT16.

So I guess my question is, what do I do now?  I didn't see any difference between a logical and extended or a primary partition in the Windows Disk Manager.  They just call them volumes.  I admit I also didn't look for one either so maybe if I dig a bit.

But even if I create, what, a logical drive on the extended drive I already created, won't I still get the "some of your drives are too small" error in Linux due to the 31MB partition that doesn't go away?

I never saw in the Linux installation how to tell it where to install specifically. It just said something like "largest available space" or "alongside Vista."  I saw the partitions, but no way to select one.

---

### Post by mikewhatever on 2009-09-20
You can create, delete and edit partitions using the manual partitioning option. The 31MB partition need not be involved, but you'd have to resize one of the existing partitions to free some space for Ubuntu.

PS: Manual partitioning is no rocket science, but can be pretty confusing in the beginning, because people don't really know what to expect and aren't familiar with the terminology. Perhaps practicing in a virtual machine first is a good idea. What do you think about Virtual Box?
Some reading material:
[https://help.ubuntu.com/community/HowtoPartition?action=fullsearch&context=180&value=linkto%3A%22HowtoPartition%22](https://help.ubuntu.com/community/HowtoPartition?action=fullsearch&context=180&value=linkto%3A%22HowtoPartition%22)
[https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning](https://help.ubuntu.com/community/WindowsDualBoot#Manual%20partitioning)

---

