---
title: "Installing Ubuntu on Vista laptops with mutliple partitions!"
date: 2007-09-13
forum: Georgia Team - US
---

### Post by siafulinux on 2007-09-13
This is in response to the original post at [http://ubuntuforums.org/showthread.php?t=538010]("http://ubuntuforums.org/showthread.php?t=538010")

> Hi Jean-Claude.

Speaking of wasted partitions. I recently got a Dell XPS M1710 with Vista Business. It came with four paritions. That's right, count em, four partitions:
1. the standard Dell 48mb partition right at the front of the drive that has no drive letter. Every Dell has one of these.
2. The main data drive (NTFS)
3. A drive labeled 'recovery' with some Vista OS files on it
4. A small partition wasted, not assigned to any drive

I could not believe this. I wanted to put Ubuntu 7.04 on this laptop and I cannot now unless:

a. someone knows a way around the four partition limit on any one physical drive
b. someone knows how to consolidate these partitions without me wiping and re-installing.

I guess if I get mad enough I may rip the whole thing apart and consolidate Vista onto a single partition.

Rick



Wow four! I was surprised to hear of three on my friend's laptop; 2 33 gigs partitions, one with Vista and one called Data and then a 7.5 gig restore partition. We simply used the 3rd DATA partition and everything is working fine.

As for your's I probably wouldn't get rid of the Dell partition; I've heard of systems and seen one laptop in particular that used just such a setup for some "extra" BIOS or other data that the system needed. Yes I know, it's pathetic. I'm not sure if Dell does this or not, but I would assume this is the case. I believe EMachine systems are the same, but I could be wrong.

Does your recovery setup allow you to make backup discs from within Vista? I remember my HP desktop system originally asked me to make backup DVD's or CD's at first boot and had a menu option to do so, but only one set. The system now proudly has Kubuntu and only Kubuntu! :-)

What I am suggesting is possibly creating your backup discs and this way you can remove the recovery partition and that "extra" one. Then resize your main NTFS partition to give you even more free space using QTParted from the Ubuntu Live-CD. 

You'll end up with:
1. The 48mb Dell partition needed. 
2. The main NTFS/Vista drive and 
3. Free space on which to create your Ubuntu setup. 
4. Still have backup Vista discs, just in case!

Otherwise if you are not interested in keeping Vista, you can simply get rid of 2, 3 and 4 and have the 48mb Dell partition and free space to use nothing but pure Ubuntu with! :KS

Before you do anything though, make sure you have backup discs for Vista (you've already paid for it, might as well keep a copy) and then have backed up any important data on the system that you want to keep!

Jean-Claude

---

### Post by rsmereka on 2007-09-13
Hi Jean-Claude,

This particular laptop came with the Vista re-installation DVD so I do not think I will need to make any disc's. I will, however, need to verify that I have all the necessary hardware drivers.

This laptop is my business machine and the operation we are discussing is pretty radical surgery and I was hoping that there may be another, less invasive way of putting Ubuntu on the laptop.

Thanks for your advice,
Rick

---

### Post by siafulinux on 2007-09-14
Hey again

Actually I thought that was about the simplest way of going about it. Unless you simply make the NTFS drive smaller with a Live-CD and use the freed up space? However at that point you might as well remove the other "wasted" space partition and the recovery partition as well. If your restore DVD isn't going to need any of those files from the recovery partition, that is.

If you need a guide on doing the above I may be able to put something together for you or find one online. It's really not hard, but you may lose your Windows partition while trying to resize it - it's a risk that goes with the territory, 

Another option may be to use an Ubuntu Live-CD with a resized NTFS to give you enough free space combined with the "wasted" space to create a new FAT32 partition instead. This would be used to save files and settings on while using the Live-CD and though it will be slower this way, you wouldn't be changing a lot with the hdd.

Last thing I can think of at this hour and probably more in line with what you are looking for, is to use an external hard drive if your laptop can boot from it. Just plug it in when needed and boot up into Ubuntu and your laptop hard drive wouldn't need to be messed with at all. You may need to use a boot CD or floppy disk. You should also be able to transfer files between your NTFS drive and your Linux drive as well.

Maybe someone else can pitch in some more ideas?
Jean-Claude

---

### Post by rsmereka on 2007-09-14
Hi Jean-Claude,

Thanks for all your suggestions but re-sizing the NTFS partition to make room will not work because this laptop is already at the four partition limit on this disk courtesy of Dell. I cannot create another partition. I guess I could destroy the recovery partition and use that partition for Ubuntu but the drive size is very small (around 5gb I think).

Rick

---

### Post by oddin85 on 2007-09-14
turn the wasted partition into an extended partition where you can have as many logical partitions as you need :-) but 1st resize the windows partition so that you will have enough space for a linux install and for some swap maybe even a partition for your /home directory if you want

---

### Post by lordikyiky on 2007-09-16
here is the experience I had:

I have a dell inspiron, and it too had 4 partitions when I got it.  To try and install linux, I deleted one of the smaller "waisted" partitions and then shrunk the windows partition to make more room.  Then I installed linux, and windows no longer worked :mad: So, I completely reinstalled windows, and suddenly it only used up 1 partition :confused:  So basically the other 3 partitions are not important.  But when I repartitioned the hard drive again to install linux, windows again, no longer worked.......In order to make it work on my machine, I had to create a logical partition to put linux on, and then create the partition to put windows on, then install windows, and finally install linux.  After that everything works great, and I can reinstall linux on the logical partition whenever I feel like it :)

---

### Post by rsmereka on 2007-09-16
Thanks for the post,

Now I am getting scared. I guess the upshot is that Windows may not run after the re-size. This is strange since I have installed Linux may times on PC's that are 100% Windows and the result was great without any consequences but I always have a habit of turning off VM in Windows (which deletes the page file) and then running a defrag before re-sizing.

Rick

---

### Post by jynyl on 2007-09-22
As reported elsewhere, Vista uses a slightly different form of NTFS, which seems to be more fragile.  If Linux resizes the Vista partition, Vista won't boot (but Linux works fine :)  ).  This is different to Win2000 and XP.
However, Vista includes a partition editing tool.  Use this to resize your ntfs partition, and Vista should be ok.

HTH

Peter

---

### Post by siafulinux on 2007-09-22
Thanks for that Peter!

Jean-Claude

---

