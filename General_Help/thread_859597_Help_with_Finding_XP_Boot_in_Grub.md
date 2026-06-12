---
title: "Help with Finding XP Boot in Grub"
date: 2008-07-14
forum: General Help
---

### Post by Biohazard388 on 2008-07-14
Hello,
I am a new user to Linux based systems, but I am liking it.

When I partitioned my HD to install Ubuntu Hardy, something must have gone wrong...


When I hit ESC when booting my PC, I see the normal Ubuntu boot optinos and the X86memtest option, but strangely my XP boot option seems to be missing.

I did a little searching and tried things out that were previously posted:

I ran the Sudo grub file and added XP to the list of options, but I'm getting an error when I try to boot from it.

My guess is that the Partition number ...something like H(0,0) or whatnot... is not correct.

I've tried going to "places" > "Computer" and seeing if I can access my XP files, but all I have in the list under "computer" is:

FileSystem
CD-ROM Drive
CD-RW Drive
External Hardrive

But my native drive, which XP is loaded onto, isn't showing up. I've gone and ran the Partition command see to my different partitions...and here was the output:

> (parted) print

Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  76.9GB  76.9GB  primary   ext3         boot 
 2      76.9GB  80.0GB  3101MB  extended                    
 5      76.9GB  80.0GB  3101MB  logical   linux-swap        

(parted)      

I think something was messed up in my Partition when I did it when loading Ubuntu for the first time yesterday... but I'm not sure which value I should change to redirect GRUB to accessing my XP boot from...

Thanks in advance for any help. I'm loving Ubuntu so far, but I have several programs I need for work (I work partly at home) and I'm scared that I will have to wipe the hard drive or something...

---

### Post by Biohazard388 on 2008-07-14
Okay, here is small update...and a free bump I guess...

I've tried going into the Command line for Grub at start up and using the:

Grub> root (hd [tab]

funtion to look up existing directories.

It says that HD0 and HD1 are available...However when I do:

grub> root (hd0, [tab]

It shows the linux file system in slot number 1, and an "unknown file system" in slot number 4......but no slot 2 or five...?

I'm so confused. I'm new to Linux...so I do'nt understand what a lot of this means at deep level. I know what it means on the surface though...but I can't seem to fix this problem by myself..which sucks...

---

### Post by Fixman on 2008-07-14
Im sorry to say it, but you deleted your XP partition. The three partitions that are showing are three linux partitions.

---

### Post by Biohazard388 on 2008-07-14
Hmm... But I didn't delete the whole of the XP files and everything under that partition did i?

---

### Post by Fixman on 2008-07-14
> **Biohazard388 said:**
> Hmm... But I didn't delete the whole of the XP files and everything under that partition did i?

You quite did. The only thing you could do is to use some partition recovery tools (just google it).

---

### Post by Biohazard388 on 2008-07-14
Strange. I just used the bundled partition program that came with Ubuntu...very strange.

What would these tools do? Would they just unerase the partition and leave everything else intact, or would it destroy my linux partitions and restore the drive to its Windows only format?



Thanks for the help so far. I'm loving the community support Ubuntu has. :D

---

### Post by Biohazard388 on 2008-07-14
Okay, I have found a nice free partition recovery tool named "TestDisk".

I downloaded the Linux 2.6 compatible version. It has to be run under the root, so I'm trying the run command provided on their site, but it isn't running at all.

Commmand is:
```

sudo testdisk-6.9/linux/testdisk_static
```

The first time I try to run it "in terminal" it comes up with the form asking for my account password, but once I enter it, my computer goes back to idle again...

Is there any other free software that can unerase the partition? Test Disk seems to not want to work for me for some reason...

---

### Post by logos34 on 2008-07-14
you can try to recover the lost xp partition with TestDisk.

---

### Post by logos34 on 2008-07-14
no, use the deb--it's in the repos

sudo apt-get install testdisk

---

### Post by Biohazard388 on 2008-07-14
> **logos34 said:**
> you can try to recover the lost xp partition with TestDisk.

I know, but as I stated before, Test Disk won't open when I try to run it... either by Sudo or by accessing it on my desktop (in its folder)..


I'm new to all of this, so if you could explain how to do things in more detail, I will be able to solve this much faster.

:)

---

### Post by Biohazard388 on 2008-07-14
> **logos34 said:**
> no, use the deb--it's in the repos

sudo apt-get install testdisk


Okay... just ran the apt-get of test disk...now what? I've tried running the sudo to run test disk that was on the CGsecurity website...still nothing happens...

Am I totally looking in the wrong place?

---

### Post by Biohazard388 on 2008-07-14
Finally figured out how to run testdisk:

sudo testdisk

very simple...



So, I ran a quick search, and it yielded the same results as I had earlier with just the non-xp partitions.

I'm running a deeper search and when results are in, I'll post them up.

---

### Post by Biohazard388 on 2008-07-14
Alright, I'm running it again, because I hit a key and lost the info...

What I remember:


It has one or two FAT32 sections...

It also had an NTFS that had " [dellrestore] " behind it.

Once it finishes running for teh second time, I'll copy and past it here. Hopefully it will help.

---

### Post by Biohazard388 on 2008-07-14
Alright, here we go:

[IMG]http://i44.photobucket.com/albums/f26/Biohazard388/Screenshot-2.png[/IMG]


Now, which function do I want to do now? I'm unsure. Would I "load backup"?

---

### Post by logos34 on 2008-07-14
Not quite there...notice how the numbers overlap one line to the next?

0...9348
6...9105
9106...9724
9349...9725

Dig deeper...[URL="http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search"]Follow the documents guide.
[/URL]
Then you need to change the letter at the beginning of each line from 'D' to '*', 'P', etc.  Green will indicate 'OK'.  Then you can write changes to disk

---

### Post by Biohazard388 on 2008-07-15
I read somewhere that I should be doing this from running the Live CD instead of running off of the drive while I am fixing it. It sounds like a good idea...

And which specific partitions should I label as which? Which one is primary, *boot, etc etc..?

Thanks for your help Logos! I hope to get this sorted out. Means a lot to have the community support.

---

### Post by Biohazard388 on 2008-07-15
As requested via PM:

updated screenshot of a new analysis....not sure if it is the same or no, as I haven't checked...but this is the one I just ran:



[IMG]http://i44.photobucket.com/albums/f26/Biohazard388/Screenshot-1.png[/IMG]



Now...which ones are which? Boot*, primary, logical, etc?

---

### Post by Biohazard388 on 2008-07-15
Okay, so I've experimented....

If I have the top "linux" drive in the boot* or P positions....the only one that works for the NTFS slot is D...which gets me no where cause that means it is deleted....

I'm assuming the top Linux slot needs to be the boot one? or does the "linux swap" need to be the boot? Would the boot be the smaller linux? or would it be the one with the really large sector number?


Need to know:


Which is Boot* and which is Primary...

---

### Post by logos34 on 2008-07-15
Ok, I guess that's it.

To restore windows and dell partition, mark the 2nd one and the fat 

[COLOR=Black]*****[/COLOR]'HPFS-NTFS' 6 - 9105...

**P** FAT 32 LBA 9106 - 9724 [DellRestore]

Leave the 'D' on the others to delete.  Since you will lose the ubuntu partition, you will need to restore the windows bootloader to the MBR.  **So quit testdisk right know and download and burn a copy of Super Grub Disk (unless you already have a copy of the XP install cd).  **Then rerun testdisk and make the changes.

---

### Post by Biohazard388 on 2008-07-15
Set the partitions and write to disk...then download the super grub and reboot?


Sorry to question it, I just really want to understand what I'm doing before I make any permanent changes.

---

### Post by logos34 on 2008-07-15
no, reread what I said above.  Quit testdisk now, boot back into ubuntu and dl SGD, burn to disc.  Then rerun Testdisk and make the changes.

---

### Post by Biohazard388 on 2008-07-15
Ah....haha, wow. Yeah, makes sense now. Will do! When you say reboot, I'm assuming you mean run off the drive, and not the live CD like I am now?

When I make the changes, does it matter if I'm running on CD or drive?

---

### Post by logos34 on 2008-07-15
good luck.  gotta go now.

---

### Post by Biohazard388 on 2008-07-15
Okay, well thanks for your help tonight. I really appreciate it. :D


Just incase this all fails and I'm not able to get on for a day or two (until I can get access at the library or something) this is what I'm going to do...


I have Super Grub disc burned and in my CD drive.

I'm going to open Testdisk and make the suggested changes:

```
*'HPFS-NTFS' 6 - 9105...

P FAT 32 LBA 9106 - 9724 [DellRestore]
```


I'm guessing the Super Grub will be a boot disk? or will it repair the boot?


And what do I do after I make the changes? What happens? Do I lose Ubuntu? or what?


I'm confused ...again. :D

---

### Post by Biohazard388 on 2008-07-15
Okay, so I applied the changes and booted with the SGD in the drive....


This is my experience:


The thing doesn't boot itself... first time rebooting, the grub loader had "error 17" and wouldn't load. Turned off the tower, rebooted. F12 for boot setup....chose the CD ROM to boot SGD.

Now, I went through a WHOLE bunch of options with help and such...but nothing has seemed to work to restore anything to anything. Right now I'm using the LIVE disc.

I'll run a quick analysis of the drives and show what it looks like now and post it. What should I be doing now? what do I change to get the Ubuntu grub back since you had me delete the partition that housed it (apparently from what you said)..

---

### Post by Biohazard388 on 2008-07-15
Well......

I ran the software source things, made it universal....downloaded it all...can't seem to open testdisk at all...

Good news though:

under the "places" tab I can see and access my XP files, so I know the restore worked on that...but I'm still out of a grub boot file....

So...stilll waiting on how to do that using SGD.

---

### Post by logos34 on 2008-07-15
> 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#boot_windows)

**1) I just want to boot Windows for now, I'll fix it later,**

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Windows
   4. Boot Windows

This will boot Windows for now for you and you can verify that Windows is still okay and able to be booted. You can access all your data and get any urgent work done. You can fix the problem more permanently later on when you have time or you are in a better mood.
[B]
2) I  want my MBR pointing to Windows  bootloader again  - right now![/B]

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Windows
   4. Fix Boot of Windows

....

>  I ran the software source things, made it universal....downloaded it all...can't seem to open testdisk at all...

and you ran **sudo testdisk** in a terminal like you did before from the hard disk?

>  And what do I do after I make the changes? What happens? Do I lose Ubuntu? or what?

ubuntu est finis.  I said that already.  It should be obvious, since you've just rescued/restored the XP that ubuntu overwrote.

---

### Post by Biohazard388 on 2008-07-15
> **logos34 said:**
> ....



and you ran **sudo testdisk** in a terminal like you did before from the hard disk?

Yes, it wouldn't load. The terminal would flash on screen and then disappear...


I just did all the steps again, and then sudo apt-get install testdisk and it is running now. I must have missed that step last night.

I'm running a new analysis to see if it gives any insight...


> **logos34 said:**
> 

ubuntu est finis.  I said that already.  It should be obvious, since you've just rescued/restored the XP that ubuntu overwrote.

yes, and thank you for being so patient with me.

I tried the plain old boot of XP and it didn't work. Just the flashing underscore on the top left of the screen...

I then tried the "Fix boot" option and when it came to the screen that said "pick the operating system you had installed before"...the only option was syslinux? There is nothing that says Windows anything.

I'm also noticing that I have only recovered probably 98% of the files that were on my XP machine before. I'm missing some of my photos and such I had on there before, but I believe I have them still on my camera, so no big worries. I guess some fileloss is to be expected.

Since the fix boot and boot windows does work... what should I attempt to do next? Is there a diagnostic I could run?

When I am looking at the options of which partition to look in to boot from and which to repair, there are only two options: one has 74GB and the other is 0KB....I'm assuming I should be attempting to fix the boot on the larger one, correct? Is that were the boot files reside?

And really, I can't thank you enough for all the help you have given me so far. I've recovered most of my files, so if I can't get windows to boot anymore, it isn't a real heartbreak. I have an external HD that I have moved all my personal files too. If I can get Windows to boot again, it will just be icing on the cake to allow me not to rely on the live disc for the next two weeks.

---

### Post by WRDN on 2008-07-15
If you have the XP Install disk, or can access the Dell Recovery partition (assuming that was left or recovered) then you may need to reinstall Windows. As you stated, when you recovered the XP partition, some files may have been lost. There are loads of guides for reinstalling XP, its a pretty simple process though, and it overwrites the MBR with its own version, so the next time you restarted the PC, it would boot directly into Windows.

---

### Post by Biohazard388 on 2008-07-15
Thanks WRDN. I'm searching for it right now. I know I bought the backup disc from Dell when I bought the computer. I have to resort to that, I'll wait until I get my new PC. The plan right now is to wipe the hard drive and take it and give it to my parents so they have access to email the like. Last computer they had was either 98 or ME and haven't used one in a while. Figured it is a good way to recycle the system.

I'd hate spend the hours installing and updating the service packs just to have to wipe the drive and do it all over again a few weeks later. Might as well just do it one swoop...

Is there possibily any way to see if an XP reinstallation is my only choice at the point? Any software I can run that will give a clear answer?



and:

I just want to thank everyone that has helped me so far. I would have gotten NO WHERE without you guys and I'm eternally grateful. Even though I had a "bad" experience using ubuntu the first go around, when I install it on my new laptop in a few weeks time, I'll be sure to not use the "full disc" write that I so naively used this time around. :D 

I'll be sure to give a bunch of thanks to you guys...once I figured out how to use that function. :D

---

### Post by logos34 on 2008-07-15
I you only had the XP install cd (not the recovery cd), you could boot into the Recovery Console (>'R') and run **chkdisk /r**, **fixboot **and **fixmbr**.  

>  I tried the plain old boot of XP and it didn't work. Just the flashing underscore on the top left of the screen..Try to enter safe mode:
> [CENTER]**How to boot into Safe Mode in Windows XP**[/CENTER]
                  
                 Restart the computer. Immediately after the screen goes blank for the first time, or after the BIOS post ends, start taping the F8 key repeatedly. The Windows Advanced Options menu appears. If the menu does not appear, restart the computer and try again. If the Keyboard has a [F-Lock key]("http://bertk.mvps.org/html/safemode.html"), it may be necessary to press it first - **QUICKLY** before pressing the F8 Key. This will have to be done quickly before tapping the F8 key repeatedly.
                 The **Windows Advanced Options Menu** shown next should appear
If you can, Start>Run>CMD>type [B]chkdsk /r

[/B]when done, note the results.  Then type:[B]

fixboot 
[/B]
this will rewrite boot sector code to system partition (you may only be able to do this frm cd, not sure)

Try the SGD again...see if it allows you to see and boot into windows and/or restore windows bootloader to MBR (what's this with 'syslinux'? hmm.)

Or if you have a floppy you can use fdisk to restore the windows bootloader to the mbr:

1. dl the 'windows 98 se oem' floppy [here]("http://www.bootdisk.com/bootdisk.htm")
2. [make the floppy and use command 'fdisk /mbr']("http://users.bigpond.net.au/hermanzone/p18.htm#Windows_98_Floppy_Disk_Method")

To get the rest of those pictures/files, try **PhotoRec** (see TestDisk mainpage)

> looking at the options of which partition to look in to boot from and which to repair, there are only two options: one has 74GB and the other is **0KB**gee, doesn't look like dell partition survived (maybe it's wrong though)

---

