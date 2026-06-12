---
title: "2 Harddisks - dual booting - winxp and ubuntu"
date: 2008-08-05
forum: General Help
---

### Post by Swan_aBohovian on 2008-08-05
Hi!,
I want to have dual booting with winxp and ubuntu.
Right now, 
1) Harddisk1 --> having XP and some crucial data
2) Harddisk2 --> empty.

I was suggested as follows : 
1) Make XP disk master and load ubuntu files on the slave empty harddisk
2) Change the settings and make the XP disk the slave and the blank disk the master.
3) Install Linux on the (blank) master HDD (with grub installed on this disk).

Now my QUERY is, that once i load the necessary ubuntu installation files on the blank harddisk, then JUST FOR THE SAKE OF RISKFREE INSTALLATIION, can i disconnect my Harddisk1 ( having XP ) , before i install Ubuntu ? 
And after installation, and connecting the harddisk1 again, would there be problem in dual booting.

The reason i want to disconnect the harddisk1 before installing ubuntu is, that i don't want to take the risk of selecting wrong drive by mistake, and the overwriting my XP harddisk.

Thanks. :)

---

### Post by Zakhafr on 2008-08-06
I have similar needs, and I'm also interested on feedbacks from those who know/have done it.

Let's try to be as clear as possible !

I have a system with two disks.
Disk 1 has Vista (and XP for Dell Media Direct)
I'll like to have Ubuntu on disk 2.

As swan, I'll like to have two **totally independent** installations.
- No BootMGR menu on Vista partition to boot Ubuntu on Disk2
- No Grub-Startup Menu on Ubuntu (Disk 2) to boot to disk 1.

I'll manage multi-boot from BIOS.
Every recent PC uses F12 to allow "One time boot", that is good to boot once to the OS that is not your default.
And if you want to change the default, BIOS will do it.

From what swan write, I'll doubt Windows will still boot if it is not on the first disk !

As of Hardy, _there is an option_, when you install, to _install GRUB to a different disk_ than default (first disk).

**Question is**, if I use this option, will it _NOT AT ALL_ impact Windows MBR/BootMGR on disk one and install all the part of Linux GRUB on disk 2.
Or will it anyway modify MBR/BootMGR on disk one so that I have a menu when I boot from disk one: that is NOT what I want, I'm fine dual-booting with BIOS, so that both systems are totally independent.

Of course unplugging disk one when doing the Ubuntu install is the best solution to be sure you don't mistake, an also that Ubuntu will not try to modify Windows MBR/BootMGR. If Disk 1 is unplugged, Ubuntu will also not try to detect other OS during install and put them in it's own GRUB-startup menu.
But as my PC is a laptop, it's less easy to unplug disks !

[I]**@swan:** I can see two problems in your suggestion:
- as I said, I doubt windows will still boot if it is not on first drive. Just try it switching disks...
- if you unplug disk 1, the other disk having no system at all, you will not be able to boot your PC for the Ubuntu installation. So you need to burn the image you have on you "data" disk to a CD-R or CD-RW. Then unplug your disk 1 and boot from CD.[/I]

---

### Post by RedPandaFox on 2008-08-06
I have the same set up as swan. 
All I did to achieve duel boot with xp and ubuntu was install ubuntu to the 2nd hdd and install grub to hd0, it does everything for yo, or should do. if you want to be safe tho, install grub to second hdd and tel BIOS to boot to 2nd hd so it wont effect xp at all but you can still boot to it, then if you have a problem you should be able to tell the BIOS to boot to hd0 and shouldn't cause any problems

Leave the first hdd there, i would not suggest taking it out, just find out the sizes, if they different sizes, just seek the correct size, if not then just it should be hd0 and hd1 i think it would be, then it will put an option in the grub to boot to XP or 'buntu

---

### Post by logos34 on 2008-08-06
> **Swan_aBohovian said:**
> 
Now my QUERY is, that once i load the necessary ubuntu installation files on the blank harddisk, then JUST FOR THE SAKE OF RISKFREE INSTALLATIION, can i disconnect my Harddisk1 ( having XP ) , before i install Ubuntu ? 
And after installation, and connecting the harddisk1 again, would there be problem in dual booting.

The reason i want to disconnect the harddisk1 before installing ubuntu is, that i don't want to take the risk of selecting wrong drive by mistake, and the overwriting my XP harddisk.

Yes, you can do that.  You'll just have to manually add a windows boot entry to menu.lst, as well as a line to /etc/fstab if you want to access XP from linux side:

[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.04%20LTS%20(Hardy%20Heron](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.04%20LTS%20(Hardy%20Heron))

---

### Post by Zakhafr on 2008-08-06
> **RedPandaFox said:**
> install ubuntu to the 2nd hdd and install grub to hd0

Of course that works ;-)
But it modifies Windows Boot sequence adding a screen with a choice + timeout, and I don't want that.

> **RedPandaFox said:**
> If you want to be safe tho, install grub to second hdd and tel BIOS to boot to 2nd hd so **it wont effect xp at all** but you can still boot to it

Yes, this is precisely what I would like, but are you **really sure** it works like that... you didn't do it that way.
What I suspect is that Ubuntu will try to "help" you, and that it will put part 1 of GRUB in hd0 and part 1.5 on hd1.
On the windows partition it might add the screen to boot Ubuntu.

That is what I do NOT want.

Of course unplugging the Windows disk makes sure it won't do this way, but it is a risky hardware operation on a laptop. Furthermore, I might loose my warranty if I open it by myself.

---

### Post by logos34 on 2008-08-06
> **Zakhafr said:**
> 

**Question is**, if I use this option, will it _NOT AT ALL_ impact Windows MBR/BootMGR on disk one and install all the part of Linux GRUB on disk 2.
Or will it anyway modify MBR/BootMGR on disk one so that I have a menu when I boot from disk one: that is NOT what I want, I'm fine dual-booting with BIOS, so that both systems are totally independent.

Of course unplugging disk one when doing the Ubuntu install is the best solution to be sure you don't mistake, an also that Ubuntu will not try to modify Windows MBR/BootMGR. If Disk 1 is unplugged, Ubuntu will also not try to detect other OS during install and put them in it's own GRUB-startup menu.
But as my PC is a laptop, it's less easy to unplug disks !

You can avoid any possible confusion as to which disk is '(hd0)' and '(hd1)' by using the '**/dev/sdx**' format.  So if the installer sees your ubuntu disk as /dev/sdb, then:

step 7 'Ready to Install' screen

-> 'Advanced' button lower right

-> replace default '(hd0)' with [B]/dev/sdb

[/B]Grub will install, writing stage1 portion to the MBR of the Ubuntu (not windows) disk, and you can toggle the boot order for your desired OS session.

You'll have to do just one thing when you try to boot into ubuntu the first time:

-> on the grub menu screen press 'e' on the highlighted ubuntu kernel, 'e' again on the 'root' line and change to (hd**0**,?).  'Enter' and 'b' to boot.  Once it loads make the change permanent:

gksudo /boot/grub/menu.lst

-> change 'root' and 'groot' lines to match.

---

### Post by caljohnsmith on 2008-08-06
Zakhafr, when you go to install Ubuntu, since you don't want it to touch your Windows drive, first do the following from the Live CD:
```
sudo fdisk -l
```
So that will show your drives, and look for the one that says it has a NTFS file system. That of course will be your internal HDD with Windows that you don't want to touch, and it will most likely be /dev/sda. 

Now that you know for sure which is your Windows HDD, when you go about installing Ubuntu on your other HDD, when you get to the Grub installation part, use the "advanced" options to make sure you install Grub to the MBR of your *other* HDD; in other words, not /dev/sda or whatever is your Windows drive. Again, most likely you will be installing Grub to /dev/sdb. 

But now the tough question--how are you going to boot Ubuntu? It is possible to [modify your Windows bootloader]("http://ubuntuforums.org/showthread.php?t=56723") to give you an option to boot Ubuntu. Or you could go into BIOS every time you want to change which HDD to boot from. Or you could easily create a Grub boot floppy (I've done this) that will allow you to boot Ubuntu on the second HDD. Let me know if you need more details.

---

### Post by Zakhafr on 2008-08-06
Thanks everyone for your help.

I'm not quite totally reassured by your answers :confused:

> **caljohnsmith said:**
> Again, most likely you will be installing Grub to /dev/sdb.

I don't like the "most likely" part!
Do you mean "most likely" my second drive will be /dev/sdb (it is indeed), or "most likely" if you say /dev/sdb it will install here... but not quite 100% sure ;-)

> **caljohnsmith said:**
> But now the tough question--how are you going to boot Ubuntu? It is possible to [modify your Windows bootloader]("http://ubuntuforums.org/showthread.php?t=56723") to give you an option to boot Ubuntu. Or you could go into BIOS every time you want to change which HDD to boot from. Or you could easily create a Grub boot floppy (I've done this) that will allow you to boot Ubuntu on the second HDD. Let me know if you need more details.

In fact it is a very easy question. Nevertheless I can understand it is a bit puzzling if you haven't seen a modern PC recently.

My BIOS has the option to choose which device I want to boot from first. In fact you define the poll sequence, let's say :
1- CD-ROM
2- HDD 1
3- HDD 2
4- USB Disk
5- Floppy (although I have no floppy drive, so this is not proposed by BIOS)
With such a sequence, BIOS would try to find an OS on the CD first, then on HDD 1, then on HDD 2, and so on.

First OS found will be booted.

So to change once for all the default OS I just go on the BIOS and change the order, switching HDD 2 in front of HDD 1.

Now let's says Ubuntu is on HDD2 (/dev/sdb), I set it as default on BIOS ordering it to scan HDD2 before HDD1, and I want, just this time to boot on HDD1 to launch a Windows game that do not work properly on Ubuntu. For that I don't need to go to the BIOS, change the params, boot, then change them back again in the BIOS. This would be quite a complicated manipulation.
Modern PC have a very convenient option: at Boot time, you hold F12.
This calls the "One time boot menu".
From there, you choose the boot order, same as described above for the BIOS, but it is only "one time", and next boot it will use standard BIOS parameter again.


So if you are using Ubuntu 90% of the time and Windows 10%, this is a very good method.
Of course, if you randomly use both OS, the "old" GRUB-Menu method is as good, because you might get bored waiting for the right moment to hit F12!

For instance, I use the "one time boot menu"-F12 key at work when I want to boot on my Mandriva USB Key instead of stupid XP Professional! After having held F12 at BIOS boot, I get the menu, I put USB Disk in first position, and it works perfectly!
And that is, most of the time at work I'm working ;-) But sometimes, at lunch break, I like to use my special Mandriva Key!
"One-time boot menu" thus is wonderful for that.


> **logos34 said:**
> You can avoid any possible confusion as to which disk is '(hd0)' and '(hd1)' by using the '**/dev/sdx**' format.  So if the installer sees your ubuntu disk as /dev/sdb, then:

step 7 'Ready to Install' screen

-> 'Advanced' button lower right

-> replace default '(hd0)' with [B]/dev/sdb

[/B]Grub will install, writing stage1 portion to the MBR of the Ubuntu (not windows) disk, and you can toggle the boot order for your desired OS session.

You'll have to do just one thing when you try to boot into ubuntu the first time:

-> on the grub menu screen press 'e' on the highlighted ubuntu kernel, 'e' again on the 'root' line and change to (hd**0**,?).  'Enter' and 'b' to boot.  Once it loads make the change permanent:

gksudo /boot/grub/menu.lst

-> change 'root' and 'groot' lines to match.


This is **very **useful Logos34!
But to be sure, I'd like to understand **WHY **and not only **HOW**.

So if I interpret correctly your instructions, you mean that when I installed, I booted in the order :
1- CD-ROM = CD with the Ubuntu Live/installation program
2- HDD 1 = hd0 = /dev/sda (Vista)
3- HDD 2 = hd1 = /dev/sdb (Ubuntu)

Then once I have switched in the BIOS HDD 2 in front of HDD 1, as HDD 2 is scanned before HDD 1, from Ubuntu it becomes :

HDD 2 = hd0 = /dev/sda (?.. or is it still /dev/sdb ?)

I makes sense, and would explain why it did not work at all when I tried first time this type of install (at the time of 8.04.00).
Of course, when I installed it it was hd1, so that's what on GRUB menus, and once reversed by the BIOS it becomes hd0... and GRUB do not find any GRUB 1.5 stage on hd1 (which is now Vista Disk).

_Is my understanding correct ?_

If the understanding is correct, what if I set the boot order to:
1- CD-ROM
2- HDD 2
3- HDD 1 (the one with Vista)
**during installation.**

If it is set so, wouldn't HDD 2 appear as hd0 (/dev/sda ?) during Ubuntu Installation, so that I don't even need to bother changing default hd0 GRUB installation or doing the trick you suggest at first time.

*[Note... I think I can safely check if it works like that, using Ubuntu in Live CD mode, so that it does not write anything to disk, and watch disks partitions when I change disks order in the BIOS]*

**And last question...**
I fear Ubuntu tries to scan "other disks" for existing OSes.
As I explained, I'd rather **NOT **unplug it, to avoid loosing warranty on my laptop.
At the moment, I have it installed through Wubi, and that's what it did.
So when I will install like that, it will probably add Vista to it's list of existing OSes... which would be quite useless because I doubt Vista would boot with the BIOS set as explained, because then Vista will not be on "first" (scanned) drive where it needs to be in order to boot.

Anyway, I presume that if Ubuntu adds a line to boot windows in its GRUB menu, there is a way to remove it, as it is a useless line!

---

### Post by logos34 on 2008-08-06
> **Zakhafr said:**
> So if I interpret correctly your instructions, you mean that when I installed, I booted in the order :
1- CD-ROM = CD with the Ubuntu Live/installation program
2- HDD 1 = hd0 = /dev/sda (Vista)
3- HDD 2 = hd1 = /dev/sdb (Ubuntu)

Then once I have switched in the BIOS HDD 2 in front of HDD 1, as HDD 2 is scanned before HDD 1, from Ubuntu it becomes :

HDD 2 = hd0 = /dev/sda (?.. or is it still /dev/sdb ?)

I makes sense, and would explain why it did not work at all when I tried first time this type of install (at the time of 8.04.00).
Of course, when I installed it it was hd1, so that's what on GRUB menus, and once reversed by the BIOS it becomes hd0... and GRUB do not find any GRUB 1.5 stage on hd1 (which is now Vista Disk).

_Is my understanding correct ?_

Exactly.  

The device name remains the same (sdb) but the Grub/Bios designation changes to (hd0) as soon as you make it the boot disk.




>  If the understanding is correct, what if I set the boot order to:
1- CD-ROM
2- HDD 2
3- HDD 1 (the one with Vista)
**during installation.**

If it is set so, wouldn't HDD 2 appear as hd0 (/dev/sda ?) during Ubuntu Installation, so that I don't even need to bother changing default hd0 GRUB installation or doing the trick you suggest at first time.

*[Note... I think I can safely check if it works like that, using Ubuntu in Live CD mode, so that it does not write anything to disk, and watch disks partitions when I change disks order in the BIOS]*

Sure, you can change the order of the hard disks before installing, in which case it should become (hd0) and you wouldn't have to edit anything.  Either way. 
 > 
**And last question...**
I fear Ubuntu tries to scan "other disks" for existing OSes.
As I explained, I'd rather **NOT **unplug it, to avoid loosing warranty on my laptop.
At the moment, I have it installed through Wubi, and that's what it did.
So when I will install like that, it will probably add Vista to it's list of existing OSes... which would be quite useless **because I doubt Vista would boot with the BIOS set as explained, because then Vista will not be on "first" (scanned) drive where it needs to be in order to boot.**

Anyway, I presume that if Ubuntu adds a line to boot windows in its GRUB menu, there is a way to remove it, as it is a useless line!

No, ubuntu is pretty good about adding the right entry that will boot vista/windows on a second hard disk--it does a trick called 'virtual swap' ([http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)).

At any rate, yes, you can simply delete the entry from menu.lst if you wish.

---

### Post by Zakhafr on 2008-08-06
Many many thanks Logos34.

Now it's all perfectly clear.

I'm preparing CD-ROM with Ubuntu 8.04.01-amd64 and I'll test all of that very soon.

---

### Post by Zakhafr on 2008-08-07
At the moment my data disk is a bit too full to install Ubuntu...
It's cluttered by huge files (truecrypt volumes).

But I'll have a last question.

When I boot with the CD, is there a mean to know which disk will be considered as hd0 by GRUB.

I mean, I have
/dev/sda
/dev/sdb

One of them is going to be hd0, the other one hd1.
It could depend on the order of the disks declared in the Bios.

In order to check that, I started from the CD, but then, I have no /boot/grub directory to tell which is what.

(hd0 = sda and hd1 = sdb)
or
(hd1 = sda and hd0 = sdb)

Is the device.map file somewhere else when booting in Live CD mode, or is there a command to know the association ?

---

### Post by logos34 on 2008-08-07
in a terminal try 
> **sudo grub**

grub> **geometry (h[COLOR=Black]d[/COLOR]**[COLOR=Black]**0)**[/COLOR][COLOR=Black][/COLOR]

---

### Post by Zakhafr on 2008-08-08
Wonderful! :)

It works, booting from my Mandriva USB Key (using su instead of sudo... because that's how it works with Mandriva). I'll try that this evening from the Ubuntu CD.

Many thanks agains Logos34!

---

### Post by Zakhafr on 2008-08-08
Works fine in Ubuntu too, but booting from Live CD, it makes no difference wether I say in the BIOS Second Disk is first or not.

I still have hd0 equivalent to sda.

So I hope your diagnostic is correct, and thus, anyway I'll have to change Grub's guessing once installed as you wrote on your first post. As soon as I can make some room to move my huge files, I'll try.

---

