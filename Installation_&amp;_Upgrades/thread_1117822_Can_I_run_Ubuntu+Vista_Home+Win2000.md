---
title: "Can I run Ubuntu+Vista Home+Win2000?"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by walterius on 2009-04-06
If I can, how?

******************************
Here are some details:

I am a retired systems software person, and have used many OS's and computers. I have plenty of Windows experience (3.1 on up), but none with virtual machines. I am fairly familiar with Ubuntu. I am a Win2000 guru, if I may say so. :)

I have a new Dell Vostro 220 with Vista preinstalled. No Vista DVD; just the recovery DVD and partition. I am new to Vista, so I have ben on a learning curve.

I am presently running Vista Home Basic, with Ubuntu 8.10 running as a *program* under Vista. I hope to upgrade to the new Ubuntu this month. I consider my Vista/Ubuntu system a dual boot system.

I no longer run Win 2000 because I wanted to try just Vista. However, Vista can't install and/or run all my old programs, mostly gfx, (even after adjusting for administrator rights and compatibility) and I miss many of them, such as PSP6 and others.

Therefore I want to run a "*triple* boot system," so I can:

(a) Use Vista (and upgrade to Windows 7 if it is better).
(b) Continue to play with Ubuntu. (I mainly use the games, I admit.)
(c) Use my old pgms with Win2000, which runs them just fine.

Can I do this? And is there a better way?

I live on Social Security in govt-assisted housing, so I can't upgrade many/any old pgms. I am happy with my oldsters (I'm old too; I'll be 70 in less than 2 weeks) and I want to use the old pgms if possible.

Sincerely, and many thanks,

Walterius
Fort Lauderdale
:popcorn:

---

### Post by kiridude on 2009-04-06
I don't see why not. I run a triple boot of Windows XP, Redhat, and Ubuntu.

I would recommend partitioning your hardrive and installing one OS per partition rather than trying to run in Windows.

Or did I misunderstand and you want to run all three from one OS, in a virtual machine?

---

### Post by MysticGold04 on 2009-04-06
There is no problem doing a triple boot, but could get complicated setting it all up.  My vote would be to use VirtualBox (VM software) and run those OSes under Ubuntu.  Of course that would mean creating your Recovery DVD/CDs and then reformatting your hard disk, Installing Ubuntu, then install VB, then install your Guest OSes in VB.  

The reason I suggest this is that a triple boot of native OSes could be a potential nightmare to figure out if something goes wrong.  If something goes wrong with a VM, you just start over, and you wont have to spend time fixing your boot configurations.  This is just me.  

Running VB will require that you have a good amount of memory available to run both Ubuntu and VB/other OS at the same time.  I'd recommend at least 1GB of Ram or more.

---

### Post by Mark Phelps on 2009-04-06
> **walterius said:**
> I have a new Dell Vostro 220 with Vista preinstalled. No Vista DVD; just the recovery DVD and partition. 

This presents a problem as you are not going to be able to simply reinstall Vista as others may suggest.  The recovery DVD and partition will allow you to reload Vista as it came preinstalled -- but it will wipe the drive and partitions in the process.

> 
I am presently running Vista Home Basic, with Ubuntu 8.10 running as a *program* under Vista. I hope to upgrade to the new Ubuntu this month. I consider my Vista/Ubuntu system a dual boot system.

It's not a dual-boot system if you installed it inside Windows; it's running essentially in a virtual machine.  There are links that show how to "move" the Ubuntu installation to its own partition -- and then, it WOULD be a dual-boot system.

> 
I no longer run Win 2000 because I wanted to try just Vista. However, Vista can't install and/or run all my old programs, mostly gfx, (even after adjusting for administrator rights and compatibility) and I miss many of them, such as PSP6 and others.

You could install VMWare and run Win2K in a virtual machine inside Windows.  I think that Virtual PC 2007 might even be available for free, and it will do the same thing.

> 
Therefore I want to run a "*triple* boot system," so I can:

(a) Use Vista (and upgrade to Windows 7 if it is better).
(b) Continue to play with Ubuntu. (I mainly use the games, I admit.)
(c) Use my old pgms with Win2000, which runs them just fine.

Can I do this? And is there a better way?


Triple boot is going to be a lot of work, mainly because of the following:
1) you will want to preserve your existing Vista install (since a reinstall will wipe out everything you've done in Vista to date)
2) you will need to shrink Vista to make room for the other OSs.  Be sure to use the Vista Disk Management tool; don't use GParted or the Ubuntu installer to do this.
3) as a test, boot from the recovery DVD and see what options it provides you.  If there is a repair option, you're OK.  If there is no repair option, any problems that affect the Vista OS while you're doing this will likely force a complete reload of Vista to fix -- and then, losing everything you've done.
4) when you install Ubuntu, it should find Vista and add it to its boot menu. However, if you use the standard LiveCD, it will install GRUB to the MBR of your hard drive wiping out what Vista installed.  If you later remove Ubuntu, and your recovery DVD doesn't have a repair option, we're back to reloading Vista from scratch -- again!
5) if you're not careful (and this is not a personal slur, it's just that we get a LOT of reports of this) you run the risk of overwriting your Vista installation when installing Ubuntu -- simply by mistakenly choosing the "use entire disk" option.  If you have no backups, here we go with the reload (again).

Does that sound complicated? Yes ... because it is.  Is there risk of damage to Vista? Yes ... because there is.

Safest bet is to ask before you do anything specific.  We're here to provide advice as best we can.

Regarding Windows Seven, you will be able to upgrade from Vista when it comes out.  If all your applications and hardware are working OK in Vista now, the upgrade should not present any problems.  However, if you've built a multi-boot system in the meantime, that will probably mean some post-install corrections you will need to make to restore the multi-boot after the Seven upgrade.

---

### Post by upchucky on 2009-04-06
there is a win program called Bartpe that you can use to make your own customized win xp from an existing xp system. However I am not sure if Bartpe has been upgraded to handle Vista yet. you may want to check.

I used it to create a 150meg installed footprint of xp so it would run on an old 200mhz, 128m ram laptop. 

if you go the triple or dual boot method, you may also want to check into drive imaging programs, they make fixing windows easier when windows self destructs. 20 minute restore instead of all weekend reinstall.

---

### Post by miklcct on 2009-04-07
Divide your hard disk like below

```
Windows	Linux	FS		Purpose
C:	/dev/sda1	NTFS		Win2K
	/dev/sda2			extended
D:	/dev/sda5	NTFS		Vista
	/dev/sda6	EXT3		Ubuntu
	/dev/sda7	SWAP
E:	/dev/sda8	FAT32/NTFS	data

```
You must install Windows 2000 first, then install Vista **in** Windows 2000, finally install Ubuntu from CD.

---

### Post by walterius on 2009-04-07
I looked for BartPE for Vista. It does not (yet) exist. But thanks.

---

### Post by walterius on 2009-04-07
*Many* thanks to all who replied. I chose Sun VirtualBox because I want to learn Virtual Machines and it seemed a lot simpler than blowing everything away on the Dell and starting over, especially since I only have a recovery DVD, and not a Vista DVD.

Indeed it is simpler! I left Vista and its embedded Ubuntu 8.10 alone, installed Sun VB, created and installed a virtual Win2000, and am now learning the excellent Sun VB manual and setting up Win2000. So far, I have got the desktop set up the way I had it on the old Win2000.

Next I need to get the Internet and the DVD drives working. After that, I will install my beloved old gfx pgms. Presto: a three-OS system with little more work than simply installing Win2000 and setting it up.

I do need a bigger hard drive, though, I think. Mine is 64 GB with 10 GB free after virtual Win2000 install. I do have an external 68 GB HDD, which I plan to use as a backup/share between Vista and Win2000.

Thanks to all!

---

