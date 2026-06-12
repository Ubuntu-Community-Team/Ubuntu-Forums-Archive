---
title: "Gutsy on HP nx9420"
date: 2007-10-18
forum: Hardware &amp; Laptops
---

### Post by koytetsu on 2007-10-18
I have run the last 4 (I think) releases of Ubuntu on this laptop without much issue.

I am debating going back to Gutsy now from Vista today.  I have downloaded the CD but have some hesitation after reading the issues here and the fact that ATI hasn't released .42 yet.

Has anyone else loaded this final on a laptop with an ATI X1600 Mobility?  Are there wireless networking issues in this build or standby/sleep problems?

Also I noticed when I tried the Gutsy beta awhile back it installed Grub but there was no entry for my Vista partition?  Do you need to manually add your old windows install to the grub config?

Thanks for any insight anyone can provide.

---

### Post by Atticka on 2007-10-18
I've been running 7.04 (fresh install) on my NX9420 without issue, I'll be going through the upgrade process this evening.

The only issue I had with 7.04 was the wide screen resolution was not listed/detected. I had the modify X  to add the resolution.

Aside from this, 7.04 had no issue's with wireless....I can't see 7.10 getting worse.

---

### Post by mindlight on 2007-10-19
I am running 7.10 on my HP NX9420 right now.

There is (as always with ATI Radeon and Linux) problems with the graphics.

1. When booting up, you wont see no boot splash when booting from the harddisk. From LiveCD its ok. This seems to be a bug in the /etc/usplash.conf that has to be edited and then you need to make a new initramfs. Google it and you will find a solution.

2. Desktop Effects - Does not work. When going into System -> Preferences -> Appearance and then the Visual Effects tab it is not possible to enable anything else than "None". You will get a error message on the screen telling you: "The Composite extension is not available". 
I have found a solution on the web for this too but not able to find it again. It was agout installing xgl xserver. Still, dont know if this is to be counted as a workaround either.

---

### Post by ivanox1972 on 2007-10-20
Uh I cant even boot live CD... It starts, but somewhere in the middle CD and hard disc just stops any activity and notebook ejects CD... I don't know why? Any help...

---

### Post by mindlight on 2007-10-21
Ivanox,

have you checked the cd for errors?

Are you running a HP nx9420 laptop?

---

### Post by ivanox1972 on 2007-10-22
Hm, yes I have checked CD for errors it it hasn't found any one...
But definitely problem is with my notebooks optical drive...
I also had problems in the past with him...
Generally, 7.10 should go live CD on nx940 (unlike 7.04) isn't it?

---

### Post by mindlight on 2007-10-22
My NX9420s drive is a little bit quirky and doesnt always boot burned cds so it might be that nx9420 has a cheap dvd-drive or something.

But the livecd should boot up to X and from there you can run the installer.

I dont have a clue what could be the problem since your cd is ok... maybe your dvd-drive is broken, as you suggested.

If possible, try to boot with a USB-CDROM if you have one.

---

### Post by qwerion on 2007-11-02
I can has Gutsy for a month now...since beta version.
Using fglrx driver with xgl only to watch movies, otherwise - no xgl. When using xgl with BigDesktop feature I can't fullscreen applications to one display, it always streches to both displays - realy annoying...so, for work (using two displays) I disable xgl.
Suspend and hibernate doesn't work.
Firestarter crashes often (GUI part...)

I've tryed this [https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420](https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420)
but doesnt work for me....:confused:

One more thing, about ACPI...before Ubuntu on this laptop there was WinXP. Battery lasted for 3.5 hours. Now, under Ubuntu - 2 hours tops...:confused:

Overall feeling? I like it, just that suspend thingy and me happy.

---

### Post by qwerion on 2007-11-03
One more thing - just did it and it works: [Gusty ati 8.42.3 fglrx - with AIGLX support how to]("http://ubuntuforums.org/showthread.php?t=593348")

Now, fullscreening application to one display at time works :)

Strange stuff: video playing flickers...working on that...
------
ha!
added this to xorg.conf under
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"

#ADDED:
	Option	"XaaNoOffscreenPixmaps"
	Option	"AGPMode" "8"
	Option	"AGPFastWrite" "yes"
	Option	"EnablePageFlip" "on"
	Option	"ColorTiling"	"on"
	Option	"RenderAccel" "yes"

---

### Post by ivanox1972 on 2007-11-21
I have replaced damaged DVD drive... It is good news.
But, now bad news... Live CD cant boot... It is going and on the and says he cant rise 
Xsrver... As I saw here, 7.10 can boot live cd on nx9420...
What is problem on mine machine- is it possibile that something in bios must be changed...
Course, everything other is same on every nx9420 when you boot from cd...

---

### Post by mindlight on 2007-11-21
Ok, a silly question, and please dont take offense.

Are you sure that it is Gutsy (7.10) and not Feisty (7.04) you have on that CD?
As I can recall, Feisty had that exact behaviour when installing it on NX9420.

---

### Post by ivanox1972 on 2007-11-26
Yes, what a stupid error- I have put 7.04 in CD:confused:
With 7.10 and good CD drive Live Ubutntu finally works...
But now I have other problem- when I want to install... Installer sees only my entire hard disc...
i have 4 partitions XP, Fedora Vista and data...
I want to split data partition and install there not to lose other OS- what to do...

---

### Post by mindlight on 2007-11-26
Hmmm..

Since write support for NTFS is farely new and maybe not mature yet I wouldnt go for resizing an important partition with GPL software.

I would recommend you to boot up in windows and install an application that handles resizing paritions.

There are many commercial resizers "out there" that are worth using.
I use Acrons Disk Director which I recommend using.

---

### Post by ivanox1972 on 2007-11-27
yes, but I already have 4 partitions but 7.10 dont sees them...
You think that if I prepare partition by Partition magic, for example, loader will see that one...
I dont think...
Also, Partition Magic even cant open on mine notebook- it said that partition are made on some other way (whatever that means) and just closes...

---

### Post by mindlight on 2007-11-27
oh.
So when you look at /dev/sda you see nothing?

If partition magic just gives you and error this means that the partition information stored in the MBR (Master Boot Record, which is the first part of the harddisk which is the place where PCs store all information of the partition types on the disk, where each partition starts, ends and if any of them are bootable.) is not correct.
Partition Magic is in my experience a program that is VERY picky when it comes to handling the partitions. Thisi is probably because that it shouldnt try to do somethings with partition if the partitions are in a stat that it doesnt understand / recognize.

Can you test with Acronis DD instead? Dont know if that will help but it might be able to handle your partitions.

If the partition table is corrupt, windows will still be able to boot but it can be very dangerous to resize or move partitions. That is probably why PM dont start and why Ubuntu wont show you anything. So if you do continue with Ubuntu install: Do a BACKUP of all your important data and make sure you have burned the recovery DVD /CDs.

Could you open a terminal (when booted into livecd) and run:
sudo cfdisk /dev/sda

This is a partitioner for console which never lies ;)

Tell me what you see there.

---

### Post by qwerion on 2007-12-01
plz, guys...does your suspend (to ram) work?

---

### Post by mindlight on 2007-12-02
No. Not m,ine... but as I understood it, during my google sessions about this issue, this is a major bug which not only affects nx9420 but a lot of other PCs...
It will be fixed as I understood it.

---

### Post by ivanox1972 on 2007-12-04
@mind light
I was very very busy last days on job- cant play with Ubuntu...
I tried sudo cfdisk /dev/sda and it sees all mine partitions just as it is- win xp, vista, fedora (grub is boot manager- first I decide fedora or windows and then xp or vista from windows boot menu) and one data partition... 
i wanted to resize that data partition to make space for ubuntu..
Can I do that from this command... also how big partition to make  and how big swap partition (I have 2GB RAM)
thanks...

---

### Post by ivanox1972 on 2007-12-09
to refresh... any help...

---

### Post by ivanox1972 on 2008-01-12
this thread is dead... Any help???

---

### Post by qwerion on 2008-03-31
Nop, it's not dead :P we are still alive...
anyway...still running 7.10 on my laptop, using latest ATI drivers, but NO compiz...java apps don't like it.

only problem left is suspend to ram / hibernate... gona do with uswsusp), but I still don't get it

---

### Post by cjsteele on 2008-07-10
> **qwerion said:**
> I can has Gutsy for a month now...since beta version.
Using fglrx driver with xgl only to watch movies, otherwise - no xgl. When using xgl with BigDesktop feature I can't fullscreen applications to one display, it always streches to both displays - realy annoying...so, for work (using two displays) I disable xgl.
Suspend and hibernate doesn't work.
Firestarter crashes often (GUI part...)

I've tryed this [https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420](https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420)
but doesnt work for me....:confused:

One more thing, about ACPI...before Ubuntu on this laptop there was WinXP. Battery lasted for 3.5 hours. Now, under Ubuntu - 2 hours tops...:confused:

Overall feeling? I like it, just that suspend thingy and me happy.

Suspend using the patch mentioned in the wiki ([https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420](https://wiki.ubuntu.com/LaptopTestingTeam/HPnx9420)) works without incident on my nx9420... what version of the nx9420 do you have?  There may be subtle chipset differences.

---

