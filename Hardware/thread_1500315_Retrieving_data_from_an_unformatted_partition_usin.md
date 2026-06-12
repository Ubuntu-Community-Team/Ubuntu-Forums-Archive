---
title: "Retrieving data from an unformatted partition using a LiveCD/boot USB drive?"
date: 2010-06-03
forum: Hardware
---

### Post by cwshea on 2010-06-03
This is quite a long story, but I'd _really_ appreciate any help you folks can give me. I'm new(ish) to Ubuntu, and I NEED your help.

I'm on the verge of losing a huge chunk of personal data from the last few years (pictures, videos, music, etc). Luckily some of my data (school files and personal writings etc) was backed up on DropBox. I only had the free (2GB) service, so not everything was in DropBox.


I have a Dell Inspiron E1505, which up until a few weeks ago was running Windows XP (I think SP2, maybe SP3) pretty well. It's getting on in years so it was getting bit sluggish, but that's not the point.

2-3 weeks ago, my Dell started acting funny. I think it's after I ran Windows update, (and I think that's when I upgraded to Service Pack 3). It would run for about an hour, then completely shut off. This happened twice, I believe, and then it blue screened when I tried to turn it on. I eventually got it working by just trying a few more times, and unfortunately (**believe me** I'm kicking myself for this) I didn't back up my files at that point. A few days later, I tried to turn it on again, it blue screened, and I got a different error.
This error was along the lines of "systemroot\system32\config\software corrupt". Since then, I haven't been able to boot it into Windows.

I got caught up in school and other things for the last few weeks, so it wasn't until the day before yesterday that I was able to sit down and try to solve this. Because my laptop is still under warranty, Dell is sending me a new hard drive. HOWEVER, they will not help with data recovery.

I went out and purchased a SATA hard drive enclosure to see if I could just plug the Dell hard drive into my Acer Aspire One netbook, and recover my files in that manner. This worked, sort of. However, there is a major complication.

My Dell hard drive is partitioned into a C: drive and a D: drive. The C: drive is around 80gigs, and the D: drive is around 20gigs (these are estimates; I'm not actually sure off the top of my head).

I'm able to view files on the C: drive fairly easily, although for some of them, copying them is an issue. I get an error in the form of a "cyclic redundancy check" for roughly 1/100 of my music files. I'm not sure if it's related to mp3 vs m4a, or what. That's an annoying issue, but it's not too traumatic, as I have CDs etc from which I can recover most of my music.

**MORE IMPORTANTLY**, I am unable to view ANY of the files on the D: partition. This is (I believe) because there is no file system installed on this partition. From what I've read, if I were able to boot from Windows on the C: partition, I'd be able to view the files on the D: partition because it uses the file system (FAT? NTFS? I'm lost when I get at all deep into the inner workings of OS's) from the C: partition, where Windows is installed.



Now then, on to why I'm posting on the Ubuntu forum.

While searching around trying to find solutions to this problem, I came across [this]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/") guide to backing up files from a Windows computer using an Ubuntu LiveCD. Having used Ubuntu a little bit in the past (I put it on an old laptop and used it as a spare for a year or so before it finally kicked the bucket), I decided to give it a try.
I ended up turning my 8GB USB drive into a boot drive, and after changing the boot order on the Dell, I was able to fire up Ubuntu.

My first impression was that it is a LOT (!!) quicker than Windows ever was on that laptop. Although I have to keep Windows on my Dell once I get my new hard drive in the mail (mainly to run iTunes to be able to update my phone), I will _definitely_ be switching my netbook to Ubuntu!

But back to the data issue.
I ran into the same problem I did while trying to read the Dell HDD as an external; I can't access the second partition. Despite following the instructions in that article for that very problem, I still haven't been able to.


I wrote this entire post on my netbook, but I've kept Ubuntu running on my Dell.
Just before posting, I connected my Dell to my wifi network, so I'll be able to upload screenshots of the error message I run into when trying to read from the 2nd partition in a few minutes.



I can't describe how much I would appreciate ANY help in rescuing my files. All of my pictures from the last few years (I'm an amateur photographer) are on that partition, and I haven't backed them up to my external (Western Digital) drive in a few months.


Please, please, help me out!

Thank you!

---

### Post by cwshea on 2010-06-03
Here are a few screenshots from trying to follow [these]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/") instructions.

If there's any other info I can provide, please just let me know.

---

### Post by mindpowerz on 2010-06-03
You can try PhotoRec to recover your data, it's free & powerful, not only for pictures, but for all other supported file formats.

Just google for it. It's usually included as a subfolder in TestDisk.

---

### Post by aysiu on 2010-06-03
Photorec using the Ubuntu live CD.

Tutorial with screenshots here:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

Let us know if you have any questions or run into problems.

You will need a backup external hard drive for the recovered files.

---

### Post by efflandt on 2010-06-03
What does **sudo fdisk -l** (small L) from Linux show for the drive?  That may show them even if they cannot be mounted.

If you connect the USB enclosure to a PC with Windows and go to administration tools, are you able to see 2 partitions from there?  If so, go to a command window and do **chkdsk /f** on each of them to see if Windows can fix anything wrong with them.

Otherwise I have often seen **testdisk** mentioned, which you could install on your 8GB USB from System > Administration > Synaptic.

Either my boss' grandson is rough with the old laptop, runs the battery down, or the old laptop itself is getting flaky.  At some point WinXP Pro itself refused to boot at all, even in safe mode, BOD'd to protect data.  From an Ubuntu CD I could not copy much from the user's home dir before it would hang.  In an external enclosure neither Windows nor Linux could mount it (but Linux fdisk still showed partitions).  Weeks later, I tried it again, and Ubuntu auto mounted the partition and I was able to copy most of the user's files from it.

I replaced it with WD blue Scorpio 160 GB, and sometime later Windows again refused to boot.  I fixed it with chkdsk /f from another computer, which found bad sectors, but then booted fine.  WD utility still showed issues, and because of the bad sectors, Clonezilla would not work, but I imaged the partition with WD version of Acronis (not by sector), and used the image for the warranty replacement drive.

That worked fine until Windows again refused to boot.  But this time chkdsk /f just found minor corruption (no bad sectors), but I am checking it more throughly.

But I also know someone whose failing drive I replaced, then got hopelessly infected with several viruses probably planted by a bogus search engine.  The laptop still booted, but scareware called Security Tool blocked task manager and safe boot and eventually replaced the background image with its fake virus warning.  So I had to use an Ubuntu CD to copy user files to a USB drive where I could virus scan them (found lurking in user's temp dir), then totally reinstalled Windows and added Ubuntu.

So it is hard to tell if Windows got confused, you are infected, or your hard drive is failing.

---

### Post by cwshea on 2010-06-03
I'll give this a shot right now, but in the meantime: will it still work even though I can't access the partition?

---

### Post by mickwombat on 2010-06-03
An excellent utility to use is testdisk.  You'll need another external drive to copy everything onto.

I have a drive whos partition table was corrupted and this utility was able to rewrite the table and....bingo....the drive was back to normal.

In anycase you'll be able to get all your files onto the other drive.

It is a command line utility, but fairly straightforward to use.

From a terminal,

#sudo apt-get install testdisk

then 

#sudo testdisk

From memory though I'm not sure if it will install when using the LiveCD.  You may have to enable a repository or something.

Good luck,

---

### Post by cwshea on 2010-06-03
Thanks everyone!

mindpowerz and aysiu: I'm running PhotoRec right now (still off the LiveCD/USB drive). It's had a couple of unreadable/error files so far, but it's still running. Oh, and it estimates around 300 hours to finish.. Uh oh. Hopefully it'll be able to recover everything though! I selected to recover all files from both partitions.

mickwombat: If PhotoRec doesn't work out, I'll give that a shot. Thank you!
A downside to PhotoRec, as far as I can tell, is that all filenames etc are lost; is this the case with testdisk? I may end up using it in addition to PhotoRec.


efflandt:

_What does sudo fdisk -l (small L) from Linux show for the drive? That may show them even if they cannot be mounted._
I'm not sure, but I'll let you know once PhotoRec is done.

_If you connect the USB enclosure to a PC with Windows and go to administration tools, are you able to see 2 partitions from there? If so, go to a command window and do chkdsk /f on each of them to see if Windows can fix anything wrong with them._
When I connected the Dell hard drive via an external hard drive enclosure, I was able to see both partitions, but I could only access the C: drive, which is where Windows is installed. The D: partition was inaccessible; it asked me if I wanted to format the drive (which I obviously don't want to do!).

_Otherwise I have often seen testdisk mentioned, which you could install on your 8GB USB from System > Administration > Synaptic._
I'll do this after PhotoRec is done. Thanks!

I'll also be sure to try the chkdsk /f option.
I have enough space on my external to copy everything from my Dell hard drive at least 5 times, so that's not an issue.

Thank you for the detailed response and ideas!




And again, thank you everyone from the help and replies!!

---

### Post by cwshea on 2010-06-03
Sorry to double post, but this is pretty critical. PhotoRec didn't work; it found a total of 2468 files, then came up with

Segmentation fault (core dumped)
ubuntu@ubuntu:~$


I guess PhotoRec isn't going to work out. I'll try one of the other options in the morning.
:(




**EDIT:** I tried to run testdisk to see if I could repair anything, but... I have no idea what I'm doing in Ubuntu, and couldn't figure out where I'm supposed to run it from.
I'm sorry for being so helpless, but I'd appreciate any help on that. Thanks.



**EDIT2:** Great news!!! I started running PhotoRec on the unformatted D: partition (copying the data to my external 1TB WD drive), and it seems to be working!! So far it's found 3152 files, of which 2684 (!) are .jpg files!
I'm aware that it'll be a bit of a pain to rename/re-categorize all the photos, but this is SO much better than losing all of my photos. I'll probably try another method to see if I can access all the data without having to categorize it, but for the moment this is a HUGE relief.
Thank you all so much!
Btw: I guess whatever happened in Windows only corrupted data on the C: partition, so while I'm probably going to lose some of my music, I should be able to recover everything on the D: partition. Music is replaceable (I was able to copy over all of my voice memos and other things that I recorded), but photos aren't, so this is good news :)

**EDIT 3:** Notes for data renaming/reorganizing programs: easytag & jhead

---

