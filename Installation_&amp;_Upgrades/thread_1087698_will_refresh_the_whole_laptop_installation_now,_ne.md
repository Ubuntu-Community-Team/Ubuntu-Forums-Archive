---
title: "will refresh the whole laptop installation now, need advise for dual boot"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by attilab on 2009-03-05
I am trying to make a dual boot XP-Pro and Ubuntu,
my laptop is an Asus barebone C90S w Nvidia GF8600M GT.
need the XP-Pro for work and want to have some fun with this Ubuntu as well.
started the installation severaltimes, but stepped back when I saw the ubuntu format start, it was unusual that I can not control where to instal the ubuntu, because I would prefer it on D partition. 
The case is that I had the initial windows format (C=NTFS; D=NTFS; M=Fat32) done before windows installation, don't ask me why, this is just my personal experience-preference and is probably discutable.
Now again some of my XP applications got very slow probably do to these trials, I am ready to format again.
reading on forum that many are doing format the entire HDD for windows and afterwards moving-extending the partitions.
1.)I am ready to start-try doing that way, my goal is to have the dual boot. 
2.)And to run both booths in most perfect performance, especially the XP programs.
3.)And, I allways have a user profile in XP, never work with Administrator
Have a time, waiting for your imput.
thanks in advance

---

### Post by mikewhatever on 2009-03-05
You can't install Ubuntu on an ntfs/fat32 partition, other then that, it doesn't matter if it's D or M under windows. You'll need to either delete or resize one of the existing partitions. Once you have unallocated space, the installer can format it.

---

### Post by gm75 on 2009-03-06
I have the same laptop with dual boot.

here's my setup:
1. 30 gig windows
2. 256mb /boot ext3
3. 20 gig / ext3
4. 196 gig shared fat32
5 4 gig swap

I started off with a blank hd so installed windows first w/ntfs on the whole drive. Resized ntfs to 30gb within windows w/ partition magic.  Then used ubuntu alternate install disk to make the partition in the empty space.

You should install ubuntu after xp to make the grub setup easier.  Install grub to the mbr and it'll take care of windows booting for you.

If you ever need to format windows and you wanna maintain the dual boot you need to reinstall grub after.  Or just prepare yourself to format both.

Camera and video out dont work with 8.10 but its a small price to pay for freedom.

---

### Post by LegendofTom on 2009-03-06
Just install windows on the whole disk and use the ubuntu partition manager on the install disk to allocate what you want for each.

---

### Post by attilab on 2009-03-09
so, I am back, format the HDD last nite again,
3 questions (based on my old DOS and Windows experience):
- what is a difference formating and repartitioning with (?)partition magic and leaving one portion empty=free? 
- or partitioning w/ Fdisk but leave one partition w/o format in RAW what I again consider it empty=free?
- or formating with windows and resize a partition to get a portion=space empty=free?
for me as a DOS-Windows guy not much different, used to install these once wher ever I want, but somehow can't make ubuntu:
- 4 days ago, I create (Fdisk) 3 primary partitions, 2x NTFS and left one RAW. when I installed ubuntu, manual selection to RAW but again didn't format the empty=RAW but butchered my XP.
- last nite again I create 3 primary partitions, first NTFS for XP second Fat32 for future shared, then from inside XP/Disk Management toke the third RAW primary and made it Extended, and inside Extended create 3x logical drives, temporary just put a FAT32 but can remove.
Ready again for ubuntu, wondering how to make ubuntu install there.

---

### Post by upchucky on 2009-03-09
xp needs about 25 gig, this is because some brainless developers are still writing programs that will only install on the c drive. the only thing that should be on a windows c drive is the operating system period, that way when windows self destructs as it is designed to do, it is a simple matter to just restore it from your back up image that you were clever enough to make using NTFSclone, and not have to reinstall any other programs and files. and the fact that windows by default dynamically changes its swap file size whether it needs to or not, in fact it uses the swap file even if there is excessive amounts of ram.

Ubuntu core needs at least 10 gigs, and a 1 gig swap file that it never uses, however since i have tons of room I also give linux 25gigs

I have an existing NTFS "D" drive of 250 gigs for all windows files.
I created a 250 gig EXT3 partition for the ubuntu home directory, this ensures that in the unlikely event that I have to re-install ubuntu any files and programs in ubuntu stay intact.

not sure why you want a fat 32 partition.

If you are really interested in understanding the partitions and how it all comes together, then get the knoppix cd, its free. it has two partition managers on it and safely works with the exotic ntfs windows partitons, it also lets you edit any files you need in windows and ubuntu to get both working as a dual boot, this includes setting up the menu.lst file in grub to tell it the drive info and how to set up the chainloader for windows.

you may also need advanced supergrub disk, it will repair the master bootloader in case either os will not boot.

---

### Post by attilab on 2009-03-09
totaly agree for windows, I can say I master it (as a user and not programmer) since v3.11 from the DOS4.5 time. My son uses leopard, so I need to balance it out a bit, want to entertain with linux. Im working with CAD package and sometimes bored, what else but play with XP.
also, I don't believe in windows clone, might work for some word processing, maybe some games, but definitelly not stabil for HP demanding programs as 3D CAD/CAM/CAE.
the Fat32's are there just for nothing easy to remove and leave it RAW.
now, my difficulty is to understand what I did wrong with last installation, I had an empty space (primary partition) call it M (right behind C NTFS and D NTFS) and it was RAW primary partition, point the installation there, but still went to C boot, something partially. So, I assume didn't like the RAW primary partition, now I put fat32 but on extended partition devided to 3 logical drives, so it might take it more friendly? hah, me alone, just to many options to try...no friends nobody close by to take a closer look.
for now just not enough brain to understand the dictinary what is what.
Does exist something with pictures? step by step? first of all the english is my 5th language, so there might be a problem as well- to start excusing...
I assume just the "\" is a root, Im sure I point it to RAW last time.

---

### Post by attilab on 2009-03-10
seeing many instructions/helps regards to a resizing partitions in existing Windows Vista or XP. My understanding is that Microsoft built in some of these tools for ppl not to mess around with the formating and partitioning  >>> before they install or reinstall the Windows OS
don't see however are there any specific methods if I create the empty space (extended partitions and logical drives) right there at the Fdisk, and before the windows installation.
wondering if might be any differenc how ubuntu is interpretting the totaly diferent approach?
I am ready to go with my 3rd attempt to install ubuntu parallelle with XP.

---

### Post by attilab on 2009-03-10
anybody can lead me in with soem picturial instractions, how to do the installation with allready prepared (Fdisk) partitions
soemhow I just can't manage ubuntu hump on that RAW (3rd primary/extended partition w/ logical drivess) space

---

### Post by Neo_The_User on 2009-03-10
AFAIK, Ubuntu requires the CD to format your HDD for you regardless of whether its already prepared. You have to do it all via CD installation GUI AFAIK. I tried doing the same in the past. I personally think its stupid. :violin:

---

### Post by attilab on 2009-03-10
understand that need a proper linux format
fine, do it @ the location (partition) what I sad (whoow, sounds ...)
I point it 2x allready to there, but digged out my XP
that's not nice
I am noty a programmer, need some pictures

---

### Post by attilab on 2009-03-10
> **Neo_The_User said:**
> AFAIK, Ubuntu requires the...all via CD installation GUI AFAIK....stupid. :violin:

Let me simplify, here is the example:
1. me in canada (imported guy) facing with traffic signs, the majority is text based. Can you imagine how we were driving arround for a while till we learned the language...
2. you go to IKEA, buy a whole large kitchen cabinets-furniture and able to put it together with no words in the instruction book...

---

