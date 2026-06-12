---
title: "Is Partition Magic Reliable?"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by Maheriano on 2009-03-26
I'm picking up a Dell Studio 15 in an hour and it'll have Vista 64 bit on it. I'm wondering if I should wipe the drive and reinstall Ubuntu and Vista again or if I should just use a partitioner to free up some space and then install Ubuntu, then fix Grub. I want to minimize file fragmentation as much as possible.

---

### Post by aysiu on 2009-03-26
Well, there's no point in paying for Partition Magic when Ubuntu's own installer will repartition your drive for free.

But also, why even bother with the repartitioning when Wubi will set up a dual-boot without it?

Use Wubi:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by Rohan Kapoor on 2009-03-26
Personally, I would nuke Vista and never use it. I also dislike Wubi because it requires a Windows to be installed. Just go with a native install man!

---

### Post by lisati on 2009-03-26
Ubuntu comes with its own partioner. 

Go with Wubi if you want to evaluate Ubuntu - Wubi makes it simpler to remove Ubuntu through Windows if it doesn't suit. Otherwise, if you're brave enough, go with putting it in its own partition.

You might want to consider a "dual boot" while you're finding your way around. That way, you can still use your machine if something goes wrorg, or if you *need* something that can only be done in Windows.

Good luck weighing up the options, and feel free to continue asking questions.

---

### Post by Maheriano on 2009-03-27
I think I didn't convey my needs and user level correctly.
I got a dekstop with a terabyte drive partitioned into 3 paritions for my 64 bit Ubuntu install and a 12 gig NTFS partition that I will eventually put XP on. But as of right now, Ubuntu is the only thing on it.
The laptop, if it were my daily machine, would only have Ubuntu on it but it's just for messing around with so I think I'll just dual boot it. Though now you got me wondering if I would ever even boot into Windows, I haven't used it since I returned my HP laptop in December. And I don't even like it at all to be honest. Not sure....

---

### Post by Herman on 2009-03-27
:) Another way to do things is to install Windows inside Ubuntu, (instead of the other way around). If you have a Windows 'Installation CD', (as opposed to a 'Restore CD or a 'Restoration Partition), you can do that.

You need a reasonable amount of RAM because you will be running both operating systems at the same time! You can have Windows booted in VMware Server in one workspace inside Ubuntu. The chief advantage of that is you be using Windows and you can press a few keys and click your mouse to switch to another workspace and be back in Ubuntu again whenever you need to.

 For example, I have a friend who owns a Motel, and he needs Windows only for a special business program called MYOB, which is popular in my country. His accountant also has this program, and it's most convenient for him to stick to that. His accountant's computer has the same MYOB program so he only needs to send his accountant the files, and the accountant already knows what to do. He doesn't want to switch to some other program, it would probably be too much work, and I don't know of a Linux equivalent for that program yet anyway. He only needs Windows for that one program only.

The rest of the time he would rather use Ubuntu, since Ubuntu is almost worry free and Windows is so vulnerable to viruses and other malicious programs. 
He wants to be able to watch a movie or browse the internet in Ubuntu when business is quiet and there's nothing to do, but be able to switch to Windows instantly when the phone rings or a customer arrives and wants to make a booking. Installing Windows inside Ubuntu is one way to solve this kind of problem. 

Here's the link: [B][HowTo: Windows (XP) on Ubuntu with VMWare Server]("http://ubuntuforums.org/showthread.php?t=183209&highlight=make+icons")

[/B]I'm not posting this to contradict anyone, but just to offer another alternative. No offense intended. I haven't tried wubi so I have no idea of the pros and cons or which is better or worse, only that I've tried this way and I think it's neat.

UPDATE: Actually, I just tried that out (VMWare) to test it since it's been a while and it doesn't seem to work anymore in the newer versions of Ubuntu, (at least not in a hurry when I tried it).
VirtualBox is probably better, I'm trying that out right now and it looks like it will do the same thing only better, [VirtualBox]("http://www.virtualbox.org/").
I'm installing an operating system in that right now to see how it works.

---

### Post by Mark Phelps on 2009-03-27
> **Maheriano said:**
> I'm picking up a Dell Studio 15 in an hour and it'll have Vista 64 bit on it. I'm wondering if I should wipe the drive and reinstall Ubuntu and Vista again or if I should just use a partitioner to free up some space and then install Ubuntu, then fix Grub. I want to minimize file fragmentation as much as possible.


Just be aware that the Ubuntu partitioner (and GParted) sometimes corrupts the Vista OS partition when resizing it.  If you have a Vista DVD, you should be able to fix that by booting from that CD and running Startup Repair.  If you don't have that CD, and your Vista OS does become corrupted, then you'll be stuck with a non working Vista.

---

### Post by Herman on 2009-03-27
Well I don't think GParted actually corrupts Vista, but GParted sets a 'dirty' flag in an NTFS partition deliberately to induce Windows to run a file system check in it's NTFS at the next Windows boot-up as a matter of course. It is recommended in GParted's documentation to run CHKDSK after resizing an NTFS partition.
NTFS support is pretty good now, and since the second release of Ubuntu (years ago),  I don't think there have been any problems as far as the file system is concerned, or at least not an unusual number of problems.

GParted doesn't automatically align the partition the way Vista likes. Vista has a different start point than sector 63 to make it more compatible with flash memory,  as flash pages are 4 KB and a 'block' is 128 pages. So for good partition alignment in a flash device, the start point is not sector 63 but something like 128 or 512 or some other multiple of eight. Most people are still using hard discs at this point in time, except for the military or the wealthy.
GParted still aligns partitions on cylinder boundaries  for hard discs to keep it compatible with most other software an operating systems, but you can easily over-ride that by removing the check mark from the box 'round to cylinders', if it's a problem for you.  If the Vista start point has been moved, (which most people wouldn't need to do anyway), you only need to re-install the MBR, only if you're not using GRUB. Vista's boot loader lacks the features that help it to find the other half of itself from the MBR except by the boot flag or by the sector number.

---

### Post by khelben1979 on 2009-03-27
If you decide on to use a commercial partition manager, then I personally think that [the Paragon Partition Manager]("http://en.wikipedia.org/wiki/Paragon_Software_Group") is a better alternative than [Partition Magic]("http://en.wikipedia.org/wiki/Partition_Magic") nowadays.

I tried it myself a few years ago and I personally liked it. Nice and easy user interface but still powerful software.

---

### Post by meierfra. on 2009-03-27
> GParted still aligns partitions on cylinder boundaries for hard discs to keep it compatible with most other software an operating systems,

Just curious: Can you name some  software, which is still in use  and requires partitions to be on cylindrical bound?


> If the Vista start point has been moved, (which most people wouldn't need to do anyway), you only need to re-install the MBR, only if you're not using GRUB.

Wrong.

1) Reinstalling the MBR does not help. In fact, there is nothing wrong with the MBR after the Vista start point has been moved (any partitioning program will adjust the partition table in the MBR).  So the MBR will have no problem finding the boot sector of the Vista partition.  Also the boot sector is still  able to find  "bootmgr". But "bootmgr" will not be able to find "winload.exe". (bootmgr consults BCD to determine the partition containing "winload.exe" and   BCD often labels partitions by the starting sector.)

2)  Grub also  won't be able boot Vista.  Grub just calls the boot sector of the Vista partition.  But  the problem occurs much later in the booting process at a stage when grub is longer involved.


> I don't think GParted actually corrupts Vista,
But gparted moves the start point to  keep  partitions on cylindrical  bounds. No modern partitioning program should do that without at least asking the user.
** Edit: only when gparted  has a "round to cylinder"  box and that box is checked, will gparted move the start point.**


PS:  I would like to mentioned   that recent version of  gparted have  a "round to cylinder"  box. Unchecking that box should avoid the problem with resizing  Vista. (**Edit:  I'm no longer sure that unchecking box will always be enough to avoid booting problems. **

---

### Post by wpshooter on 2009-03-27
> **darth-vader said:**
> Personally, I would nuke Vista and never use it. I also dislike Wubi because it requires a Windows to be installed. Just go with a native install man!

I second that !!!

---

### Post by ronparent on 2009-03-27
To reply to your original question - Partition Magic is now owned by Norton, and they haven't yet done anything I know of to update it since the release of Vista. I have used it from time to time and have found it relyable. It should be fine with Win XP.

---

### Post by kestrel1 on 2009-03-27
> **ronparent said:**
> To reply to your original question - Partition Magic is now owned by Norton, and they haven't yet done anything I know of to update it since the release of Vista. I have used it from time to time and have found it relyable. It should be fine with Win XP.
Partition Magic is reliable for Windows XP & below, but personally I now prefer to use gparted. Acronis Partition Manager is also OK, but why pay for it when Gparted is free. :-)

---

### Post by Maheriano on 2009-03-28
Good points, forgot about the partitioner included with the LiveCD. I won't actually be getting the machine now until mid April so I got lots of time to think about if 9.04 would be enough for me or not. I'd rather not use Windows since I don't use it at all right now and it should be pretty easy to keep going with this routine.

---

### Post by PenguinsFan on 2009-03-28
I've used Partition Magic for years - its a little slow, but very reliable.

Yes - you can just use Ubuntu's built in partitioner if you'd like (no reason not too, its literally the same thing) but it can be handy and a little more intuitive to have a dedicated partitioning disc. I'd say make yourself a copy and give it a go!

Good luck!

---

### Post by MysticGold04 on 2009-03-28
Cheers Man... Hold on to Ubuntu... its good stuff and will suit you well!

---

### Post by Herman on 2009-03-28
:) Hello meierfra,
> 
                    [quote]GParted still aligns partitions on cylinder boundaries for hard discs to keep it compatible with most other software an operating systems,            Just curious: Can you name some  software, which is still in use  and requires partitions to be on cylindrical bound?
[/quote]According to the following link to a blog by Theodore Ts'o, [Aligning filesystems to an SSD&#8217;s erase block size]("http://ubuntuforums.org/Aligning%20filesystems%20to%20an%20SSD%C3%A2%C2%80%C2%99s%20erase%20block%20size") , quote "So this is one place where Vista is ahead of Linux&#8230;.   unfortunately the default 255 heads and 63 sectors is hard coded in many places in the kernel, in the SCSI stack, and in various partitioning programs; so fixing this will require changes in many places."
Here's the follow-up post too, [Should Filesystems Be Optimized for SSD&#8217;s?]("http://thunk.org/tytso/blog/2009/02/20/2009/02/22/should-filesystems-be-optimized-for-ssds/").

Linus Torvalds, on the other hand thought that SSD manufacturers should make their disc controllers capable of emulating hard discs more accurately,  in the following linked interview, [To SSD or not? Real data..]("http://www.realworldtech.com/forums/index.cfm?action=detail&id=93409&threadid=92678&roomid=2")

As users, we'll just have to wait and see . . . 

> 
                    [quote]If the Vista start point has been moved, (which most people wouldn't need to do anyway), you only need to re-install the MBR, only if you're not using GRUB.            Wrong.

1) Reinstalling the MBR does not help. In fact, there is nothing wrong with the MBR after the Vista start point has been moved (any partitioning program will adjust the partition table in the MBR). So the MBR will have no problem finding the boot sector of the Vista partition. Also the boot sector is still able to find "bootmgr". But "bootmgr" will not be able to find "winload.exe". (bootmgr consults BCD to determine the partition containing "winload.exe" and BCD often labels partitions by the starting sector.)

2) Grub also won't be able boot Vista. Grub just calls the boot sector of the Vista partition. But the problem occurs much later in the booting process at a stage when grub is longer involved.

[/quote]Okay, that makes sense, thank you for the correction. 

> 
                                                 [quote]I don't think GParted actually corrupts Vista,                                 But gparted moves the start point to keep partitions on cylindrical bounds. No modern partitioning program should do that without at least asking the user.[/quote]I don't think GParted touches the start of the Vista partition unless it's told to. Most people leave the Vista at the start of the disc and resize the NTFS partition from the end to make room for Ubuntu when they install.

What do other partition editors do? I think all except whatever the Vista installer uses would default to the partitions starting and ending on cylinder boundaries?
> PS: I would like to mentioned that recent version of gparted have a "round to cylinder" box. Unchecking that box should avoid the problem with resizing Vista.It would be nice to see Partition Editors with an option like 'Optimize for SSD' someday, if the user has an SSD that requires the special partition alignment, rather than just the option to not start and finish on cylinder boundaries.

Regards, Herman :)

---

### Post by Kevbert on 2009-03-28
Partition Magic can cause problems and is probably best avoided, based on my experiences, with version 10.

---

### Post by meierfra. on 2009-03-28
> following link to a blog by Theodore Ts'o, 

I looked at the blog. So it seems that if one uses Raid it is important to have partition aligned correctly. But I'm not sure that it implies that keeping partition  on cylindrical bounds with respect to the 255/63 geometry is a good thing. (Sorry, Raid is one of the things I don't understand)

> I don't think GParted touches the start of the Vista partition unless it's told to. 
I just did a test.  I created  an ntfs partition which did not start on a cylindrical bound. I then used gparted  to  shrink the partition from the end (by  dragging the right end point of the slider to the left).  I clicked on "resize/move" and  gparted informed me of  the actions it is going to take:

Move /dev/sdb5 to the right and shrink it from 7.16GB to 7.10 GB

So I  did not explicitly tell gparted to move the start point, but gparted still was going to move it.  But I indirectly told gparted to move the start point by not  unchecking the "round to cylinder" box.
I doubt that many people would even consider unchecking that box or will pay much attention to the "move /dev/sdb5 to the right" message.
But the situation is much worse if one lets the Ubuntu installer resize a Vista partition. There is no indication that start point of  Vista partition will be moved.

After all the gparted bashing I have been doing, I should point out that gparted is my favorite partitioning program and I'm doing virtual all my partition work with gparted.  

Also almost all partitioning problems are caused by using more than one partitioning program. Different programs  follow different rules and also write the partition table in slightly different ways.
The problem caused by gparted when resizing Vista, is just one example for that. The Vista  partition was created by Vista, so its best to use the Vista diskmanagement to resize it (although  in my experience using gparted  works fine, as long as one unchecks the "round to cylinder" box).

---

### Post by Herman on 2009-03-28
Most people using GParted to resize Windows Vista or Windows 7 to make room for a Ubuntu partition would probably be using the inbuilt partition editing program in the Ubuntu 'Desktop' Live CD. The partitioner in the Ubuntu 'Desktop' Live CD is based on GParted, but it doesn't offer GParted with the same interface which would allow a novice user to be able to make the same series of 'mistakes' as you did, (with respect), sir.
**EDIT: Since this was typed here, I have invested a lot of my own time into testing the behaviour of ****the Ubuntu installer's inbuilt partition editor**** with Windows Vista and Windows 7 and I found not found any problem with ****the Ubuntu installer's inbuilt partition editor**[B] at all.
[/B] 
When a person does decide to pre-partition their hard disk with GParted, and have their partitions already prepared before starting the Ubuntu installer, (that's the way I like to do it), GParted will do what it's told to do.
**EDIT: The above statement is incorrect, GParted (System'-->'Administration'-->'Partition Editor'), can and often does move the start point of the partition without being explicitly told to, if the user fails to remove the check mark from 'round to cylinders' box.**
First, there are two different shaped arrows, one is a double-headed arrow to select a resize only operation, and then there is a four-way arrow the user can use to command a resize and move operation can be selected.
Then, after you click 'Resize/Move', you are told what GParted intends to do.
You have to hit 'Apply' after that, and that only brings up a confirmation window.
"Are you sure you want to apply the pending operations?"
It is only after you hit 'Apply' once again in the confirmation window to confirm that's what you really want to do that GParted will actually start performing any operation.

I haven't tried Partition Magic, so I don't know how many safeguards and obstacles are in the way before Partition Magic will actually do anything. Do you know?

Personally, I wouldn't enjoy using a partition editor with any more safety measures then are already in place in GParted, I think the programmers have it about right.

Still, you do make a good point, it is theoretically possible to somebody who is really clumsy or careless to unintentionally move their Windows Vista or Windows 7 partition without being aware of what is happening if they are not paying any attention to what they are doing. 
That's the equivalent of driving through a give way sign, a stop sign and a red light, if you were a motorist. Yes, "some mothers do 'ave 'em", and I suppose it does happen sometimes.

I think that you were only offering me an example scenario and I don't think you would actually be that careless yourself.


I have had the good experiences with GParted myself.
One computer I fixed last week had Windows Vista in it but it had a damaged hard disk.
First I tried to clone Windows Vista and the recovery partition and another OEM partition with Partimage, but Partimage threw up error messages when it got to the damaged sectors on the hard disk (in the Vista partition), and quit on me.
The new replacement hard disk arrived, one which is double the GB capacity of the old one and tried to use the Linux dd command to clone Vista from the old hard disk to the new hard disk.
The dd command continued in spite of all the errors at the damaged area, and after having run overnight, produced a copy of Vista in the new hard disk.
It booted, but it would only boot in safe mode, and running CHKDSK /F on it borked it.
The recovery partition refused to do anything, claiming it couldn't find a Windows operating system to restore. The recovery CDs installed Windows XP instead of Vista. I phoned the computer manufacturer, to be informed that their 'Recovery Discs' that are supplied with their brand of computers are 'downgrade' discs, and they don't actually restore Windows Vista. (Which the customer has paid for).
The rest of the saga is too long to type out here, and took up a lot of my spare time for several days. 
I finally solved the problem by using GParted to resize the Windows Vista install in the old hard disc first, away from the damaged area of the disc.
Then I used the dd command again and when it was over, Windows Vista booted right up in the new hard disk! :)
I don't know how GParted can read a damaged hard disk better than the dd command, but I am very pleased with GParted. Hooray for GParted!  GParted has never let me down, and I've been using it since its alpha stages.

Of course, the first thing I did after I got the computer working again was to install Ubuntu with Partimage in it and make a Partimage backup of the Vista OS, just in case anything goes wrong with it again.
Actually, an increasing number of people just want Windows deleted, and Ubuntu installed instead, but I do whatever the computer owner wants. There are still a few programs that work in Windows that I don't know the Linux equivalents for. (Not very many though).

---

### Post by florus on 2009-03-28
Vista has a tool for shrinking its own partition. Then you can install Ubuntu into the empty space. Safe and easy.

---

### Post by Herman on 2009-03-28
> I looked at the blog. So it seems that if one uses Raid it is important to have partition aligned correctly. But I'm not sure that it implies that keeping partition on cylindrical bounds with respect to the 255/63 geometry is a good thing. (Sorry, Raid is one of the things I don't understand)I don't understand very much about RAID either, (or care much for it). There are too many different kinds of RAID, (software RAID, hardware RAID, and different kinds of each) to bother with if I wanted to study it for the purpose of helping people with it.

The main reason I've read for Windows Vista and later to have decided to go away from the traditional hard disk partitioning convention of having the start of the first partition beginning at sector 63, (the beginning of the second track of the hard disc), has nothing to do with RAID, (as far as I know).
The reason is to align the partition with the 'pages' and 'blocks' in flash memory and SSD drives.

Here's another link, this might help you understand what I'm on about, (sorry but it's quite a long one if you want to read all the pages of the entire series), [The SSD Anthology: Understanding SSDs and New Drives from OCZ]("http://www.anandtech.com/storage/showdoc.aspx?i=3531&p=2") - AnandTech.

Windows has already decided to alter the start point of their partitions for compatibilty with SSD drives.

The Linux developers are also preparing for the possibility or probability that in the not-to-distant future, many users will begin switching from hard discs for installing operating systems in, to SSD drives, as SSD drives become more affordable.
Hard drives will most likely still be used for storing large amounts of data.

There are already a number of people who like to have Ubuntu installed in a USB flash memory stick or in a USB hard disc drive.
When USB3 comes out next year some time, we may see many more people installing Linux in external USB3 SSD flash memory drives.

Because Ubuntu and other Linux distros and not encumbered by the antipiracy measures that Windows has built into it, it's easy to carry Ubuntu around in a USB device and plug it into any computer. It isn't going to detect that it's in different hardware and self destruct, but rather, Ubuntu can automatically configure itself for the different hardware. That means, people will be able to carry their operating system around in thier pocket.
I think that many people will find that very convenient and Ubuntu will really take off when that happens.

---

### Post by Herman on 2009-03-28
> Vista has a tool for shrinking its own partition. Then you can install Ubuntu into the empty space. Safe and easy. Yes, but Windows 'Disc Manager' has a bad track record for corrupting partition tables. (Unless they've improved it).

Easy, perhaps.

Safe? - No!

[B]EDIT: They may have improved it since I have been paying attention to it. I last used it in Windows XP, the new one for Vista and Windows7 is much nicer, maybe it works okay too. I'm refering to the one in the Installation CDs now.
[/B]

---

### Post by meierfra. on 2009-03-28
> but it doesn't offer GParted with the same interface which would allow a novice user to be able to make the same series of 'mistakes' as you did. 
 
Sorry, but it  seems that you are misunderstanding the situation:

The build in partitioning program for the Ubuntu installer does the same set of "mistakes". (**Edit:  this statement is wrong)**

There  are lots and  lots of cases in the forums where people were not able to boot into Vista  for this reason. gparted is aware of the problem (see item #9 in their [FAQ]("http://gparted.sourceforge.net/faq.php")). Almost everybody  in the ubuntu forums recommends to resize Vista with the Vista disk management. The popular [apcmag howto]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2")  also recommends using the Vista disk management.

I never liked the idea to use the Vista disk management, for example  Vista only lets you shrink the partition by a fairly small amount. So I did a series of experiment and realized that the problem can be avoided by simply unchecking the "round to cylinder" box in gparted.
**Edit:  I'm no longer sure that unchecking the "round to cylinder box" will always be enough to  avoid booting problems**


> it is theoretically possible to somebody who is really clumsy or careless to unintentionally move their Windows Vista or Windows 7 partition without being aware of what is happening if they are not paying any attention to what they are doing.
That's the equivalent of driving through a give way sign, a stop sign and a red light, if you were a motorist. Yes, "some mothers do 'ave 'em", and I suppose it does happen sometimes.

I disagree with this assessment. Only somebody who understands the inner working of the  Vista Boot loader will realize that there is problem with the default gparted settings.  Who would think that moving the start point of the vista partition by less than 8MB would cause problems?

Anyway, both of us are guilty of making mountain out of a molehill. To fix the problem created by the resizing the vista partition one merely has to boot from the Vista CD, choose "Repair Computer" and the CD will reconfigure the Vista Boot loader for  you. Similar things  can happen with Grub after repartitioning the hard drive. The UUID  or "root" of the Ubuntu partition might change and one needs to reinstall grub  or edit menu.lst.

> don't think you would actually be that careless yourself
It's not me who is doing this, I'm just trying to point out what the Ubuntu installer is doing.


> I finally solved the problem by using GParted to resize the Windows Vista install in the old hard disc first, away from the damaged area of the disc.

Brilliant!

---

### Post by Herman on 2009-03-29
So, I re-installed Ubuntu Jaunty Jackalope and while I was doing so I took the time to resize my Windows 7 installation.
I fail to see how anyone could possibly get into any trouble with the Ubuntu installer's partitioner, even if they tried.
Afterwards, my Windows 7 installation booted perfectly, did a chkdsk like it's supposed to and rebooted into Windows 7 without any problems at all.

I don't see a lot of posts in Ubuntu web forums about problems booting Windows Vista after resizing it with Ubuntu's installer or with GParted. I haven't even seen one.
> Anyway, both of us are guilty of making mountain out of a molehill.It's important to me because I will need to make a lot of changes to my website if what you are alleging is actually true, and that would be a lot of work.
I do actually care to make sure that what I tell people is correct and the best possible information available.

I do strongly suspect that you are either exaggerating or misrepresenting the truth, I don't think resizing the NTFS partition from the end will cause the start point to move at all.

---

### Post by Mark Phelps on 2009-03-29
> **Herman said:**
> I don't see a lot of posts in Ubuntu web forums about problems booting Windows Vista after resizing it with Ubuntu's installer or with GParted. I haven't even seen one.


I am really surprised at a comment like this, especially from someone as experienced as you.  You're joking, right?  

In one simple search, in less than 5 minutes, I found over five posts dealing with this problem -- and that was from a search list of over 25 pages!!  Do I actually need to attach the links to the posts to show you that this is a REAL problem??

Do you think that these other people are just making this up?  I could see a magazine doing it in order to sell copy.  But, I really don't think the How-to- geek would make this up.

I recently downloaded the GPArted LiveCD, burnt it, and booted from it -- just to see what new capabilities it had over the version embedded in Ubuntu.  This is what the "Info" icon generates in GParted: "At the moment, GParted is not able to shrink Vista. In fact, it sometimes does and sometimes does'nt! So you need to use ntfsresize in command line to shrink Vista.  Don't try to move it, since bootsector won't be update, and then you couldn't boot Vista anymore."  You can see for yourself if you don't believe me. Click the Info icon and then select Windows Information.

And yeah, while it's a simple matter to fix the boot with a Vista DVD, in the great majority of cases, folks buying machines with Vista preloaded don't even HAVE such a DVD.

And finally, regarding other comments made (I think NOT by you) that moving a Vista partition a little amount couldn't possibly make in unbootable -- tell that to the makers of Acronis True Image!  Their first release for Vista did exactly that: when you restored a Vista OS partition, it aligned the partition differently than the original alingnment, and then, the OS no longer booted.  Folks had to boot from their Vista DVD and run Startup Repair to fix it.  If you don't believe this as well, I'll see if I can find the posts to this effect in the Wilders Security Forum.

> 
It's important to me because I will need to make a lot of changes to my website if what you are alleging is actually true, and that would be a lot of work.
I do actually care to make sure that what I tell people is correct and the best possible information available.


Well, it seems to me that even if only a few people report something as a problem, it really IS a problem.  But, your site is your business and your call.

> 
I do strongly suspect that you are either exaggerating or misrepresenting the truth, I don't think resizing the NTFS partition from the end will cause the start point to move at all.

I can't speak for others, but I only report what I find.  I've never claimed this is a problem ALL the time, only SOME of the time -- and that is based on reports from others.  If ALL of them are lying, then they've fooled me to.

I know for a fact that shrinking a partition in GParted CAN cause it to move automatically because I recently did just that: I shrunk an NTFS partition to make room behind it for another partition.  Before I did this, it was adjacent to the preceding partition.  After I did this, I went into GParted and there was now a gap between it and the preceding partition. So, shrinking it caused the start point to move.

Please, I'm not trying to start a flame war with you; I'm not claiming that this is ALWAYS a problem or even that it's OFTEN a problem, but it is SOMETIMES a problem -- and telling people to be sure to have a Vista DVD or recovery CD lying around JUST IN CASE, is "being safe, not sorry".

---

### Post by Herman on 2009-03-29
Okay then, I'll start by reading all the bug reports, [Bugs in “gparted” source package in Ubuntu ]("https://bugs.launchpad.net/ubuntu/+source/gparted")

If anyone wants to help me, I'm looking for links to bug reports or forum threads related to the Ubuntu installer's inbuilt partitioner. (Not just GParted in the Live CD).

I'm primarily interested in cases where the Windows Vista partition has been 'moved' by the  Ubuntu installer's inbuilt partitioner.
There is only an option to resize it with a numerical spinbox, so there is no opportunity in the installation partitioner for a user mistake. 
There is no 'move' in the installer, as far as I can see.
If it's true that it does 'move' (or re-align) when it's only told to 'resize' then that is definitely a bug, and should be reported to Launchpad.

I'm secondarily interested in links to Bug Reports or threads which say that they told the GParted partitioner in the Ubuntu Live CD, to 'resize' their Vista partition and GParted 'moved' it without being told. (GParted in the Live CD, not the inbuilt one in the installer).

'Resize' means only the right-hand end of the partition will be changed (either to make the partition larger or smaller), and the start point of the partition should not be touched.
(Or at least that's what it's supposed to mean).
You can resize a partition from the left-hand end if you tell GParted to do that, but then it's the user's own idea. 
The problem I'm interested in is if GParted is told to resize the right-hand end and it also resizes the left as well. I still don't think that's likely.

'Moved' means the entire partition including the start point will be moved to somewhere else, including the start point.

Okay, since there are people who feel strongly about this and seem sure this is a problem, I'll invest a lot of my own time now trying to find out more.
I'm searching bug reports, I'm searching thread, and I'm going to run more tests and experiments to see if I can replicate this problem.

Thanks everyone for your help already,
Regards, Herman :)

---

### Post by meierfra. on 2009-03-29
> So, I re-installed Ubuntu Jaunty Jackalope and while I was doing so I took the time to resize my Windows 7 installation.
I fail to see how anyone could possibly get into any trouble with the Ubuntu installer's partitioner, even if they tried.
Afterwards, my Windows 7 installation booted perfectly, did a chkdsk like it's supposed to and rebooted into Windows 7 without any problems at all.

Couple of things to keep in mind:

1)  The start point of the ntfs partition will only be moved if it did not start on cylindrical bounds.

2)  It only cause problems if "BCD" refers to the "Win 7" partition in terms of the starting sector. (Sometimes, but not usually, "BCD"   refers to the Win 7  partition as the  "boot" partition.)

3)  Originally, on my thinkpad, the Vista boot files were actually on a separate lenovo system partition Then I moved the start point of the Vista partition, the system partition  detected  and automatically fixed the problem.

So there are various situation, where resizing a Vista/Win 7 partition will not lead  to any problems. 


>  I don't think resizing the NTFS partition from the end will cause the start point to move at all.

If the NTFS partition does not start on a cylindrical bound and one  uses the default options "round to cylinder", gparted will move the start point. 

> I do strongly suspect that you are either exaggerating or misrepresenting the truth, 

Maybe I am, but I'm just trying to describe the situation to the best of my knowledge.

> I don't see a lot of posts in Ubuntu web forums about problems booting Windows Vista after resizing it with Ubuntu's installer 

There used to be quite a  few such posts, but there haven't been many lately. I assumed this is  due to the fact that everybody  is recommending to use "Vista disk management". But maybe there are some changes in Ubuntu installer.    Today I did an experiment with "Jauntry alpha 2" (which I had lying around), but there was a bug which would not let me resize the Vista partition at all. 
I'll do some testing with Intrepid and Jaundry beta.

---

### Post by meierfra. on 2009-03-29
[QUOTE=meierfra]The build in partitioning program for the Ubuntu installer does the same set of "mistakes".[/QUOTE]

**Until further testing I'm withdrawing this claim**. (Edit: that claim is indeed false)

What I know for a fact:

1.  In the past, resizing a Vista partition with the Ubuntu installer often let to problems booting Vista.

2.  If a Vista partition is shrunk  from the right end with  gparted and the Vista partitions does not start on  cylindrical bound and one does not change the default "round to cyclinder" setting, gparted will move the start point of the Vista partition.

3.  Moving the start point of a Vista partition does lead to problems booting.

I also thought that I had done some testing  proving that the Ubuntu installer (in some cases) moves the start point of the Vista partition.  Well, if I did, those tests would  have been done a few months ago, and I'm not sure anymore whether I actually did those test  or whether the above three facts   just made me  jump to conclusions.

---

### Post by Mark Phelps on 2009-03-29
> **Herman said:**
> 
The problem I'm interested in is if GParted is told to resize the right-hand end and it also resizes the left as well. I still don't think that's likely.

Well, in the case I experienced, I was not using the built-in partitioner, I was using the GParted LiveCD -- so maybe my experience doesn't "count".  

But I can assure you that I was only shrinking the partition (NTFS) on the right side to expand the adjacent Ext3 partition -- and when GParted finished and redisplayed the partition layout, there was a new "gap" on the left side of the NTFS partition that was not there before.

I didn't report it as a "bug" because it really didn't present any problems.  The GParted version was 0.4.3-1.  The NTFS partition was a data partition, not a Vista OS partition.

---

### Post by meierfra. on 2009-03-29
**[SIZE="4"]two of my statements have been plainly wrong.[/SIZE]** 

In fact

4. The Ubuntu installer does not move the start point  of a  Vista/Win 7 partition (unless one specifically request the start point to be moved) 

5.  Versions of  gparted which did not have the "round to cyclinder" box, also to not move the start point of a partition unless specifically asked.

I apologize for spreading wrong information.

This being said, statements 1-3 from my  previous post still remain true, only that I no longer have an explanation for statement 1.

---

### Post by Herman on 2009-03-30
We are all guilty of distorting the truth to make our own arguments look good.

I suppose it would be a very boring world if we all just spoke like robots and only churned out raw factual data without any emotions or feelings.
I'm glad we can have our different opinions and have a good debate or heated discussion, it makes life more fun, and we learn more too.

For my part, I must admit that it is likely that some people using GParted in the Live CD, ('System'-->'Administration'-->'Partition Editor'), might easily make the mistake of accidentally 'moving' their Vista partition as well as resizing it.
I will add warnings in my website where they are needed to try to help people avoid that problem when I update the website for the upcoming Jaunty Jackalope version of Ubuntu.

Thank both you for your help, the information we exchanged here will be put to good use.

Regards, Herman :)

---

### Post by meierfra. on 2009-03-30
> I will add warnings in my website where they are needed to try to help people avoid that problem when I update the website for the upcoming Jaunty Jackalope version of Ubuntu.

This is what I would tell people:

[LIST]
[*]Moving  the start point of a Vista/Win 7 partition with gparted requires a fair amount of additional work to be able to boot Vista/Win 7 again. 

[*] Uncheck the "round to cylincer" box to avoid moving the start point by accident.

[*] Even if the start point of the Windows partition is not moved, there is a (small) chance that you will have  a problem booting  Windows. But this  can usually be fixed  with your Window CD.
[/LIST]


After Mark Phelps mentioned that  gparted does not update the boot sector of an ntfs partition, I actually went ahead and shrunk my Win 7  without uncheching the "round to cylinder box" (the last time I had quit gparted once it told me that it will move the partition)
And indeed, gparted moved that start point and did not update the boot sector.

Now the problem is, that the Windows CD is not able to fix the boot loader if the Boot Parameter Block (BPB) in the boot sector is messed up.
(even fixboot only repairs the boot code in the boot sector, but not the BPB)
Well, I  used "testdisk RebuildBS" and the  BPB was fixed in just a couple of minutes. So to be able to boot Vista/Win 7 after the gparted moved the start point, one first has to run testdisk to fix the BPB  and then use the Window CD to fix  the BCD.

I checked the gparted  forums today, and there were two cases in the last two weeks where exactly this problem occurred. In instead of using testdisk, the  problem was fixed by using an hex editor to manually edit the BPB.

> I'm glad we can have our different opinions and have a good debate or heated discussion, it makes life more fun, and we learn more too.

I agree, but there was a point where  the discussion got a little bit too heated for my taste :( Luckily we all calmed down and turned the whole thing into a good learning experience :P

---

### Post by Herman on 2009-03-31
I put a warning message in a big yellow box for Windows Vista and Windows 7 users in ['Pre-install Page]("http://www.users.bigpond.net.au/hermanzone/p17.htm")'  --> '[Help on Partitioning]("http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning")'.

I put another warning message in a big yellow box for Windows Vista and Windows 7 users in '[Hardy Heron Beta / Gutsy Gibbon Graphical Installation C]("http://mywebsite.bigpond.net.au/dfelderh/p22.html")', (even though it's not really about dual booting with Vista or Windows 7).

My other installation pages are either about the 'Alternate' CD or they show the use of the Ubuntu installer's inbuilt partitioner.

How do those look?

I already have some new pages I'm working on for Jaunty Jackalope which will be much different from those old pages. I'm not uploading them until closer to Jaunty Jackalope's release date. I'll be doing some extra work on those now. 
It will be a few days before I'll have time to run any more tests and experiments myself.

Thanks for all your work looking for links. I have also browsed GParted Live CD's web forum plus Parted Magic's web forum and Ubuntu Web forums and Launchpad for bug reports but I only had time for a quick look and I don't have time to read each thread, only scan the titles. If someone has not used a descriptive title to their thread or bug report I would have overlooked it. 

Hopefully we can work together and prevent a few more incidents of this kind. Not everyone uses my website of course, but at least the people who do will see the new warning message, and it might help.

Thanks again,
Regards, Herman :D

---

### Post by kestrel1 on 2009-03-31
Herman, Looks good to me.
Something I find easier to read personally is if a web site is more central to the page, rather than at the edge.
I have my site central & find it easier to navigate & read.
[http://www.kcsdorset.co.uk]("http://www.kcsdorset.co.uk")

---

### Post by meierfra. on 2009-03-31
> If you do really need to move the start of a Windows Vista or Windows 7 partition for some reason, you can fix the problem of not being able to boot anymore merely by booting from the Vista CD, choose "Repair Computer" and the CD will reconfigure the Vista Boot loader for you.

Not quite right.    Before  using the Vista CD, one needs to fix the  boot sector of the Vista/Win 7 partition (Edit: this is only necessary in a small number of cases). Here are instruction how to use testdisk   to fix the boot sector: 
> 

[LIST]
[*]  **From Ubuntu**

Download the [testdisk-6.10.linux26.tar.bz2 package]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") to your desktop, open a terminal and do:

```
cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```

[*]  **Or from the gparted LiveCD**

Open a terminal and do

```
testdisk  /dev/sda
```
[/LIST]

In either case,  /dev/sda needs be replaced by the device name of Hard drive containing  your Windows partition. Often it is /dev/sda but you should double check via "sudo fdisk -lu".

Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition and choose
"boot"
"RebuildBS"
"Write"
Press "Y" (to confirm writing a new boot sector)

then press "q" a few times to quit testdisk.

(**Edit: ** In stead of using testdisk, one can also use 

```
bootrec /fixboot
```
 from the Vista/Win 7 CD to repair the boot sector (although in my experience testdisk has a slightly higher chance  to succeed))


 


Otherwise, it looks great.

---

### Post by Mark Phelps on 2009-03-31
Meierfra:

That's a lot of useful info.  Thanks.

Seriously ... this is scary -- even the infamous Vista DVD can't fix this!!

Since you were able to repair the problem with testdisk, do you know if it can fix the Vista boot problem as well, in other words, is there a way for our Linux folks to fix their Vista boot problems WITHOUT having to scrounge up a Vista DVD?

If that's the case, your comments rolled into a Tutorial would be a great thing to be able to point to for those folks who installed Ubuntu and now come here claiming that "Ubuntu broke their PC".

---

### Post by meierfra. on 2009-03-31
> Do you know if it can fix the Vista boot problem as well, in other words, is there a way for our Linux folks to fix their Vista boot problems WITHOUT having to scrounge up a Vista DVD?

As far as I know there is no Linux program which can edit the Vista BCD. I tried deciphering the BCD  a couple of times, but gave up. Two BCDs which contain the exact same data can look completely  different. So I was not able to figure out what is stored where and how. Also searching the Web for information didn't yield anything.

> Seriously ... this is scary -- even the infamous Vista DVD can't fix this!!

Not being able to  fix the BootParameterBlock is a serious flaw in all the Windows CD. (Edit:  fixboot is much better in  repairing the BPB than I though. Still testdisk does a better jib) And it makes  no sense, fixing the BPB is essentially trivial (My BootInfoScript could  do it, I just would have to add a couple of lines of code)
For the same reason, it makes no sense at all that "gparted" does not update the BPB. (edit: actually gparted updates the boot sector most if the time)

But on the bright side, fixing the problem with testdisk  only takes a few minutes. So as long as one knows what is going on, it isn't really scary.

---

### Post by Herman on 2009-04-01
Okay, I did find three of threads in GParted LiveCD Web Forums about this, I must have been looking in the wrong section of the forums last time.

Also, I have moved a lot of data and some Linux installations to get one hard disk tidied up and empty just for Windows 7. 
Windows 7 booted up okay yesterday I am sure. 
I didn't even touch the Windows 7 partition and I just wanted to boot it to verify that it does boot before proceeding with my first experiment and already it won't boot!

So far I'm using Ubuntu's GParted, and not the GParted in the Ubuntu installer.

Hmmm . . . :-k

UPDATE: All fixed! I simply booted a [Windows Recovery Disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and ran CHKSDK /F and BOOTREC /FIXBOOT , but most likely the problem mine had in this particular instance wasn't the same problem as we're talking about. 
Now I'll be ready to try some experiments moving Windows 7 around with GParted, as soon as I get some sleep. 
This actually only took me a few minutes to fix, but I had to do a lot of other things that have nothing to do with computers in between finding out it was 'borked' and getting a chance to do anything about it.

---

### Post by Herman on 2009-04-04
:smile: Alright, I have spent most of my time for the past two days installing both Windows 7 and Windows Vista, partitioning with GParted and installing Ubuntu Jaunty Jackalope and watching what happens.

I have tried partitioning with the GParted in the Jaunty Jackalope Live CD, ('System'-->'Administration'-->'Partition Editor'), and resized Windows Vista and Windows 7 partitions with the 'round to cylinders box' both checked and unchecked.

I have installed Ubuntu Jaunty Jackalope with the Ubuntu installer's inbuilt partition editor using 'Use the largest continuous free space', 'Install them side by side, choosing between them at each startup', and 'Manual partitioning (advanced)'.

I have not had any problems with the Ubuntu Jaunty Jackalope Alpha 6 installer's inbuilt partition editor at all. No matter what I did, it always resized Windows Vista or Windows 7 for me from the left only, and didn't move the start of the partition at all.
Each time, Windows Vista or Windows 7 booted right up without any problems at all when the Ubuntu installer's inbuilt partition editor was used.

As far as Gnome Partition Editor, (GParted), ('System'-->'Administration'-->'Partition Editor') goes, I had no problem with that either, as long as the tick mark is removed from the 'round to cylinders' checkbox.

When the Windows Vista or Windows 7 partition's start point did get moved, (by resizing the operating system partition without removing the tick mark from the 'round to cylinders' checkbox, Windows wouldn't boot.

When I didn't remove the tick mark, GParted did tell me what it was about to do before I clicked 'Apply', and 'Apply' again at the 'Are your sure you want to ... ?' to confirm. 
> Are you sure you want to apply the pending operations?
Editing partitions has the potential to cause LOSS of DATA.
You are advised to backup your data before proceeding.
[RIGHT]Cancel      Apply[/RIGHT]
I would have to agree though, that many new users would fail to understand the importance of that decision. Probably it would be a good idea if there was something extra added to the message there. I'm not sure how much work that would be, but maybe they should also mention boot loader problems.
 
However, all the times I tried it, (quite a few times over the last two days or so), 'Startup Repair' in  [Windows Recovery Disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") fixed the problem(s) pretty much instantly and automatically for me. Maybe I'm just lucky.
A few times I was given an error message and told that 'Startup Repair' couldn't fix my problems and would I like to send a report to Microsoft (recommended). I just clicked 'No' and went to a command prompt and ran CHKDSK /F  and BOOTREC /FIXBOOT and if 'Startup Repair on it's own wasn't enough, that fixed it every time for me.

I also tried running 'Startup Repair' with and without GRUB in the MBR just in case that might make any difference. It didn't seem to, at least not in my computer when I tried it.

For some reason, the [Windows Recovery Disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")'s 'Startup Repair' seems to work better tban the same thing in the Windows 7 installation disc, I don;t know why, maybe I'm just imagining that. Thanks to ComputerGuru from Neosmart (EasyBCD) for making that available for us.

Maybe I'm just lucky, but that's what happened to me, at least with my computer. 
It doesn't seem to be a very bad problem to me, but I will certainly make sure I explain it and emphasize it as I'm updating my website when I update it for Ubuntu Jaunty Jackalope. Thanks again for bringing this matter to my attention, (even though I didn't like reading about it at first). 

Regards, Herman :)

---

### Post by meierfra. on 2009-04-04
I'm not surprise that you didn't have problems when the  start point was not moved.  (problems in that case seem to be infrequent) 


But I'm really surprised  that you did not have to fix the boot sector, when you moved the start point.  

Could you do me a favor and  move the start point of your Win 7 partition one more time?  But don't fix the boot loader immediately, instead run "testdisk RebuildBS" and see whether the Rebuild boot sector is different from the original boot sector.

---

### Post by meierfra. on 2009-04-04
Actually you don't have to redo the experiment. 

After you move the start point of the Win 7 partition and tried to boot Win 7, what kind of error messages did you get?

1)  Blue screen of death saying something like "winload.exe missing"

2)   "Starting Up"

3)   A disk read error occured. "press ctlr alt del"

4)  Other

---

### Post by Herman on 2009-04-04
Okay, that should be interesting.
Originally I had Windows 7 in a single partition install because I installed it with some other operating systems in the same hard disk.
After I copied the other operating systems to another disk and tried installing it installing Windows 7 by itself, I found out that it defaults to a two-partition installation.
Apparently it's perfectly normal for Windows 7 to install  in two partitions by default, [_Windows 7 Partitions_]("http://www.sevenforums.com/installation-setup/2162-windows-7-partitions.html"), actually, I'm not even sure if resizing the Windows system partition will affect it much, I think Microsoft6 has done a better job with Windows 7, I'll try it shortly, (it will take me some time).

 It has a separate boot partition starting in sector 2048, and ending in sector 411647, (200MiB).
Windows 7 System partition typically starts in sector 411648.

It looks like both have a boot sector, but they're each quite a bit different, 

```
herman@amd64hh:~$ sudo dd if=/dev/sda1 count=1 | hexdump -C
[sudo] password for herman: 
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.015488 s, 33.1 kB/s
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 3f 06 00 00 00 00 00  |.........?......|
00000030  aa 42 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.B..............|
00000040  f6 00 00 00 01 00 00 00  27 61 2b 08 7a 2b 08 ce  |........'a+.z+..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
herman@amd64hh:~$ sudo dd if=/dev/sda2 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.0117449 s, 43.6 kB/s
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 48 06 00  |........?....H..|
00000020  00 00 00 00 80 00 80 00  f8 a7 4d 09 00 00 00 00  |..........M.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  00 4d 27 ac 88 27 ac ec  |.........M'..'..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
```

---

### Post by meierfra. on 2009-04-04
> It has a separate boot partition starting in sector 2048, and ending in sector 411647, (200MiB).

Now it all makes sense:  the problem with the boot sector will only  occur if you move the start point of the boot partition.   Moving the start position of the main Win 7 partition can be  easily fixed with Rescue CD.

---

### Post by kestrel1 on 2009-04-04
Thanks for all the info Herman, you have been busy :lolflag:

---

### Post by meierfra. on 2009-04-04
> It looks like both have a boot sector, but they're each quite a bit different, 

Every ntfs partition comes with a boot sector. The first 80 bytes form the  Boot Parameter Block and contain information about the file system (starting sector of the partition, size of the partition, location of the MFT,....)  The BPB obviously depends on the actual partition.

The remaining bytes contain  the boot code and are the same for any ntfs partition (well not quite, it  can be either the XP boot code, or the Vista/Win 7 boot code)


> I'm not even sure if resizing the Windows system partition will affect it much, 

I'm confused. Then you did  your test:  did you move  the start point of the main windows partition or the small 200 partition ? Or  did  you only have one Win 7 partition at the time

---

### Post by Herman on 2009-04-04
> I'm confused. Then you did your test: did you move the start point of the main windows partition or the small 200 partition ? Or did you only have one Win 7 partition at the timeI was experimenting with Windows 7 in one single partition when I started, not realizing it wasn't a typical installation.
Then I re-install it in an empty hard disk, and I was surprised when I saw that it had installed itself in two partitions.
Later I was using Vista for a while, then I re-installed Windows 7 when I thought I was finished. But there's still more to do.

I have resized Windows 7's system partition, and on reboot I'm getting 'Windows Boot Manager", "Windows failed to start. A recent hardware or software change might be the cause . . . "

---

### Post by Herman on 2009-04-04
Boot Windows 7 CD --> "repair your computer', (searching for Windows installations)-->' Windows has found problems with your computer's startup options. Do you want to apply repairs and restart your computer?' --> Repair and restart.

. . . and it reboots into Windows, but first it does a CHKDSK, (as it should), and reboots again . . .

 . . . and I'm in Windows 7. No worries! :)

Now, to reboot into Ubuntu and take a look at the bootsectors  for meierfra.

I presume this 'Startup Repair' must be fixing the boot sector(s), at least when it's a single partition installation. 
When it's a two -piece install the boot sector probablt doesn't matter.

As I said earlier, I had to run BOOTREC /FIXBOOT sometimes, (only if 'Startup Repair' coiuldn't fix it). I think BOOTREC /FIXBOOT would fix the boot sector.
> Thanks for all the info Herman, you have been busy:) Hello kestrel1**, **Yes and I'm getting tired too, I'll need some sleep very shortly.
I checked out your websitre, I'm impressed!

---

### Post by Herman on 2009-04-04
```
herman@amd64hh:~$ sudo dd if=/dev/sda1 count=1 | hexdump -C
[sudo] password for herman: 
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000404941 s, 1.3 MB/s
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 3f 06 00 00 00 00 00  |.........?......|
00000030  aa 42 00 00 00 00 00 00  02 00 00 00 00 00 00 00  |.B..............|
00000040  f6 00 00 00 01 00 00 00  27 61 2b 08 7a 2b 08 ce  |........'a+.z+..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
herman@amd64hh:~$ sudo dd if=/dev/sda2 count=1 | hexdump -C
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000484308 s, 1.1 MB/s
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 9a 5f 06 00  |........?...._..|
00000020  00 00 00 00 80 00 80 00  78 f9 7a 07 00 00 00 00  |........x.z.....|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  00 4d 27 ac 88 27 ac ec  |.........M'..'..|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f fc f3 aa  e9 5f 01 90 90 66 60 1e  |(........_...f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 cd  10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk read error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 42 4f 4f 54 4d  |occurred...BOOTM|
000001b0  47 52 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |GR is missing...|
000001c0  42 4f 4f 54 4d 47 52 20  69 73 20 63 6f 6d 70 72  |BOOTMGR is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
00000200
herman@amd64hh:~$ 


```There you are meierfra, I'll be back in a few hours. 
If it helps I can re-install Vista and try again to see what changes get written to the boot sector, or try to find out what program's fixing it.

Regards, Herman :)

EDIT: D-oh, you wanted me to run  run "testdisk RebuildBS", I'll move Windows 7 again after some sleep and then I'll  run "testdisk RebuildBS" and dd the boot sectors again for you. Sorry, I must be too tired.

---

### Post by Herman on 2009-04-04
[COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Urgent! Booting problem after resizing partitions]("http://ubuntuforums.org/showthread.php?t=1116207")

I just thought I'd add a link that's relevant to this thread's title. :)

---

### Post by meierfra. on 2009-04-04
I did my own series of test today, and gparted did update the boot sector every single time.   So  it seems the problem I describe in  post #33 is an exception, and not the rule. Unfortunately, I  have no idea  why gparted malfunctions in those exceptional cases.

I also tested how well "bootrec /fixboot" repairs the boot parameter block.   I used "dd" to mess up the BPB on purpose, and in 4 out of 5 cases "bootrec /fixboot" was able to fix the BPB. But in one case it failed. 

So both gparted and fixboot performed better than I expected.
I guess  many of my opinions are formed by working cases in the ubuntu forums. But of course   only the cases where things go wrong make it to the forums.

Anyway, I will be much less hesitant to recommend  gparted for resizing Visa/Win 7 than before we had the discussion in this thread. Although Vista disk management is still my preferred choice.

---

### Post by Herman on 2009-04-04
Rats!
I just spent some more of my time resizing Windows 7 back to the way it was originally, with the start point back in 411647 and was getting ready to take a look at the boot sector again. First I tried to boot it to see what error screen I would get but it fixed itself without even waiting for me to insert a CD and reboot! It ran 'Startup Repair', I was so surprise I opened the CD drive to check, (it was empty), so probably it was running from the 'boot' partition. Then it rebooted and ran CHKDSK, rebooted again and ran a validation programs where I has to type in my product key, and now Windows 7 is back to normal.
I didn't even have a chance to use TestDisk on the boot sectors.

Actually, what part of the boot sectors are we worried about anyway, and why do we need TestDisk? GParted does update the boot sector, probably not the boot loader area of it but it does update some part of it. If you check your details file from GParted you'll see that it does run a command for the boot sector, 
"updating boot sector of ntfs file system on /dev/sda3  00:00:04    ( SUCCESS )",                [FONT=Bitstream Vera Sans Mono]
[/FONT]```
echo c5fa3f00 | /usr/bin/xxd -r -p | /bin/dd conv=notrunc of=/dev/sda3 bs=1 seek=28
```If your GParted isn't running that command or that command isn't working for you then maybe that's where to look for a problem?

EDIT: Sorry meierfra, I was interrupted with a phone call and didn;'t look before posting this and see that you had also just posted.
> I did my own series of test today, and gparted did update the boot sector every single time. So it seems the problem I describe in post #33 is an exception, and not the rule. Unfortunately, I have no idea why gparted malfunctions in those exceptional cases.
> I guess many of my opinions are formed by working cases in the ubuntu forums. But of course only the cases where things go wrong make it to the forums.Thanks for also taking some time out for testing.

I don't know why some people (in web forums) have such extreme problems, but there could be lots and lots of reasons as you can probably imagine as well as I can, both hardware and software related.

---

### Post by meierfra. on 2009-04-04
> First I tried to boot it to see what error screen I would get but it fixed itself without even waiting for me to insert a CD and reboot! It ran 'Startup Repair',

If you don't resize the boot partition,  then the boot partition is able to to carry out the repairs automatically.

> I didn't even have a chance to use TestDisk on the boot sectors.
That's ok. Actually  you can still run testdisk, since (as far as I know)  the   Automatic repair does not fix the boot sector. 

> Actually, what part of the boot sectors are we worried about anyway
Bytes 28-31 (the starting sector of the partition is stored here)


> and why do we need TestDisk? 
If  bytes 28-31 are wrong  and one tries to chainload the  boot sector from Grub, one gets the "Starting Up" error.
One can fix "bytes  28-31" with "bootrec /fixboot" but I think testdisk has a higher chance to succeed.

> echo c5fa3f00 | /usr/bin/xxd -r -p | /bin/dd conv=notrunc of=/dev/sda3 bs=1 seek=28

Yup, that will update bytes 28-31

Did you resize /dev/sda3?  Whats on /dev/sda3?

> updating boot sector of ntfs file system on /dev/sda
Today I got this message all the time. But I don't recall seeing it the last time, when the boot sector was not updated.

---

### Post by Herman on 2009-04-06
> Anyway, I will be much less hesitant to recommend gparted for resizing Visa/Win 7 than before we had the discussion in this thread. Although Vista disk management is still my preferred choice.Yes, I quite like the GUI of the partition editor in the Vista and Windows 7 installation CDs, but I have only tried it a little so far.
At first glance it doesn't look like it has anywhere near the functionality that GParted has, but it's pretty to look at.

It doesn't seem as if any partition editor is completely safe for new users or the uninformed though. 

Interestingly, I have happened across the following linked web page, (with links to further web pages), which explains an incompatibility between Windows XP's partitioner and Windows Vista and later partition editing programs, [[FONT=Arial Black]**Vista Quirks and Bugs.**[/FONT]]("http://www.multibooters.co.uk/quirks.html")
> [FONT=Arial]If you have conventional partitions and you delete the first logical in an extended partition and let Vista recreate it during the install of itself, then any other logical in that extended [/FONT][FONT=Arial]partition [/FONT][FONT=Arial]will be deleted. Using the Vista tools manually can also produce the same results. If you have Vista made logical partitions and you use XP tools to create a new logical after a Vista one, then you will loose all Vista logicals back to any other old style logical or to the start of the extended partition. I&#8217;ve seen a few other circumstances where logicals disappear, so advisable not to mix and match at all.[/FONT][FONT=Arial] [KB article]("http://support.microsoft.com/kb/923332")

[/FONT][FONT=Arial][The case of the disappearing partitions]("http://www.dcr.net/%7Ew-clayton/Vista/DisappearingPartitions/DisappearingPartitions.htm")

originally posted by meierfra. in post #19
[/FONT]> Also almost all partitioning problems are caused by using more than one partitioning program. Different programs follow different rules and also write the partition table in slightly different ways.+1

Does Windows have any warnings in their Vista partition manager or installation CD for newbies which explains this problem to their users? 
It would be very scary for any computer user to have an entire partition suddenly disappear along with all the data it contains!
That would be much worse that only loosing the use of the boot loader.
And how would one go about recovering the data (and the boot), after such an event?

I'm also wondering if this can happen if other partition editors (such as GParted) are used before of after Vista's Disc Management or installer's partitioner?

Looks like another lot of experiments, testing and re-installing will be ahead for me. :-k
[FONT=Arial]

[/FONT]> Did you resize /dev/sda3?  Whats on /dev/sda3?That was my original Windows 7 partition number. The first time I installed it I had some other operating systems already on the hard disk, and it ended up getting partition number 3 and installing itself into just one partition as Vista does.
The next time I re-installed it I had moved the other operating systems to a different hard disk so Windows 7 had an empty disk and that was the fisrt time I noticed it installs with a root and system partitions. I later found out that installing in two partition is normal for Windows 7.
[FONT=Arial] 
[/FONT]

---

### Post by meierfra. on 2009-04-07
> At first glance it doesn't look like it has anywhere near the functionality that GParted has.

Yes,  disk management is nowhere nearly as capable as gparted.  That's why I recommend Vista/Win 7 disk management for one and only one on thing: Resizing Vista/Win 7 partitions.  (Use gparted for everything  else)

> And how would one go about recovering the data (and the boot), after such an event?
Nothing has happened to the data, only the partition table has been messed up. So testdisk "deep search" should be able to fix  the problem. 

> I'm also wondering if this can happen if other partition editors (such as GParted) are used before of after Vista's Disc Management or installer's partitioner?
I would be surprised if gparted would have a problem with an usual hidden sector number in a logical partition. (But then, it wouldn't be the first time I'm surprised in this thread)

---

### Post by meierfra. on 2009-04-11
Herman: Check out this thread:

[http://ubuntuforums.org/showthread.php?p=7056210](http://ubuntuforums.org/showthread.php?p=7056210)

"gparted" did not  update the boot sector and "fixboot" failed to repair  it.

---

### Post by kallenes on 2009-04-12
acronis disk director 10 works like a charm - tested on vista x32.

g-parted could give you a prob, where you would have to repair your vista boot.

---

### Post by Herman on 2009-04-12
> Herman: Check out this thread:
[http://ubuntuforums.org/showthread.php?p=7056210](http://ubuntuforums.org/showthread.php?p=7056210)
"gparted" did not  update the boot sector and "fixboot" failed to repair  it.Thank you, meierfra, and well done! 

I wonder how that problem can happen though?

I checked GParted Live CD's [ChangeLog]("http://svn.gnome.org/viewvc/gparted/trunk/ChangeLog?view=markup").
GParted Live CD has had full NTFS support since 23/11/2004.
GParted Live CD had the code for updating the ntfsbootsector added (after first sector has been changed, to let windows boot correctly afterwards), on 04/09/2006.

GParted versions from 0.3.5 and newer are supposed to be okay with Vista.
GParted 0.3.5 is the version that's in Ubuntu Hardy Heron.

An important question to ask the user would be "what version of GParted were you using?".
There are a lot of old versions of GParted floating around on old utilities disc CD's and so on. 
It's easy to check the version number by clicking 'Help'-->'About', while in GParted.


Further from that though, I have also looked in the GParted [all bugs]("http://bugzilla.gnome.org/buglist.cgi?query_format=advanced&short_desc_type=allwordssubstr&short_desc=&classification=Other&product=gparted&component=gparted&long_desc_type=substring&long_desc=&status_whiteboard_type=allwordssubstr&status_whiteboard=&keywords_type=allwords&keywords=&bug_status=UNCONFIRMED&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED&bug_status=NEEDINFO&bug_status=RESOLVED&bug_status=VERIFIED&bug_status=CLOSED&emailassigned_to1=1&emailtype1=substring&email1=&emailassigned_to2=1&emailreporter2=1&emailqa_contact2=1&emailcc2=1&emailtype2=substring&email2=&bugidtype=include&bug_id=&chfieldfrom=&chfieldto=Now&chfieldvalue=&cmdtype=doit&order=Reuse+same+sort+as+last+time&field0-0-0=noop&type0-0-0=noop&value0-0-0=") list and I did find - [Bug 379482]("http://bugzilla.gnome.org/show_bug.cgi?id=379482") – move/resize ntfs partition containing Windows Vista makes Vista unbootable.

By reading that page I can see that this problem still was reported a few times even when using GParted versions after 0.3.5.

Meierfra, maybe your boot_info script will help.
```
Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 98304. But according to the info from fdisk, 
                       sda1 starts at sector 63.
```Where did the number 98304 come from I wonder?
Normal Vista disc partitioning would have made the Vista partition start in sector 2048.

Regards, Herman :confused:

---

### Post by meierfra. on 2009-04-12
> By reading that page I can see that this problem still was reported a few times even when using GParted versions after 0.3.5.

Yes, but the newer case don't seem to be due to a bug. 
The "winload.exe" error will occur  with any version of gparted if  the start point  of the vista partition is moved. To avoid that error, gparted would have to edit the "BCD".  Of course, it would be nice if gparted would do  that, but updating the boot loader is not really the job of a partitioning tool. Similarly, I wouldn't expect gparted to edit "menu.lst"  and/or reinstall grub if UUID's have changed or partitions have been deleted.

Of course, there are cases where the start point is moved accidentally due to the "round to cylinder" box.  But I'm not sure that one call this a  bug, either

The "starting up" up error is different. It occurs,  if the hidden sector number in boot sector is not updated.  That really is a bug and should not happen.  I'm not 100% sure, but I think it  still can  happen even with the newest version of gparted.  


```
Where did the number 98304 come from I wonder?
```

Maybe there was small utility partition in front of the Vista parition, which  got deleted. 


> An important question to ask the user would be "what version of GParted were you using?".
Good idea,  I'll post in the thread.

---

### Post by Herman on 2009-04-14
I still couldn't get GParted to fail to update a Vista boot sector after several more Vista partition movements.
In my computer Windows 'Startup Repair' always seems to be able fix the Windows bcd boot loader by itself in a few minutes. 
I would still like to know what circumstances it takes to get GParted to mess up.

I found it interesting that the back up the boot sector was being also updated somehow, and it seems that Windows 'Startup Repair' is doing that. 

In order to try to simulate the 'Starting up . . . ' error that you're talking about, meierfra, I moved Vista and then took a dd copy of the backup boot sector right away before I did anything else.
Then, I dd'd the backup bootsector, (which still had the old boot sector in it), to overwrite the new boot sector that GParted had just updated. 
Sure enough - 
```
Starting up . . . 
 _
```The Windows Repair CD wouldn't look at it, saying I should use a CD for my version of Windows. 

I could have used TestDisk as you advise, meierfra, and I know that will work. I really like TestDisk, it saves a lot of people's bacon and makes life a lot easier for all of us.

This time though, I decided to try out the command from GParted that I mentioned earlier.
```
sudo su
# echo 3f00000000 | /usr/bin/xxd -r -p | /bin/dd conv=notrunc of=/dev/sda1 bs=1 seek=28
```Where: The first sector of the Vista partition is located in sector 63 according to 'sudo fdisk -lu'.

That fixed it instantly.

Most of the time GParted will probably move Windows to sector 63.
If it starts in some other sector then it will probably still be quicker to use TestDisk. The average computer user might have difficulties getting the input number right. 
It's simple to enter the number 63 into a program like Gbase and get the '3f', but the syntax of where to put the zeros and how many of them are needed isn't perfectly clear to me yet. I cheated and got the number 3f00000000 from GParted's log file. The above command is a lot quicker providing who-ever makes up the command is confident about the hex number. 

Regards, Herman :)

---

### Post by Herman on 2009-04-15
:) I've got it!
This will be the fastest and easiest way to fix the Vista boot sector if someone accidentally moved the start of a Vista partition and they have the 'Starting up . . . ' error.
```
sudo apt-get install gbase
``````
sudo fdisk -lu
```Look in the fdisk output for the number of the partition's start sector. 
For example, say the fdisk ouput might show the NTFS Vista partition starts at: [FONT=Bitstream Vera Sans Mono]265152825[/FONT]

Start Gbase, (Base Converter).

Type that start sector number in the 'Dec' field in Gbase,
[IMG]http://mywebsite.bigpond.net.au/dfelderh/004.k-series.png[/IMG]

(i) Input the sector number ([FONT=Bitstream Vera Sans Mono]265152825[/FONT]) and read the hex value output ([FONT=Bitstream Vera Sans Mono]FCDE939[/FONT]).

(ii) make that number into an eight character hex value, 
      by adding some zeros before it if necessary. -  [FONT=Bitstream Vera Sans Mono]0x0[/FONT][FONT=Bitstream Vera Sans Mono]FCDE939[/FONT]

(ii) Separate into 'words' (pairs of bytes) -  [FONT=Bitstream Vera Sans Mono]0[/FONT][FONT=Bitstream Vera Sans Mono]F CD E9 39[/FONT]

 (iii)  invert the order of the words  - [FONT=Bitstream Vera Sans Mono]39 E9 CD 0F[/FONT]

(iv) remove the whitespaces - [FONT=Bitstream Vera Sans Mono]39E9CD0F[/FONT]

(v) Use it in the xxd command,
```
sudo su
``````
echo 39E9CD0F | /usr/bin/xxd -r -p | /bin/dd conv=notrunc of=/dev/sda1 bs=1 seek=28

``````
exit

```

---

### Post by meierfra. on 2009-04-16
> This will be the fastest and easiest way to fix the Vista boot sector

Are you sure? :) I timed myself. It took me  80 seconds to install testdisk via "sudo apt-get install testdisk", run "sudo fdisk -lu" to determine the windows drive and then use testdisk rebuildbs to fix the boot sector.

I then tried a modification of   your method:

```
sudo fdisk -lu  #  returns the starting sector  265152825

printf %x 265152825   # returns fcde939

echo 1c: 39e9cd0f | sudo xxd -r - /dev/sda1
```

and after practicing a few times was able to do it in 45 seconds  :)
(I'm sure you can do it faster, since I'm unable to type more than three letters without a typo)


On a more  serious note:  For use in the forums, I consider  testdisk to be  safer.

Also I had another case today where the boot sector needed to be fixed:

[http://ubuntuforums.org/showthread.php?t=1126869](http://ubuntuforums.org/showthread.php?t=1126869)

---

### Post by Herman on 2009-04-16
Hey, that's neat! 
> printf %x 265152825   # returns fcde939 Thanks, meierfra! Cool! :D

If you think TestDisk is safer, that's fine.
I was thinking that if a user was quite new and unsure of themselves then it might be easier if they were getting help from someone experienced, to just give them a command that they can copy and paste into a terminal and just press 'Enter'. (No knowledge necessary on the part of the user). Some people might find TestDisk a new experience. But as long as it gets fixed and the user is happy at the end of it, all is well. 

I was wishing I could think of a program that could change the sector number right into the format needed for the input for the xxd command in one step. I looked for one but couldn't find anything.
It's amazing how often I find information I was looking for earlier after I have given up searching for it and I'm looking up something  else related. While I was googling for more info on a decimal to hex conversion program I came across this bug report from GParted Live CD, [Bug 574389 &#8211; No /usr/bin/xxd file]("http://bugzilla.gnome.org/show_bug.cgi?id=574389").

It's quite possible, and even likely I think, that this bug is restricted to one version of GParted LiveCD and doesn't appear in GParted in Ubuntu Live CDs at all. I think Ubuntu would always have xxd because it's a dependancy of vim-common. Unless there's more than only the one problem, which I also hope isn't the case.
I note that the How-To Geek's instructions your user used in your most recent case advised people to use the GParted Live CD, (and normally there's nothing wrong with that).
I'm still interested to find out what version of GParted people have used before discovering this problem, and what CD is was on.
I don't think this problem can possibly come from any Ubuntu CD or GParted installed in Ubuntu, at least I hope not.

---

### Post by unutbu on 2009-04-16
> **Herman said:**
> 
I was wishing I could think of a program that could change the sector number right into the format needed for the input for the xxd command in one step. 

This was just for fun; I'm not sure you'll find this very practical.

twist.py
[PHP]#!/usr/bin/env python
import sys
h=hex(int(sys.argv[1]))[2:].rjust(8,'0')
print(''.join([c+d for c,d in zip(h[-2::-2],h[-1::-2])]))
[/PHP]

```
% twist.py 265152825
39e9cd0f
```

Or, as a one-liner:  ;)
```
python -c "import sys;h=hex(int(sys.argv[1]))[2:].rjust(8,'0');print(''.join([c+d for c,d in zip(h[-2::-2],h[-1::-2])]))" 265152825
```

---

### Post by Herman on 2009-04-16
:D Hey unutbu! Those are great! 
I wish I could write scripts and code like you fellows. <respect>.

Regards, Herman :D

---

### Post by duyibo on 2009-07-22
Partition Wizard Home Edition is a free partition manager designed by MT Solution Ltd. It supports 32/64 bit Windows Operating System including Windows XP, Vista and Windows 7. Home users can perform complicated partition operations by using this powerful but free partition manager to manage their hard disk partition such as Resizing partitions, Copying partitions, Create partition, Delete partition, Format partition, Convert partition, Explore partition, Hide partition, Change drive letter, Set active partition and Partition Recovery.

[http://www.partitionwizard.com](http://www.partitionwizard.com)

---

### Post by duyibo on 2009-07-22
Hey guys! I&#8217;ve found a free 64 bit Windows partition manager by accident. I downloaded it and used it. This software was amazing and easy to use. The most important is that it is free here I would like to share it with you. Following are copied from the website:

Partition Wizard Home Edition is a free partition manager designed by MT Solution Ltd. It supports 32/64 bit Windows Operating System including Windows XP, Vista and Windows 7. Home users can perform complicated partition operations by using this powerful but free partition manager to manage their hard disk partition such as Resizing partitions, Copying partitions, Create partition, Delete partition, Format partition, Convert partition, Explore partition, Hide partition, Change drive letter, Set active partition and Partition Recovery.

Partition Wizard comes absolutely free for Home user and free of charge for business user. Home users, business users, system administrators can easily use this Windows based software to manage their disk partitions. Download it for free from [http://www.PartitionWizard.com](http://www.PartitionWizard.com) and enjoy the new technology and new experience of Partition Wizard.

More information at [http://www.partitionwizard.com](http://www.partitionwizard.com)

---

### Post by kestrel1 on 2009-07-22
> **duyibo said:**
> Hey guys! I’ve found a free 64 bit Windows partition manager by accident. I downloaded it and used it. This software was amazing and easy to use. The most important is that it is free here I would like to share it with you. Following are copied from the website:

Partition Wizard Home Edition is a free partition manager designed by MT Solution Ltd. It supports 32/64 bit Windows Operating System including Windows XP, Vista and Windows 7. Home users can perform complicated partition operations by using this powerful but free partition manager to manage their hard disk partition such as Resizing partitions, Copying partitions, Create partition, Delete partition, Format partition, Convert partition, Explore partition, Hide partition, Change drive letter, Set active partition and Partition Recovery.

Partition Wizard comes absolutely free for Home user and free of charge for business user. Home users, business users, system administrators can easily use this Windows based software to manage their disk partitions. Download it for free from [http://www.PartitionWizard.com](http://www.PartitionWizard.com) and enjoy the new technology and new experience of Partition Wizard.

More information at [http://www.partitionwizard.com](http://www.partitionwizard.com)

Looks very useful for Windows environments. Thamks

---

### Post by sloggerkhan on 2009-07-22
I've had bad experiences with partition magic, but they were a long time ago.

---

