---
title: "Grub Error 18 - Was working - frustrated!"
date: 2008-10-29
forum: General Help
---

### Post by paustin on 2008-10-29
Morning all,

I apologize in advance if I sound frustrated.  2 different machines just failed on me, and I am ready to rip my hair out.  Any help would be greatly appreciated.  I will try to be as detailed as I can.


Background:
IT for 25 years.  Linux newbie (but learning really fast)

I have an older ex-Windows PC set up as a headless backup system / media server.  Nothing really exciting - I just back data onto it, and store movies and music to be used throughout the house.  Hardy Heron.  Once I got it all set up, I removed keyboard and monitor, and stuck it in a corner.  It has been working fine for a month.  I have only Hardy installed - this is not dual-boot.


Issue:
Now, when I boot, I am getting the "Grub Loading Stage1.5" "Grub Loading, please wait..." then "Error 18"  (note that there is no space after the word 'Stage', doubt that is useful, but wanted to mention)

It started yesterday I tried to VNC to it and the desktop only seemed to partially load.  I was able to see the desktop, but could not click on anything.  I recycled the power as I was unable to click on anything to force a soft shutdown.

On reboot, I got a NTLDR error.  (Remember that this used to be a windows machine.)  I went into BIOS and discovered that it was trying to boot from the non-Ubuntu drive.  I changed the boot-order in BIOS and rebooted.  Here I got the "Error 18".

To isolate the error, I have gone into BIOS and disabled *all* drives except the Ubuntu boot drive.  I have also tried resetting the BIOS to the default, with no change.  I've turned down/off all options (not that there were many).  Disabled the floppy (didn't have one in there anyway), slowed the CPU down, disabled the QuickBoot option, etc.

Configuration:
Drive 1 - 1TB sata drive connected via internal SATA card.  This is my Ubuntu boot drive.  It has a single partition with Hardy loaded.  (Yeah, I know - I tried to create a smaller boot partition on install, but I kept getting some error and just let it take the whole thing)

Drive 2 & 3 - 250gig drives - One of these was the original Windows boot drive.  Now used only for storage.  Again, these *are* disabled in BIOS.  

Drive 4 - DVD/RW drive - Nothing loaded in the drive.  Disabled in BIOS.

I have read that the Error 18 can indicate a problem with the drive being to large for BIOS.  I don't think that this is relevant here.  The drive is SATA managed by an external card - also, it has been working fine for a month.

In my searches, there are also some references to obtaining a command prompt - I am unable to get one.  Tried hitting Escape a number of times when I started to see the Grub reference during boot, but either that tip is a bad one, or my timing is off.  It hits *really* fast so I don't think it is my timing.

I've also read that formatting the drive is another solution.  This is a large drive with a lot of data.  I would *really* like to avoid this.  (I mean *really* like to avoid it)

ANY help would be greatly appreciated.  I am enormously frustrated.  I need to be able to get the system operational without loosing all of my data.

Also, please remember the note above about being a Linux newbie.  I'm very technical and can build desktops and laptops, but I don't know the linux lingo.  Small words for the mentally challenged would be really appreciated.

Thanks in advance,
Pete
[email]paustin@worldedi.com[/email]

---

### Post by caljohnsmith on 2008-10-29
I can understand your frustration, Pete, because Grub problems can be really difficult sometimes. If you can boot up your Live CD, how about opening a terminal (applications > accessories > terminal) and do:
```
sudo fdisk -lu
```
Post the output of that, and then:
```
sudo grub
grub> find /boot/grub/stage2

```
The above command should output (hdX,Y) where X and Y are numbers, use that:
```
grub> root (hdX,Y)
grub> blocklist /boot/grub/stage2
grub> blocklist /boot/grub/menu.lst
grub> setup (hdX)
```
Please post the output of all the above commands, reboot, and let me know if anything changed; we can work from there. :)

---

### Post by paustin on 2008-10-29
- Will do.  Working on it now.

---

### Post by paustin on 2008-10-29
I am assuming that you mean for meet to run with the topmost option of the boot options.  Something like "Try Ubuntu without any changes to your system"

I'm getting a bunch of errors. { DRDY ERR } and buffer i/o errors on SDA1 (noting numerous logical blocks.  I assumed my CD is bad and re-burned from another image.  I had the burning software do a compare of the CD against the image and it verified ok.  

I rebooted and had Ubunto "Check CD Image" and it gave me similar errors (they go by pretty quickly).  It slowed down while checking integrity of some file systems, so I caught some of these errors. 

Buffer I/O error on device sda1, logical block 5
183,929656] ata1.00: status: {drdy err ]
186.859847] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
183.929598] ata1.00: cmd c8/00:01:44:00:00/00:00:00:00:00/eo tag0 (I lost the rest)

It got all the way to the end and says, 
Check finished: no errors found
Press any key to reboot your system

Is SDA1 the CD drive?  Or is my data hosed.  Currently I only have the CD drive and the SATA drive (where I initially installed) loaded.

===============

Update:  I left the CD in and left the room for a bit.  (even geeks need lunch).  Came back to a Ubuntu desktop, though I didnt' watch the boot.  

Followed your command:
***sudo grub***
got back a **grub>**
entered    ***find /boot/grub/stage2***
got back   **Error 15: File not found**

Tried ***find /boot***
got back   **Error 15: File not found**

---

### Post by caljohnsmith on 2008-10-29
How did you originally install Hardy to that HDD? Do you have any Linux Live CD's that will boot OK? "sda" should be your SATA drive, and "sda1" would be the first partition, probably your Ubuntu install. I'm not sure why you would be getting an error about sda1 if you are trying to boot the Live CD though. And yes, you used the correct option, the "Try Ubuntu without making any changes to your system" or whatever it exactly is. 

I'm not sure what to say, because you'll need some sort of Live CD or maybe Live CD on a USB drive to do the troubleshooting. I know there are lots of tricks to getting a Live CD to boot correctly, like adding certain kernel options at boot time, but I don't remember any of them since I've never had to use them. You could download and try another Live CD, maybe PCLinuxOS, Mandriva, etc and see if they will boot. The bottom line is you'll need the command line from a Live CD to do most of the troubleshooting.

---

### Post by paustin on 2008-10-29
See my update above - it did finally load...after all the errors.  

Take a look at my "screenshots"  <grin>.  

They should be readable.  If not, let me know and I can post them much better. I'll be upping a 2nd post with 4 more pics

1, 2 - Just showing that I only have the DVD and the original boot drive loading
3 - The initial booting of the CD
4 - Showing my menu selection of "Try Ubuntu"
5-7 - The errors
8 - Some OKs after the errors, then more errors
9 - Result of the attempt to follow your commands.

Pete

---

### Post by paustin on 2008-10-29
Remaining shots

---

### Post by caljohnsmith on 2008-10-29
OK, you originally mentioned that Ubuntu was working fine for a month, and now when you boot it you get the Grub error 18. So what of significance happened before you started getting the Grub error? Did you get some updates or install new software? Make any hardware changes? Change BIOS? Any clues you can provide would greatly help.

Also, please post:
```
sudo fdisk -lu
```
And if you can, try and make your screen shot a little larger.

---

### Post by paustin on 2008-10-29
Changes:  This system has been sitting in a corner for the last 5 days.  I finally moved it from the middle of the office where it'd been sitting awhile.  It has been running find.  Yesterday I tried to VNC in to it.  I connected but the desktop was a little odd.  Oddly sized, and mouse-clicking didnt' have any effect anywhere.  After d/c'ing and reconnecting a couple of times, I gave up and hit the power switch.  That was about it.  I did have a 500 gig SATA drive in the machine that was going bad.  It was mounted, but I had nothing loaded to it as I didnt' trust it.  When this problem started, I did d/c it to remove it from the equation (as I did with the 2 250gig IDE drives.  Nothign else I can think of.  

I just use it as a file server, with *very* little software loaded to it.  I think the only non-base software I have on it is VNC, and a couple other VNC-like tools (that I used till I could get VNC working).  

sudo fdisk -lu - Attached is a larger shot.  Let me know what else.

Screenshots:  Do you need the OTHERS made larger?  If so, I have posted the most meaningful ones here.  
[http://picasaweb.google.com/pete.austin1/Tempjunk#](http://picasaweb.google.com/pete.austin1/Tempjunk#)   

Pete

---

### Post by caljohnsmith on 2008-10-29
OK, next try:
```
sudo fsck -y /dev/sda1
```
If that returns any errors, please post a screen shot of it. Next post:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt /mnt/boot/grub
```
And finally please post:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

---

### Post by paustin on 2008-10-29
I like this. A man with a plan.   Question. You say:
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

Remembering that my drive is a  sd, not a hd, are your instruction still ok?  Holding on your response.

---

### Post by caljohnsmith on 2008-10-29
Yes, all drives, whether IDE or SATA, will be (hd) in Grub's Convoluted World. :)

---

### Post by paustin on 2008-10-29
The mount command tells me that you must specify the filesystem type.  What should I use here?

Convoluted?  So I am beginning to learn.

---

### Post by caljohnsmith on 2008-10-29
What did the fsck return? If it said all was OK, then you shouldn't have to specify the file system type with the mount command. Try:
```
sudo blkid
```
That will show the file system type for sda1, most likely ext3, and then you could try and mount it with:
```
sudo mount -t ext3 /dev/sda1 /mnt
```
Or replace ext3 with whatever is your sda1 file system.

---

### Post by paustin on 2008-10-29
fsck -y /dev/sda1   gives me
fsck.ext2:  Attempt to read block from filesystem resulted in short ready while trying to open /dev/sda1

Please note that I *can* open the data folder on that root drive

root (hd0,0)   gives me
Error 25: Disk read error

setup (hd0)    gives me
Error 12: Invalid device requested

sudo blkid      gives me
  << see picture >>



This is beginning to scare me, should I start to worry?
Pete

---

### Post by caljohnsmith on 2008-10-29
> **paustin said:**
> 
Please note that I *can* open the data folder on that root drive

What do you mean--can you mount and see the contents of sda1 somehow? You only have two partitions on sda, one your root file system and the other your swap. If you can somehow access your files on sda1, then I would strongly suggest backing up anything important before we go any further; at least to me, it looks likely that you have a hardware problem at this point. Note that the blkid command didn't even detect your sda1 partition. 

You did mention that it's an older PC; how old is the HDD? I would crack open the computer's case and re-seat the HDD connections just to make sure that isn't the issue. I think it would also be judicious to run some HDD diagnostic tests on it to check if it's failing. You probably have your own arsenal of HDD tools, but in case you don't, you can always download and use the [Ultimate Boot CD]("http://www.ultimatebootcd.com").

EDIT: Since you had so many problems with even booting the Live CD, it might be a problem with your motherboard or RAM. I would run the "memtest86+" option from the Live CD (I think it has that option) to test your RAM.

---

### Post by paustin on 2008-10-29
yes, I can see the contents of the drive.  If you look one of the pics that I sent (the last in the series of 9) you can see the beginning of the folders (Archvie, AutoHotkey, etc).

Using your suggestion of blkid, I assumed that the drive in question was NTFS and attempted to do the mount as
sudo mount -t ntfs /dev/sda1 /mnt 

See the picture for the results.    The picture **also** shows the data on the drive - as you can see, I can access it, and I can open it...

Is it possible that we not attempting to fix the correct drive?   How could I be having all these problems and still see the drive.  As for mounting it, if I can *see* the files, it is already mounted right?

---

### Post by caljohnsmith on 2008-10-29
OK, while you still have the "DATA_" folder open/mounted, do:
```
mount | grep -i data
```
And what partition does it show is mounted on "/media/DATA_"?

---

### Post by alienprdkt on 2008-10-29
> **paustin said:**
> 

Using your suggestion of blkid, I assumed that the drive in question was NTFS and attempted to do the mount as
sudo mount -t ntfs /dev/sda1 /mnt 



If the drive in question is your Ubuntu drive it is ext3 not ntfs


sudo mount -t ext3 /dev/sda1 /mnt

---

### Post by paustin on 2008-10-29
/dev/sdb1 on /media/DATA_ fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

so maybe we need to get sdb1 corrected?

Ok, then, here is another question.  Is it possible that I am flat-out-wrong about what I am seeing.  I think that I am.  

Looking at the picture that I sent, the sudo fdisk -lu says the following, and seems to point to the 1TB drive
sda1 - Linux
sda2 - Extended
sda5 - Linux Swap/Solaris

sdb1 - NTFS and appears to be a 250 gig drive
sdc1 - same as sdb1

**_how can it see the 250 gig drives? _**  I have them turned of in BIOS. (as you can see from one of those pictures)  I don't have them [U]disconnected[U], but they are turned off.  It looks like Ubuntu is seeing them anyway.

I have the data backed up on the 250's **_and_** the 1TB.  I think I am seeing the data from one of the 250's, not the 1TB.

I'm still looking.

---

### Post by caljohnsmith on 2008-10-29
> **paustin said:**
> /dev/sdb1 on /media/DATA_ fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

so maybe we need to get sdb1 corrected?
I don't think I'm following you; at this point, we're trying to access your Ubuntu install on sda1, not sdb1, and sdb1 is your NTFS partition on the sdb drive. Based on everything you've said so far, it all seems to point to a hardware problem I think. Most likely it could be your motherboard, RAM, or HDD. You could swap the sda drive into another computer, boot a Live CD, and see if you can access it. If you can access sda1 that way, you would know that your Ubuntu HDD is probably not the problem. 

I don't think I can help you any further because your problem seems to be a hardware problem and not a Grub-related problem. Good luck and let me know how it goes.

---

### Post by paustin on 2008-10-29
Ok, I have consolidated all of the information that we've discussed so far into a single Word document, which I have attached.  

I apologize for my confusion.  I think that it was caused by my erroneous believe that if my 250 gig drives were set to OFF in Bios, then they could not be seen by Ubuntu.  Thinking this, I misunderstood some of what I was seeing, attributing it to my 1TB.

Take a look at my Word document and tell me what you think.  Here is what it looks like to me:
 - I'm screwed.  but I am hoping you can bullwinkle a rabbit out of your hat.

sda1 reports a whole catalog of errors on boot, as seen by my 'screenshots'.

sudo fdisk -lu gives me the following (editing out my 250gig drives)
[B]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x79d4a826

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1947463559   973731748+  83  Linux
/dev/sda2      1947463560  1953520064     3028252+   5  Extended
/dev/sda5      1947463623  1953520064     3028221   82  Linux swap / Solaris[/B]


grub> find /boot/grub/stage2   tells me **Error 15: File not found**

grub> blocklist /boot/grub/stage2  tells me **Error 12: invalid device requested**

grub> blocklist /boot/grub/menu.lst  tells me the same.

sudo fsck -y /dev/sda1  tells me
[B]ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
[/B]
**_*And that looks like the killer to me*_**


grub> root (hd0,0) gives me  **Error 23: Disk read error**

grub> setup (hd0) give me   **Error 12: Invalid device requested**

and the finale is:
sudo blkid   
which doesnt even see sda1 and says:[B]
/dev/sda5: TYPE="swap" UUID="59e73ad3-8964-4dc5-915a-ccb744299b69" 
/dev/sdb1: UUID="6A60C89F60C8737D" LABEL="DATA" TYPE="ntfs" 
/dev/sdc1: UUID="38D47142D4710382" LABEL="DATA" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sdd1: UUID="E72D-BFB4" TYPE="vfat"[/B]

---

### Post by caljohnsmith on 2008-10-29
Like I mentioned in my previous post, I would start with swapping out the sda drive and try it in another computer (you could even use a USB enclosure), and see if you can access it from a Live CD. If you can't access it, then definitely the Ubuntu HDD is at least part of your problems. But if you can access it, then maybe your RAM, motherboard, or something like that is the problem. My guess is that the Ubuntu HDD is at least part of the problem, because you were able to access your NTFS sdb drive OK. Good luck.

---

### Post by paustin on 2008-10-29
Yep.  Will do that now and let you know.  If it *is* some sort of a fried partition, is it possible to recover it without losing data?

---

### Post by caljohnsmith on 2008-10-29
You can use "[photorec]("http://www.cgsecurity.org/wiki/PhotoRec")" to try and recover files off of the partition, but that could be extremely time consuming and messy since sda1 is basically a 1 TB partition. You'll also need another 1 TB drive to save all the recovered files to. If you have the time and patience though, then photorec could work.

---

### Post by paustin on 2008-10-29
Thank you for all your help.  I have been looking at PhotoRec, though I surely don't have another 1tb drive to drop in.  

What about Testdisk?  It claims that it can recover ext2 and ext3 partitions.  Do you think that I stand a chance?

I have it, and am running it, but don't see a partition type that makes sense to me.  Would it be the Sun Solaris?

[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection

---

### Post by caljohnsmith on 2008-10-29
Unfortunately, testdisk probably won't help in your situation, because testdisk is mainly for fixing partition table problems such as overlapping partitions. Your partition table is extremely simple, only two partitions. You can go ahead and use testdisk and see if it reports any errors; if it doesn't give any errors, and if the start/stop endpoints for your partitions agree with the fdisk output you gave earlier, then it's highly unlikely there's any problem with your partition table. But as long as you have it running, in the first screen choose "no log", select the sda HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. If it doesn't report any errors, and the start/stop/size numbers of the partitions agree with fdisk, then your partition table should be fine.

---

