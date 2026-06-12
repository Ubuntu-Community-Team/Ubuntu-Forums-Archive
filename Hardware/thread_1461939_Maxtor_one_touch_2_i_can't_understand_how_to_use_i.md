---
title: "Maxtor one touch 2 i can't understand how to use it"
date: 2010-04-24
forum: Hardware
---

### Post by Smart Viking on 2010-04-24
Hi all, i have a very old Maxtor one touch 2 hard disk, and i have never really used it cause when my dad bought it ages ago we didn't know how to use it (seriously it sucked).

And now when i was gonna install linux 10.04 on dad's machine from a usb, the hard disk suddenly worked with vista, i thought that was good cause i needed to take a backup of some important pictures dad didn't wanna lose, and i figured if it runs in vista it should work in ubuntu. But i was wrong, and it diddnt work with another laptop he had with windows 7. When i go under the disk properties thingy under administration(sorry if that is wrong i installed norwegian ubuntu and dont know if that is the right word on english), i can see it under extarnal hard drives "300gb hard drive" and under that "maxtor one touch ll".

The problem is that i cant to anything with it, when i say that i'm gona take that from the computer per example it says this: 

Error detaching: helper exited with exit code 1: Detaching device /dev/sdb
USB device: /sys/devices/pci0000:00/0000:00:04.1/usb1/1-6)
SYNCHRONIZE CACHE: FAILED: No such file or directory
(Continuing despite SYNCHRONIZE CACHE failure.)
STOP UNIT: FAILED: No such file or directory

Here is also an error i get when i test how fast it is:

Error benchmarking: helper exited with exit code 1: Error reading 104857600 bytes at 104857600 from /dev/sdb when guesstimating buffer size: Input/output error

And i can't even format it, then it says:

Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb: Input/output error

I don't know what is wrong with it, can someone please say a way that i can backup the images that are on it i don't want to lose them, if that is not possible is it a way i can just make that hard disk work?

---

### Post by wilee-nilee on 2010-04-25
That maxtor is formatted with NTFS you would have to partition it to install Ubuntu on it. I would run whatever tests will confirm it is a usable HD and not broken.

---

### Post by Smart Viking on 2010-04-25
> **wilee-nilee said:**
> That maxtor is formatted with NTFS you would have to partition it to install Ubuntu on it. I would run whatever tests will confirm it is a usable HD and not broken.

Hi thank you for your reply, but i'm not that good with ubuntu. So i understand i will be able to use it if i partition it, how do i do that? :)

---

### Post by wilee-nilee on 2010-04-25
So if you boot the Ubuntu live CD there is a program called gparted in system>administration>gparted this is the partitioner. Be very careful with it as it will remove everything on a partition so make sure you are removing or shrinking what you want. Also you never want to interrupt the partitioner until it finishes.

If you have a thumb drive laying around that might be a good way to figure out how gparted works, just make sure that your looking at the actual partition or empty space you want to change.

I have never used vista, and I am not sure about using gparted to shrink vista to leave a open unallocated space for the Ubuntu install. That is if you have Vista installed on the maxtor now. I suspect that there is a on board partitioner for vista. With W7 there is a virtual partitioner. Linux can't partition a running system like W7 that is why you need the Live CD for setting up the maxtor. Once Ubuntu is installed though you can install gparted to it and re-partition thumbs or any partition not actually running the computer, although if you wanted to partition a second operating system not running but on the same HD of the running Linux you have to turn off the swap partition.

No matter what though you want to backup what you need to and have a install disc for vista or at least a recovery disc. A full install disc is really the best, I always have these discs it will save a lot of time and hassles in case something goes wrong. Make sure that maxtor is actually working from what you have described I wouldn't trust it so test it. Hard drives are cheap. I don't know the testing protocol but others do.

Partitioning is easy once you know how, but it has a high level possibility of user error for a beginner so go slow and ask questions on the forum.

If you search you tube with gparted you will find tons of videos. gparted can be down loaded and booted by itself from a cd so some of he tutorials will show them using a gparted only disc, or search Google

---

### Post by Smart Viking on 2010-04-25
> **wilee-nilee said:**
> So if you boot the Ubuntu live CD there is a program called gparted in system>administration>gparted this is the partitioner. Be very careful with it as it will remove everything on a partition so make sure you are removing or shrinking what you want. Also you never want to interrupt the partitioner until it finishes.

If you have a thumb drive laying around that might be a good way to figure out how gparted works, just make sure that your looking at the actual partition or empty space you want to change.

I have never used vista, and I am not sure about using gparted to shrink vista to leave a open unallocated space for the Ubuntu install. That is if you have Vista installed on the maxtor now. I suspect that there is a on board partitioner for vista. With W7 there is a virtual partitioner. Linux can't partition a running system like W7 that is why you need the Live CD for setting up the maxtor. Once Ubuntu is installed though you can install gparted to it and re-partition thumbs or any partition not actually running the computer, although if you wanted to partition a second operating system not running but on the same HD of the running Linux you have to turn off the swap partition.


No matter what though you want to backup what you need to and have a install disc for vista or at least a recovery disc. A full install disc is really the best, I always have these discs it will save a lot of time and hassles in case something goes wrong. Make sure that maxtor is actually working from what you have described I wouldn't trust it so test it. Hard drives are cheap. I don't know the testing protocol but others do.

Partitioning is easy once you know how, but it has a high level possibility of user error for a beginner so go slow and ask questions on the forum.

If you search you tube with gparted you will find tons of videos. gparted can be down loaded and booted by itself from a cd so some of he tutorials will show them using a gparted only disc, or search Google

Hi i installed gnome partition editor, and opened it and all, but i think there have been a misunderstanding, i have installed ubuntu and it worked nice, but i am trying to make an external hard disk to work with ubuntu, cause i have pictures there. After reading you reply here it looks like you think i have not completed the install on the pc, if i'm wrong i am sorry, and if not i am sorry for my bad explanation. I am only trying to get this hard disk to be usable. :)

EDIT: The hard disk inside the pc is working fine. :)

---

### Post by wilee-nilee on 2010-04-25
> **Smart Viking said:**
> Hi i installed gnome partition editor, and opened it and all, but i think there have been a misunderstanding, i have installed ubuntu and it worked nice, but i am trying to make an external hard disk to work with ubuntu, cause i have pictures there. After reading you reply here it looks like you think i have not completed the install on the pc, if i'm wrong i am sorry, and if not i am sorry for my bad explanation. I am only trying to get this hard disk to be usable. :)

EDIT: The hard disk inside the pc is working fine. :)

I could have easily misread your post don't worry about it. Ubuntu should recognize the hard drive, if you look at the maxtor with gparted take a screenshot and post it, I am curious as to what it looks like. There are recovery methods, one I see most often prescribed is testdisk, I have never used it so I can't really help you there, but there are people on the forum who can.

So this maxtor is a usb HD I have a maxtor 4 320 gig version, is that correct?

---

### Post by Smart Viking on 2010-04-25
Hi here is a print screen in the disk information thingy:

[img]http://img651.imageshack.us/img651/1154/skjermdump300gbharddiskcydydb.png[/img]

About that program departed, it looks like that program doesnt find the external hard disk:

[img]http://img717.imageshack.us/img717/1185/skjermdumpdevsdagparted.png[/img]

Where you see there where i can choose where it stands "/dev/sda (596.17 GiB)" I cant chose that isthe only option. What also is really weird is that i think the hard disk inside the pc is 290 GB, so i don't really understand it. Can it be that that program combines the external hard disk together with the one inside the pc i dont know. :)

And thank you for your help i really appreciate it. :)

---

### Post by wilee-nilee on 2010-04-25
If you click on this drop down it may show the maxtor.
[ATTACH]154275[/ATTACH]
Gparted will only show each single hard drive or thumb,you have to use the dropdown to see others. The gparted shot looks correct I see a 600 gig HD the one Ubuntu is on in the disk utility.

---

### Post by Smart Viking on 2010-04-25
> **wilee-nilee said:**
> If you click on this drop down it may show the maxtor.
[ATTACH]154275[/ATTACH]
Gparted will only show each single hard drive or thumb.

Yes i thought so do but it only show that. it wont give me any option, the one that is chosen is the only option. :(

---

### Post by Smart Viking on 2010-04-25
Hey i think i know the answer, as you see in my reply over there i said that maybe the program combines the external hard drive and the one inside the pc, and i now know that that must be it, cause the hard disk insode the pc was 290GB and the external hard drive is ~300GB, and them together is: 590GB, which is what that lsit shows, so somewhere there is the external hard drive. :)

edit: So inside the "sda1" is te external hard drive, and the thing i have to do is to partition it, hm, i might use some help from people who know how to do that. :)

Or, i might be wrong. :( Look: 

[img]http://img707.imageshack.us/img707/8707/skjermdump640gbharddiskd.png[/img]

This shows that the main hdd in the computer is acctually over 600GB. :/

---

### Post by wilee-nilee on 2010-04-25
If you run sudo fdisk -l in Ubuntu it will give a little more information l=smallcase L.
It is showing a 600gig HD and the maxtor in the disc utility, so I am not really sure whats going on. I think your correct though that others are going to have more expertise in this area. I would be careful about doing any partitioning, when you remove one you have to use a recovery like testdisk to find stuff and you may not find it all or intact there is also a boot script which will tell us more.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
I will leave you with this, the people who are usually on line that are really good at figuring stuff out, usually show up sometime after noon pacific time and after so if you have no answers bump the thread around that time or in about the 6 hours after. 

I suggested partitioning to begin with, misunderstanding your situation. I think you recognize what partitioning is.

Yay I see somebody else posting.

---

### Post by P4man on 2010-04-25
Do you have windows installed on the internal drive? It shows up as ext4, so linux filesystem? I hope you didnt accidentally format it :S. 

It does look like a 600 GB harddrive. Dont worry about the differences between 599, 600 and 640. Its just depends if you call a gigabte 1024 megabyte or 1000 megabyte. Read this if you want to know more:
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

As for the external drive, there does seem to be a serious (hardware) issue with it. Have you tried plugging it in a different USB port? does the drive have its own power connector, or does it only use USB ? If it does not have its own power, you should use a powered USB hub.

---

### Post by Smart Viking on 2010-04-25
> **wilee-nilee said:**
> If you run sudo fdisk -l in Ubuntu it will  give a little more information l=smallcase L.
It is showing a 600gig HD and the maxtor in the disc utility, so I am  not really sure whats going on. I think your correct though that others  are going to have more expertise in this area. I would be careful about  doing any partitioning, when you remove one you have to use a recovery  like testdisk to find stuff and you may not find it all or intact there  is also a boot script which will tell us more.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
I will leave you with this, the people who are usually on line that are  really good at figuring stuff out, usually show up sometime after noon  pacific time and after so if you have no answers bump the thread around  that time or in about the 6 hours after. 

I suggested partitioning to begin with, misunderstanding your situation.  I think you recognize what partitioning is.

Yay I see somebody else posting.

Hi you have been great help, i will try out the program you linked me  too and post an eventual report of what it shows.  and here is a picture of the output when i write sudo fdisk -l:

[img]http://img693.imageshack.us/img693/6544/skjermdumpjohanjohandes.png[/img]


> **P4man said:**
> Do you have windows installed on the internal drive? It shows up as ext4, so linux filesystem? I hope you didnt accidentally format it :S. 

It does look like a 600 GB harddrive. Dont worry about the differences between 599, 600 and 640. Its just depends if you call a gigabte 1024 megabyte or 1000 megabyte. Read this if you want to know more:
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

As for the external drive, there does seem to be a serious (hardware) issue with it. Have you tried plugging it in a different USB port? does the drive have its own power connector, or does it only use USB ? If it does not have its own power, you should use a powered USB hub.

Hi, i don't think i have a windows partition on it, when i installed ubuntu i told it to use all the place in the hard disk.

I have tried plugging the usb in a different usb port, it shows the same thing, the hard disk have its own power connector.

Thank you for your reply. :)

---

### Post by P4man on 2010-04-25
Oh, maybe I misread. There seems to be no problem with the internal drive, and if its bigger than you thought, be happy :)

As for the external, since you had trouble on windows before and seeing the output you are getting in ubuntu, there clearly seems to be a hardware issue with it. It could be just the controller (/enclosure), in which case I would suggest opening the enclosure and installing the drive in your PC (assuming its a PC and not a laptop).

---

### Post by Smart Viking on 2010-04-25
Hi that programed i got a link to, "boot info script", i diddnt really understand how to use it. :(

---

### Post by Smart Viking on 2010-04-25
> **P4man said:**
> Oh, maybe I misread. There seems to be no problem with the internal drive, and if its bigger than you thought, be happy :)

As for the external, since you had trouble on windows before and seeing the output you are getting in ubuntu, there clearly seems to be a hardware issue with it. It could be just the controller (/enclosure), in which case I would suggest opening the enclosure and installing the drive in your PC (assuming its a PC and not a laptop).

Oh thanks for your reply i like you, i am not that good with ubuntu and all havent used it for more than a few months :redface: It would be nice if you told me how i do that(opening the enclosure and installing the drive in your PC) And it is a desktop and not a daptop. :)

---

### Post by wilee-nilee on 2010-04-25
> **P4man said:**
> Oh, maybe I misread. There seems to be no problem with the internal drive, and if its bigger than you thought, be happy :)

As for the external, since you had trouble on windows before and seeing the output you are getting in ubuntu, there clearly seems to be a hardware issue with it. It could be just the controller (/enclosure), in which case I would suggest opening the enclosure and installing the drive in your PC (assuming its a PC and not a laptop).

That would be great if it can be done. I wonder about the cords running to the maxtor as well. My maxtor 4 came with a dual cord but will run with just a regular single line. Good luck to you guys.

---

### Post by P4man on 2010-04-25
Here is a guide to disassemble the maxtor:
[http://www.pcdoctor-guide.com/wordpress/?p=574](http://www.pcdoctor-guide.com/wordpress/?p=574)

(interestingly, the guy who wrote that also had memory issues with it and did the disassembly for the same reason I am suggesting it to you)

It looks its an "old" PATA drive. To install it in your PC, you will need a [PATA (Parallel ATA) cable]("http://img.zdnet.com/techDirectory/_SATPAT.JPG"). Just connect it to your motherboard and drive, and connect the power connector.

---

### Post by Smart Viking on 2010-04-25
> **P4man said:**
> Here is a guide to disassemble the maxtor:
[http://www.pcdoctor-guide.com/wordpress/?p=574](http://www.pcdoctor-guide.com/wordpress/?p=574)

(interestingly, the guy who wrote that also had memory issues with it and did the disassembly for the same reason I am suggesting it to you)

It looks its an "old" PATA drive. To install it in your PC, you will need a [PATA (Parallel ATA) cable]("http://img.zdnet.com/techDirectory/_SATPAT.JPG"). Just connect it to your motherboard and drive, and connect the power connector.
Hi i was away for some minutes cause i was eating breakfast, thank you for that link it helped me much. and i'm gona take apart the hard disk if i find available pata cables inside the pc, i hope there is some or else i have to find one elsewere. I will be back later with updates.

---

### Post by P4man on 2010-04-25
Judging by your disk utility screenshots, you only have SATA devices, so probably no spare cable. IF you do have pata devices, then you may need to worry about master/slave settings too if you connect 2 devices on a single cable. I didnt mention that because I figured your system was all pata now anyway.

---

### Post by Smart Viking on 2010-04-25
> **P4man said:**
> Judging by your disk utility screenshots, you only have SATA devices, so probably no spare cable. IF you do have pata devices, then you may need to worry about master/slave settings too if you connect 2 devices on a single cable. I didnt mention that because I figured your system was all pata now anyway.

Hi, you are right the system was sata, but however i have pata cables at home and from there i might be able to use them. I am running ubuntu 9.10 at my pc where i live and i think i'm gona take with me this hard disk and continue to work on it there. 

I have now opened the hard disk and i have it right here, will it work like a normal hard disk when i later today use it with my main computer? What should i do then, when i come home? Thank for all the help it have been very valuable. :)

My main computer have pata cables with the CD player, and i will take away the cd player and use that cable with this hard disk, will that work? :)

---

### Post by P4man on 2010-04-25
> **Smart Viking said:**
> 

I have now opened the hard disk and i have it right here, will it work like a normal hard disk when i later today use it with my main computer? What should i do then, when i come home? Thank for all the help it have been very valuable. :)

Yes, it will work just like any other hdd. It is a standard harddrive, just sold in an enclosure. As for what to do, see if it shows it in fdisk -l and gparted. If the problem is with the drive itself, this wont really help, but it might be an issue with USB controller / cable or enclosure's controller or power supply.

> My main computer have pata cables with the CD player, and i will take away the cd player and use that cable with this hard disk, will that work? :)

Probably. If the cd player is the only device on the cable, it will work (just dont forget to hook up the power cable too).  If the cd is daisy chained to another pata device, make sure one of the devices on the cable is set as MASTER and the other as SLAVE. You can set that with jumpers on the back of the drive and there should be a label on the drive showing how to set the jumpers.

---

### Post by Smart Viking on 2010-04-25
> **P4man said:**
> Yes, it will work just like any other hdd. It is a standard harddrive, just sold in an enclosure. As for what to do, see if it shows it in fdisk -l and gparted. If the problem is with the drive itself, this wont really help, but it might be an issue with USB controller / cable or enclosure's controller or power supply.



Probably. If the cd player is the only device on the cable, it will work (just dont forget to hook up the power cable too).  If the cd is daisy chained to another pata device, make sure one of the devices on the cable is set as MASTER and the other as SLAVE. You can set that with jumpers on the back of the drive and there should be a label on the drive showing how to set the jumpers.

Ok, thank you for another reply you are an awesome human being that help poor noobs like me. :popcorn:

I will lay this thread to rest, and when i come home later today i will try out the hard disk once again and i will bump this thread with the updates i got, eventually i will find it to be a working hard disk and i will get the pictures on it that i needed and everything. Else i will have to work a little more on it.

I thank you once again and all that have helped me, you have learned me a lot and i have saved very much time. :KS

---

### Post by Smart Viking on 2010-04-25
Ok here is the situation.

I have just plugged the hard disk to my pc, and this it what it shows:

[img]http://img687.imageshack.us/img687/6214/screenshotpalimpsestdis.png[/img]

So, does someone know how to backup the files that are on it? It is 2 gb of pictures.

---

### Post by P4man on 2010-04-26
does seem as if the drive is working now; I guess thats progress.

To recover a damaged partition and the data on that, have a look at testdisk. Its in the repository. Extensive information available here:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

You can also try photorec from the same suite. Probably a better way if its photo's you are after:

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Smart Viking on 2010-04-26
Hi, thanks once again for a reply. 

I installed that program from the terminal, and when i find it and stuff, i looks like it is gona literally take ages to complete the scan, here it have scanned over a half hour:

[IMG]http://img130.imageshack.us/img130/4654/screenshotsmartvikingsm.png[/IMG]

---

### Post by P4man on 2010-04-26
It says "read error". Thats not good. Looks like the drive itself is hosed after all. What does palimpsest (disk utility) tell you? Also, is this during the partition detection phase? If so, maybe try photorec instead. Or let it run a while probably not ALL sectors on the drive are bad, once it can actually read them it will go a lot faster.

---

### Post by P4man on 2010-04-26
One more thing. Does the drive make funny ticking noises? If so (and even if not) what you can try is put the drive in an air tight bag and put the bag in the freezer for several hours. Use a bag to prevent condensation. That often works to temporarily revive mechanically failing drives. Then reinsert the drive in your PC and run photorec asap before it starts heating up again.

---

### Post by Smart Viking on 2010-04-26
Palimpsest say the the same it did in post #24. That was after i chose "analyse".

I might try the thing with the freezer.

But i dont know how to install photorec, in the website is game me some files and i diddnt know what to do with it, so i tried "sudo apt-get install testdisk" and it worked. But i dont know what to do to install photorec, when i try the same method it says that it diddnt find package.

EDIT: Also, i dont think i can hear any ticking noises, but i think i still will try to put it in the freezer, it sounds appealing to me. :)

---

### Post by P4man on 2010-04-26
if you installed testdisk, you already have photorec. Just run it from the terminal

---

### Post by P4man on 2010-04-26
BTW post 24 shows no drive info, only partition info. im curious about the smart status.

---

### Post by Smart Viking on 2010-04-26
> **P4man said:**
> if you installed testdisk, you already have photorec. Just run it from the terminal

Oh ok thanks it worked now, i will go to school now so i cant work more on the hard disk before i get back, thank you for the help. :)

---

### Post by Smart Viking on 2010-04-26
> **P4man said:**
> BTW post 24 shows no drive info, only partition info. im curious about the smart status.

It says "SMART status now available".

---

### Post by P4man on 2010-04-26
> **Smart Viking said:**
> It says "SMART status now available".

Now or Not ?
If its NOT, then try if you can enable SMART in your bios.
If its now (which I doubt heh), then show the smart data. Not quite sure how the menu looks in 9.10 but im looking for something like this:

[[img]http://www.ubuntu-pics.de/thumb/54185/screenshot_015_227B0C.png[/img]](http://www.ubuntu-pics.de/bild/54185/screenshot_015_227B0C.png)

---

### Post by Smart Viking on 2010-04-26
> **P4man said:**
> Now or Not ?
If its NOT, then try if you can enable SMART in your bios.
If its now (which I doubt heh), then show the smart data. Not quite sure how the menu looks in 9.10 but im looking for something like this:

[[IMG]http://www.ubuntu-pics.de/thumb/54185/screenshot_015_227B0C.png[/IMG]]("http://www.ubuntu-pics.de/bild/54185/screenshot_015_227B0C.png")

It was "not" :P

I don't know how to enable "smart" in bios.

But i found out photorec was much faster, it is an estimated time of only 140 hours with it. I will try the thing with the freezer and see. tomorrow.

---

### Post by P4man on 2010-04-26
Look around in your BIOS. It should be an option for harddrives unless you have a really old computer. Every bios looks different, but here is an example:
[IMG]http://lh6.ggpht.com/_cR9em871POY/SUlkcErkC1I/AAAAAAAABt4/CRM15lOZpc4/s800/biossmart.png[/IMG]
 If you really cant find it, can you tell me which motherboard you have, or can you tell me anything about the BIOS (like is it phoenix bios, or american megatrends or whatever). Maybe even snap a photo and upload it.

---

### Post by Smart Viking on 2010-04-26
Hi, i know about BIOS so i would manage that, and it is fully possible that it is not enabled, because the boot hard disk diddnt have a smart thingy either.

But i wont do that, because both testdisk and photorec are scanning here, so i will go to bed now, and if i'm lucky maybe it is finished when i wake up. :)

---

### Post by Everheart on 2011-02-15
Did you manage to solve the problem you were having with the hard disk?
I'm having the exact same problem.

---

