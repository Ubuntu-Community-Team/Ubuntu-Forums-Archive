---
title: "Problems with instalation"
date: 2009-03-01
forum: Installation &amp; Upgrades
---

### Post by Rlad78 on 2009-03-01
(Forgot to mention, this is a homemade computer. Specs at the bottom)

So I'm installing Ubuntu 8.10 32-BIT + Live version from a disk my friend got from a magazine. I check the disk with the program that came with it, but when I get to the real installation, at the point where it's setting up the partitioner, it gets to 50% where it says it's reading the disks and freezes. 

I've done the trial run, defragmented my hard drive, and have 42 GB of free space.

The only things I haven't done is the disk checker program found on the disk (takes WAAAAAYYYY too long) and downloaded Ubuntu off the internet (don't feel like wasting a CD if my CD is fine).

Does anyone have any tips?
My friend has Ubuntu on his laptop and I really want it.

BTW, here are the specs on my computer (According to Belarc Advisor):
OS: Windows XP Home Edition Service Pack 3 (build 2600)
Motherboard: ASUS P5K SE/EPU
Processor: 1.60 gigahertz Intel Celeron
Hard Drive: WDC WD1600AAJS-65WAA0 160.04 GB (???)
CD-ROM: ASUS DVD-E818A

---

### Post by whoop on 2009-03-01
Maybe you should make the 42 gb of free space 42 (or less) gb of unpartitioned space. Although you defragmented you drive I think it is still fragmented.
I had the same problem on a machine. I had to defrag in safe mode and create unpartitioned disk space using the livecd to make it work.

---

### Post by Rlad78 on 2009-03-01
Fix the problem. Did it in text mode.

Now I have a bigger problem.

I have windows XP installed on my computer and I want to have both OS on my computer. Since this is in text mode, I'm kinda confused on what I should pick and I REALLY don't want to lose everything I have on XP. 

Here are the options Ubuntu is giving me:
Guided - resize SCSI1 (0, 0, 0), partition #1 (sda) and freed s
Guided - use entire disk
Guided - use the largest continuous free space
Guided - use entire disk and set up LVM
Guided - use entire disk and set up encrypted LVM
Manual

Please help! I REALLY do not want to screw up my computer!

---

### Post by whoop on 2009-03-01
Wait for someone else to confirm, but I am sure it is:
Guided - use the largest continuous free space

I have done this in the past when my goal was to create multiboot

---

### Post by mudguts on 2009-03-01
not sure what my two cents are worth but I just did a similar install 30 minutes ago.

I had the similar issue where I kept XP and installed Ubuntu in the free space.

I chose:

Guided - use the largest continuous free space

and so far... so good.

---

### Post by Rlad78 on 2009-03-01
PROBLEM!

> Failed to partition the selected disk

This probably happened because the selected disk or free space is too small to be automatically partitioned.

<Go Back>     <Continue>


I have 42GB of free space. Is that not enough?

---

### Post by Rlad78 on 2009-03-01
Bump (hope bumping is allowed on this forum... :???: )

---

### Post by Rlad78 on 2009-03-01
Anyone!?

---

### Post by halw on 2009-03-01
42Gb should be enough space.

I have XP and linux dual booting on a 40Gb laptop with no problem.

---

### Post by Rlad78 on 2009-03-02
> **halw said:**
> 42Gb should be enough space.

I have XP and linux dual booting on a 40Gb laptop with no problem.

Then why is this error occurring?

Should I just choose:
Guided - resize SCSI1 (0, 0, 0), partition #1 (sda) and freed s
or
Manual?

---

### Post by Rlad78 on 2009-03-02
Hello!? 
Anyone out there!?

---

### Post by boof1988 on 2009-03-02
> **Rlad78 said:**
> Hello!? 
Anyone out there!?

Nope.

---

### Post by Rlad78 on 2009-03-02
> **boof1988 said:**
> Nope.

:(

Thanks for the help...

---

### Post by whoop on 2009-03-02
Maybe it is still just free (partitioned) space on your windows partition and the partitioner is having problems because the windows files are fragmented all over the partition.

So some (possible) solutions could be:
Defragment your windows drive in safe mode (I remember once I had to do that twice).
With a livecd like ubuntu or gparted create unpartitioned space for the ubuntu installer to install to.

I have seen posts in various threads of people who advise against resizing windows partitions using ubuntu livecd (don't really know why) I did it several times and did not have any problems; I mean it's not like the drive is mounted or anything.

---

### Post by Rlad78 on 2009-03-02
> **whoop said:**
> 
So some (possible) solutions could be:
Defragment your windows drive in safe mode (I remember once I 

Would it be safe right now to shut down my computer?

> **whoop said:**
> 
With a livecd like ubuntu or gparted create unpartitioned space for the ubuntu installer to install to.


Kinda confused on how to do that...

Here is a picture of my screen right now:
[IMG]http://i217.photobucket.com/albums/cc292/ChipzMaster/Picture.jpg[/IMG]

---

### Post by whoop on 2009-03-02
Well looking at your screenshot your windows partition is currently taking up the entire drive (just about). So you have a good chance that my previous post is accurate:
> 
Maybe it is still just free (partitioned) space on your windows partition and the partitioner is having problems because the windows files are fragmented all over the partition.


I guess nothing can stop you from turning off/restarting your machine.

So I would try to defragment windows in safe mode. and resize windows partition. Looking at the screenshot it looks like you are installing using the server cd or the alternate desktop cd. You can't use these to resize your current partition. Safest bet will be to download partedmagic and resize the partition with that: [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by Rlad78 on 2009-03-02
> **whoop said:**
> Well looking at your screenshot your windows partition is currently taking up the entire drive (just about). So you have a good chance that my previous post is accurate:


I guess nothing can stop you from turning off/restarting your machine.

So I would try to defragment windows in safe mode. and resize windows partition. Looking at the screenshot it looks like you are installing using the server cd or the alternate desktop cd. You can't use these to resize your current partition. Safest bet will be to download partedmagic and resize the partition with that: [http://partedmagic.com/](http://partedmagic.com/)

I'm pretty sure I can resize the partition form the disk.
(Plus, I tried that program and I couldn't get it to work)
EDIT: I am using the livecd, it's just that I can't get the partitioner to come up on the regular install.

I'm just confused about how do do it.
When I hit "#1 primary..." there is a button that says "use as."
On the 1st screen (the one above) it says that the partition is ntfs (WHAT DOES THAT MEAN?). 
Should I choose that and then hit "resize the partition (currently 160.0 GB)"?

---

### Post by Rlad78 on 2009-03-02
Bumpity bump bump...

---

### Post by Rlad78 on 2009-03-02
K, so I got tired of waiting for almost 2 hours and decided to read the pocket guide. 

According to it, I'm supposed to hit
Guided - resize SCSI1 (0, 0, 0), partition #1 (sda) and freed s

If anyone disagrees, speak up before I press it...

EDIT:
> **whoop said:**
> 
I have seen posts in various threads of people who advise against resizing windows partitions using ubuntu livecd (don't really know why) I did it several times and did not have any problems; I mean it's not like the drive is mounted or anything.

 ](*,)

---

### Post by avtolle on 2009-03-02
> **Rlad78 said:**
> I'm pretty sure I can resize the partition form the disk.
(Plus, I tried that program and I couldn't get it to work)
EDIT: I am using the livecd, it's just that I can't get the partitioner to come up on the regular install.

I'm just confused about how do do it.
When I hit "#1 primary..." there is a button that says "use as."
On the 1st screen (the one above) it says that the partition is ntfs (WHAT DOES THAT MEAN?). 
Should I choose that and then hit "resize the partition (currently 160.0 GB)"?

The partition, if installing the Ubuntu o/s on it, needs to be formatted as ext3; I believe that is what the "use as" is for, the file system type (which is currently NFTS, the Windows default).

---

### Post by Rlad78 on 2009-03-02
> **avtolle said:**
> The partition, if installing the Ubuntu o/s on it, needs to be formatted as ext3; I believe that is what the "use as" is for, the file system type (which is currently NFTS, the Windows default).

So I have to do Manual?

I can't just hit 
Guided - resize SCSI1 (0, 0, 0), partition #1 (sda) and freed s

??

By the way, that is a screen shot of when I press Manual, not the first Partition screen.

---

### Post by Rallg on 2009-03-02
Picking up from the request for help at the "General" forum:

1. I assume your computer has USB. If you have not already done so, create a bootable live Ubuntu on USB stick. Then boot to it. If you do not know how to do that, info is available elsewhere on this forum.

2. If you can create the live Ubuntu on USB, and boot to it, but the boot fails sometime during Ubuntu load, then you have a problem that is unrelated to your hard drive.

3. If you can successfully boot to live Ubuntu on USB, go the the menu System, Administration, partition manager. When it loads, it may be aware of your hard drive and its own live USB. Using the selector at upper right of the program, be sure that you pick the hard drive. It won't say "hard drive," but you will know when you have the right one, because the display will show its expected contents with Windows.

4. If the partition manager is unable to read your hard drive, then you have a problem that the Ubuntu installer cannot fix directly.

5. If the partition manager can read your hard drive: Come back here, and tell us how many partitions you have, whether or not they are primary, what type they are, and what is in them. Then, we can advise you how to manually make good choices for partitioning.

COMMENT: The "guided" installation appears to mislead some new users. One advantage to a fully manual installation, starting from manual partitioning prior to using the installer, is that it forces the user to think about what will be happening within the computer.

---

### Post by Rlad78 on 2009-03-02
Picking up from the request for help at the "General" forum:

1. I assume your computer has USB. If you have not already done so, create a bootable live Ubuntu on USB stick. Then boot to it. If you do not know how to do that, info is available elsewhere on this forum.

[COLOR="Red"]My computer has USB, but I do not have a 5GB USB stick right now, so I can't put the entire livecd on the USB stick.[/COLOR]

2. If you can create the live Ubuntu on USB, and boot to it, but the boot fails sometime during Ubuntu load, then you have a problem that is unrelated to your hard drive.

[COLOR="red"]I used the disk self check that came on the disk and it seemed fine. The only trouble I've had so far is that if I don't do the Text installation, the regular installation crashes at 50% when loading the Partitioner (Says its reading disks). Another thing is that I just now tried to change the size of my Windows partition and an error comes up.[/COLOR]

3. If you can successfully boot to live Ubuntu on USB, go the the menu System, Administration, partition manager. When it loads, it may be aware of your hard drive and its own live USB. Using the selector at upper right of the program, be sure that you pick the hard drive. It won't say "hard drive," but you will know when you have the right one, because the display will show its expected contents with Windows.

[COLOR="red"]The screenshot on page 2 shows that.[/COLOR]

4. If the partition manager is unable to read your hard drive, then you have a problem that the Ubuntu installer cannot fix directly.

5. If the partition manager can read your hard drive: Come back here, and tell us how many partitions you have, whether or not they are primary, what type they are, and what is in them. Then, we can advise you how to manually make good choices for partitioning.

COMMENT: The "guided" installation appears to mislead some new users. One advantage to a fully manual installation, starting from manual partitioning prior to using the installer, is that it forces the user to think about what will be happening within the computer.

---

### Post by Rallg on 2009-03-02
You only need 1Gb for the live CD. It does not unpack Ubuntu there, but uses a compressed file system. The total is not much larger than the downloaded *.iso file. The live CD runs more slowly than a real installation would run, so you must be patient.

Also, if there is any hardware incompatibility (video, whatever), the live CD will probably have a problem.

One other thing: When changing the size of the Windows partition, it is best to move its end. Moving the start of the Windows partition can sometimes cause a problem with the Windows boot loader, especially if you later need to re-install Windows for any reason.

---

