---
title: "BOOT experts help"
date: 2004-11-29
forum: Hardware &amp; Laptops
---

### Post by tacubuntuforums on 2004-11-29
[FONT=Arial]I'm very sad I hadn't been able to install and try my recently downloaded **[COLOR=Sienna]Ubuntu[/COLOR] [COLOR=DarkRed]Linux[/COLOR] **.

I'll explain the circumstances in the hope that someone might help.

Does someone knows whether the following Bios fully supports interrupt 13 extensions and if that is relevant in order to continue using it with this Seagate hard disk device:

**-My BIOS:**
ROM PCI/ISA  TX97-E 
Award Modular Bios v4.51PG (c)1984-95
#401A0-0106e
(with LBA and Autodetect supports)

**-My HARD DISK:**
Seagate ST340810A
Cyl: 16,383,    Heads:16,    Sectors: 63,    LBA: 78,165,360
40 GB

**-My PC:**
intel PentiumII-MMX
97MB RAM

The point is that I don't believe that an upgrade is necessary (or maybe it is, in order to make things easier) because that same hardisk with that same BIOS was running a Windows2000 installation using the whole drive in a single partition.

My problem is that after a slight change in the BIOS CMOS geometry of the drive, there had been no way to turn back (undo the changes) and reboot the system from the same hard disk. Booting from a floppy with the basic boot files ("ntldr" converted to a *.bin, "ntdetect" and  "boot.ini") was possible but I couldn't fix the problem with any available tools.

Moreover, no reformatting, no repartitioning, no "fixmbr" or "fixboot" instructions, could help; no matter what is the single OS sistem I try to intall: Windows2000 or Linux,  no matter what geometry I use in the BIOS-CMOS Setup (the "autodetected" or the previous that was already working with Windows2000) and no matter what hints I find on the internet, the result is that I can't boot any new installation, even if it finishes without errors, and my hard disk is completely useless with that motherboard.

Some of the different error messages I'have been receiving, depending on which day of the battle, which installation and with what geometry I was trying to boot are:

[INDENT]- "Ntldr is missing" (the first message after the first change mentioned above).
- "Primary disk error".
- ntoskrl does not exist or it's corrupted (it was false! - but appeared when trying to start the recuperation console).
- "GRUB" (after Ubuntu Linux installation).
- sometimes no message at all.
- "1. No emulation system -Type(00)" just before booting from CD-ROM"
- something like "the automatic system recuperation  found an internal incoherence (A2210) and can't continue", when trying to repair a recen't installation on the clean drive.[/INDENT]

However, I believe the solution must be quite simple. I would appreciate very much your help to determine whether the BIOS supports interrupt 13 extensions and what would help solve this problem. I'm addressing to you after days of effort, search, trials,.. trying by all means to find the solution.

Thank you very much.

Regards from Barcelona.

Toni[/FONT]
e-mail: barcelona(at-nospam)mail(dot)com

---

### Post by Magneto on 2004-11-29
[QUOTE=tacubuntuforums][FONT=Arial]I'm very sad I hadn't been able to install and try my recently downloaded **[COLOR=Sienna]Ubuntu[/COLOR] [COLOR=DarkRed]Linux[/COLOR] **.

My problem is that after a slight change in the BIOS CMOS geometry of the drive, there had been no way to turn back (undo the changes) and reboot the system from the same hard disk. [/QUOTE]

What happened? What did you do? What changed on the system? The system booted win2000 fine until..........?

---

### Post by wallijonn on 2004-11-29
Are you using a Promise IDE controller card?

---

### Post by bob k on 2004-11-29
I would get hard disk tools from Seagate. I believe they have a boot floppy that you can down load and while I was at the site I would get the correct drive geometry, correct the bios, and do a low level format of the drive.

It is possible that when you changed the geometry you could have corrupted the sector information track.

These errors are windows errors

- "Ntldr is missing" (the first message after the first change mentioned above).
- "Primary disk error".
- ntoskrl does not exist or it's corrupted (it was false! - but appeared when trying to start the recuperation console).

---

### Post by Magneto on 2004-11-29
[QUOTE=bob k]

These errors are windows errors

- "Ntldr is missing" (the first message after the first change mentioned above).
- "Primary disk error".

- ntoskrl does not exist or it's corrupted (it was false! - but appeared when trying to start the recuperation console).[/QUOTE]
 those errors can usually be resolved with the repair function of the windows installation disk of the same operating system weird

I still don't understand what drove him to change the geometry and why manually changing the geometry hosed autodetect

flash the bios if nothing else works- youd probably be up already if you just flashed it

---

### Post by tacubuntuforums on 2004-11-29
Thanks to all:

**Magneto 1>** Everything worked finw with Windows2000. I received the PC (PC2) from my sister and started to "investigate" how things were, because that PC had had viruses, it had been slow, had changes, etc. I realized that according to the BIOS and to the "POST"information during boot-up the Hard disk was smaller than it was according to Windows2000. I just tried to change the values in the BIOS, to see what..... I Rebooted and it didn't boot. I think I booted from a windows95 diskette (at least at some time) and tried format and fdisk just to show information. When I changed to the original values of the Hard Disk specification in the BIOS:

Type:user
(Size: 2112)
Cyls: 1023
Head: 64
Precomp: 0
LandZ: 4094
Sector:63
Mode: LBA


while the 1st option of the Autodetect  values are:

Type: user
(Size: 8447)
Cyls: 1027
Head: 255 (how can it say 255 heads when the disk has 16?)
Precomp: 0
LandZ: 16382
Sector:63
Mode: LBA

I couldn't boot. At some time I set the values shown on the top side of th same Hard Disk..it didn't work. I tried several geometries...nothing, and so on...
ntldr and all those files were there. Later I used the same files that worked on the diskette to boot from the diskette to the hard drive. I copied those files to the Hard drive and tried with several geometries, etc....

**The story:**
Forgiveme, I can't remember the order in which all things happened. The battle has been long and tough because I don't have tools and I don't know much. One night in the middle of the struggle (the first time I managed to boot Windos2000 from the diskette) I installed but couldn't use the repair console because of the "ntoskernel-message". I went to see what was wrong and when I was exploring the system32 folder the w32/Blaster.F.worm appeared in the \system32\enbiei.exe file. Norton antivirus couldn't exterminate it so I tried to update it. I set-up the ppp-conection and when I was updating a message appeared saying that lsass.exe terminated unexpectedly and the the computer would shutdown in a minute.
I tried to rename the lsasrv.exe file but a copy appeared and appeared avery time I deleted the file so I try connecting and delete the file every5 seconds, it helped a bit but the time to do the update was very long, so I really failed.
That shutdown happened everytime I connected to the internet so I couldn't download. I tried with an old copy of Panda antivirus but nothing. At a certain point I went to MY COMPUTER (PC1) that served me to read things on the internet, to compare files, to copy files, etc. and guess what did I see? ...  there was the same lsass.exe message, and the computer shutted-down in front of my nose. That was the end, it my only and last resource. Hours later I had the idea to log in as a diferent user and it worked!! I was able to update both antiviruses which killed the fucking worm (oohps! it's forbidden to curse in here, I hope they don't kick me out) and another w32/Gaobot.BFA.worm they found in system32\TFTP1620
--

**wallijonn  >** how can I know that?

---- 
**bob k >** Thanks. I already went to Seagate and Asus webpages but its too much for me :-(  . But i'll do an extra effort I'll try again and see what . I already have the "real geometry" or the har disk specifications. I've read all sorts of things. Once I read that if you change the LBA mode you may be unable to use the hard drive again. Well ..why can't I start if I have reformated and repartitioned several times?
---
**Magneto 2>** Yes, but not in my case. At the begining I couldn't use the repair console (the installation CD didn't show that option) but in the end I made 4 diskettes tried them tried fixmbr, fixboot and nothing. Now, the repair console is the only way I can get into the drive. Not even with the win95 boot diskette (I don't have a Win3x nor MSDOS system/boot diskettes). There I have tried repartitioning, reformating, regeometring, reinstalling either Win200 or Ubuntu. Everything seems to go ok, but it just doesn't boot. 

One of those days, when the problem appeared I downloaded some files to update the bios but I'm afraid to spoil more everything and besides I've always thought maybe if I update the bios things work easier but I don't forget that Windows200 was already working properly, using th whole "large (for the bios time)" disk.


*I just want to learn to get rid of windows .... I want to install * [FONT=Verdana][COLOR=DarkOrange]**UBUNTU**[/COLOR][/FONT]  :sad:

---

### Post by tacubuntuforums on 2004-11-30
And what about [FONT=Verdana]**[COLOR=DarkOrange]UBUNTU[/COLOR]**[/FONT] ?

Do you have any idea how can it be possible that I follow the whole installation process with no errors (except a few quick messages at the very begining that say fatal error which pass very fast and I'm unable to read) and when it reboots to start, the  message  which says "GRUB" appears at the very beginning and the bootup stops.

---

### Post by tacubuntuforums on 2004-11-30
Among my tools, I forgot to tell that I've got a new Knoppix CD. Does anyone know if it can help?

**bob k > ** I don't know exactly what would or would not be a low level format of the entire disk and if it erases everything: bootsectors, mbrs etc .
I've executed the format insrtruction in the "repair console" (or command-console that's my translation of its name in spanish) which i executed from the instalation CD after repartitioning to a single partition.  I have also asked for a format  of the single partition as a step during the installation process while running the same installation CD.
In any of the two ubuntu installations I've done I received any mesage saying that there was another system or if I wanted to mantain anything.

---

### Post by Magneto on 2004-11-30
ok now I see-  some BIOSes only see a drive as being a certain size but it doesn't restrict the operating system being used from utilizing the whole drive, which is why the bios would state the drive was one size while WIN2000 saw the accurate size.  This is very common with older BIOSes. I have one older system with a 15gb disk that is seen as 8gb because of the geometry.

The main problem here is your bios.  It does not see your drive too accurately at all anymore and you cannot boot. It can't see the mbr it seems.
I'd suggest getting some floppies and following the EXACT procedure for flashing your BIOS to the same version it is currently running or a newer one- or any version if you cannot find one current or newer.
Flashing the bios will erase whatever configuration errors are present.  

Did you try resetting the BIOS to its default configuration?  There should be a reset to defaults option somewhere in the BIOS Setup.

---

### Post by tacubuntuforums on 2004-11-30
[QUOTE=Magneto]ok now I see-  some BIOSes only see a drive as being a certain size but it doesn't restrict the operating system being used from utilizing the whole drive, which is why the bios would state the drive was one size while WIN2000 saw the accurate size.  This is very common with older BIOSes. I have one older system with a 15gb disk that is seen as 8gb because of the geometry.

The main problem here is your bios.  It does not see your drive too accurately at all anymore and you cannot boot. It can't see the mbr it seems.
I'd suggest getting some floppies and following the EXACT procedure for flashing your BIOS to the same version it is currently running or a newer one- or any version if you cannot find one current or newer.
Flashing the bios will erase whatever configuration errors are present.  

Did you try resetting the BIOS to its default configuration?  There should be a reset to defaults option somewhere in the BIOS Setup.[/QUOTE]

Yes, there's a reset, but I was afraid of using it and I don't know how to save the values.
How come you say it could help to flash to the same version of BIOS (that amounts to reset the values only?)
I'm looking in the internet what to do about the BIOS... there are some places that sell them, but it scares me a bit and without phone service, even more.
I didn't want to go this path from the begining of the problem, because don't forget that the BIOS is not so old: it has LBA support and, although I think it works under a  8GB limit or so, it was working ok before I spoiled the whole thing. Therefore, I think, if it was working ok and it consists on HW and ROM why can't it work anymore. What happened?

---

### Post by Magneto on 2004-11-30
[QUOTE=tacubuntuforums]Yes, there's a reset, but I was afraid of using it and I don't know how to save the values.
How come you say it could help to flash to the same version of BIOS (that amounts to reset the values only?)
I'm looking in the internet what to do about the BIOS... there are some places that sell them, but it scares me a bit and without phone service, even more.
I didn't want to go this path at the begining of the problem, because don't forget that the BIOS is not that old: it has LBA support and, although I think its limit is (GB or so, it was working ok. Therefore I think, if it was working ok and it's HW and ROM why can't it work anymore. What happened?[/QUOTE]
 USE THE BIOS RESET!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
You don't need to save the values- what are you trying to save? boot device order? memory allocation? whatever it is - go to each page and write down each setting you customized- if you did not customize anything besides that drive config dont worry about it

THE BIOS WILL BE FINE on reset and your problems most likely gone

DONT BUY ANY BIOS
the bios program is free- you can get it from the motherboard manufacturer but you probably do not need it. What you need to do is reset the bios to default so that the mistaken info you put in is erased and your system can boot again upon finding the drive's mbr

The problem is 100% within the bios. You changed the settings mistakenly. A reset of the bios to defaults should solve this problem unless your BIOS is screwed up. If your BIOS is screwed up the next step is flashing it.
But right now reset the bios to default configuration please.  This won't harm a normally functioning bios.

---

### Post by tacubuntuforums on 2004-12-01
[QUOTE=Magneto]USE THE BIOS RESET!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
You don't need to save the values- ......[more].[/QUOTE]
Thanks, you make me feel more secure.

I'll try , what you suggest.
Having to buy the bios is what disappointed me yesterday. I was looking for upgrades and the only shure way I found was in

[http://www.esupport.com/global/why.cfm](http://www.esupport.com/global/why.cfm)

but too many things to make it too expensive. I'm not trying to be the expert nr. 1 in BIOSes and receive a BIOS-newspaper and all that!!.

Going to the manufacturer, here in Barcelona, same thing. In bBarcelona nobody moves a finger if it's not to charge you a lot. (An idea: When internet connections started it was 6 times more expensive here than in Mexico, not to mention the US)

I'll anounce here when I'm over, which I hope is before the conference that's going to be held in Mataró. Still not shure if I'll go someday but if anybody that is coming needs help, just let me know.

---

### Post by tacubuntuforums on 2004-12-01
[QUOTE=Magneto]USE THE BIOS RESET!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
You don't need to save the....[[COLOR=DarkRed][more][/COLOR]](http://www.ubuntuforums.org/showpost.php?p=26289&postcount=11) .[/QUOTE]

Before I spoil it more, just let me tell you I'm puzzled again:

I forgot that this BIOS, as seems to be usual, has these options which i don't understand:   :confused: 

[B]- Load BIOS defaults (except standard CMOS setup) 
- Load Setup defaults (except standard CMOS setup) [/B] 

Don't tell me this is not done on purpose to puzzle us...  If I load the the BIOS defaults, new values will replace the values that I can actually SEE on my screen and then change right (or wrong?) so those are values that I set up and belong to the Setup values. So what do I load when I load Setup defaults?. I mean which is which and which does what?

**Magneto >** Do you have any clue as to how should I try these changes: which option first, which second,  both at the same time or it doesn't matter: trial and error?

and then what?:

a) fixmbr +> fixboot +> partition +>format +> install
b) partition +> format +> install
c) format +> fixmbr +> fixboot +> install
d) just install and follow instructions.
e) other

not knowing the order in which i should try things has driven me crazy and all the literature I pick is obscure.

---

### Post by Magneto on 2004-12-01
Load BIOS defaults

and then install - no need to fix mbr - just install

if you want dual boot with windows  then install windows first then install ubuntu

if you only want ubuntu just pop the disk in- when the OS install installs grub it will write to the mbr

your mbr was never damaged your drive was never messed up - it was your tinkering with the geometry in the bios that screwed everything up-  the reset function is there for a reason :)

Your BIOS will automatically deal with the hardware it finds and if it cant deal with some issue it will ask you about it-

---

### Post by tacubuntuforums on 2004-12-02
:mrgreen: 
Something's changing and is changing right now. Ain't got time to wait .....

---

### Post by Magneto on 2004-12-02
[QUOTE=tacubuntuforums]:mrgreen: 
Something's changing and is changing right now. Ain't got time to wait .....[/QUOTE]
 does that mean youre up?

---

### Post by bob k on 2004-12-02
bob k > Thanks. I already went to Seagate and Asus webpages but its too much for me . But i'll do an extra effort I'll try again and see what . I already have the "real geometry" or the har disk specifications. I've read all sorts of things. Once I read that if you change the LBA mode you may be unable to use the hard drive again. Well ..why can't I start if I have reformatted and repartitioned several times?

==================================

The reason I'm telling you to get the low level disk utilities is that you might be able to repair the damage already done. There is a track on the disk that nobody can access but the controller, which maps every sector and the physical disk address based on the disk geometry supplied to the controller. If this mapping gets trashed and the low level utils cannot correct it the disk is dead.

EDIT

I had a TX97-XE and ran into some of the problems that you are having, but I thought that was an AMD board and  not an Intel, anyway the bios showed one size and the OS showed another size. I think you can still get the last bios for that board. (I guess we are talking 98/99). But I will say one thing about that board, you would have take a sledge hammer to it to break it.

Bob

---

### Post by tacubuntuforums on 2004-12-02
**ALMOST !!!!**

 #-o 


**bob k>**  That's what I've thought several times, that there was something in the disk I couldn't access and that maybe changing the settings of the bios made it impossible to touch those values...but I don't know. I would like to have tools like that whith which you can know at least, for example, if you have erased all data, or deleted the mbr or whatever. However, asking Seagate if my BIOS Bios supports interrupt 13 extensions and if that could be the problem with my disk they answered almos nothing.

**Magneto> ** Thanks. One step forward. 
I wrote *"Something is changing ..."  * when Windows2000 was being installed in it's second phase or step: Until now, instead of passing to the configuration's second after the first phase of the installation process it rebooted to the same phase (the CD boots in a different way each time: first parameters and install then more install and configure) in an infinite loop of installation and rebooting.

I would have loved to do my next post (this one) from [COLOR=DarkOrange]**[FONT=Verdana]ubuntu[/FONT] **[/COLOR], but it failed.

First of all an update of my adventures:
As **Magneto** suggested:
- I loaded the 'BIOS default' values, rebooted, ... nothing (the first phase was already done)
- I used autedetect, rebooted,... nothign.
- I reinstalled, rebooted,...nothing.
- I loaded the 'SETUP default' values, rebooted, ... nothing.
- I used autedetect, rebooted,... nothing.
- I reinstalled, rebooted,...nothing.
- I partitioned to make shorter th process. Half disk for Windows.
- I reinstalled everything (reformat, repartition), rebooted,...nothing.
- I changed the eometry again to the original values (when I received the PC working ok),....nothing.

Meanwhile I was contacting Asus in Spain. I got from them the update kit for the BIOS. I was reading the instructions, but tired ... went back to the computer

I changed the geometry values several times using LBA (since I've read everywhere  that you should use "LBA mode", especially with this kind of problems) but nothing!. With "LBA mode" the boot  process has always (or almost, I can't remember) stopped in an earlyier stage (error: Primary disk error or cold stop) than with "normal" or "large" modes (error: NTLDR is missing)
- I used the values which allowed me not to boot from the same HD but, at least, to boot from a windows2000 boot dikette (other values didn't let me even that) for the first time, rebooted,.... and voila!...the second phase started. I finished ok. The hard disk booted by its own bootstraps!

The solution came from  a combination of loading the default values, as Magneto suggested, and replacing the *autodetected* values for the HDD for ones that didn'r work before, but worked better than others.


I started to install [COLOR=DarkOrange]**ubuntus**:[/COLOR]

 :-k 
First problem:
-Should I use the parameter that allows me specify the geometry of the HD in the installation command (at the very begining)?
-Should I use expert mode to solve any prob. with the disk? (Remeber that it seems to me that the BIOS (year 1997) has a 8GB limit)

Since there's no information whatsoever in the boot program, I executed the default installation and established the partitions in the following way:

```
IDEmaster (hda) 40 GB:
#1  primary  16.7 GB NTFS
#2  primary  31.9 MB  ext3(*)   /boot
#5  logical  500  MB  swap      swap
#6  logical  9.9  GB  ext3(*)   /
#3  primary  12.7 GB  ext3(*)   /home

with boot marked as active or bootable.
where (*)= ext3 journalling system
mount options=default, in all of them
```
Don't ask me why I chose primary or logical. no clue!
Don't ask me why that type of file system. no clue!
same goes to mount options.
(Any improvement or suggestion to change these is welcomed)

Everything went fine and at the end of the installation I'm asked if I want to install grub in the MBR to be able to do a dual boot or not. I was going to say no (more conservative), and try to do it by myself in windows boot (I've learned these days a bit how it goes), but the message was so convincing that I consented. It rebooooots and....

..I read:

```
Grub Loading stage 1.5
GRUB loading, please wait ...
Error 17
```
Now windows2000 needs the boot-diskette again to be able too boot and it 'sees' nothing from the other partitions, not even that they exist.

I'm looking 4 information on this. But it seems to happen in many different cases and people solve it in ways i can't understand. In my opinion it's again the bios, I think the problem is that the /boot partition is too far for the BIOS. 

So what do you think about the following possible solutions (that I hope I can handle)

 :confused: 
- Place /boot at the beginning
- reinstall ubuntus with the parameter that specifies the geometry
(which geometry to use: the real?)
- Reinstall ubuntus and don't choose the 'replace the MBR 'option at the end +Try to fix the MBR so that windows2000 boots again and change the boot.ini to be able to choose which system to boot from (how do I do both things??? is it possible?)
- Boot with knoppix and fix things in ubuntus?? (no idea??)
- Give up

---

### Post by Magneto on 2004-12-02
man you are nuts

your bios is and was fine- you messed it up with your settings- you fixed it by resetting it- win2000 booted from the hard drive after you installed it properly

windows2000 will only boot from the diskette because grub is not installed right


The main source of all your problems is you.  You are trying to apply added levels of detail to configuration of your system without knowledge of how your system works. There is nothing wrong with fine-tuning your system, but if you try this without knowing the implications of your actions this thread results.

You are fixated on dealing with the specifics of your disk's geometry without knowing how the disk is used by your system.  Every problem youve had has been selfinduced.  Your grub error is in posts all over this forum like you've seen but you refuse to read up on why and how these things are going on.

Dont give up- just read.  It is very frustrating to see you doing this. Please calm down and READ about grub, learn how it works and you will understand that it simply needs to be installed correctly.  

GOOGLE.COM

THERE IS NOTHING WRONG WITH YOUR BIOS - /boot is fine -  grub resides in the MBR  and knows where the /boot partition resides if it is setup right - it also will know where your win2000 partition is if it is setup right
cmon man you're obviously a bright individual  please read, either read or stop messing with settings you don't understand because the result is a screwed up system.  I'm not trying to be negative and I apologize if this comes off that way.

---

### Post by tacubuntuforums on 2004-12-02
[QUOTE=Magneto]man you are nuts
your bios is and was fine- you messed it up with your settings- you fixed it by resetting it- win2000 booted from the hard drive after you installed it properly
.... and thousands more ...[/QUOTE]

I appreciate very much your help, Magneto, Thanks again. You're right I should have loaded the default values from the very begining a week ago. I thought about doing that, but without knowing how the bios works and if there could be other values than those displayed, flashed at some time, or whatever..., I was afraid of touching it (just aplying the principle of prudence)

and I still don't understand how it works, because the loaded default values are exactly the same than the ones I wrote down before the reset. What changed? ... who knows?...

About what happened after, ....what can I tell you. That's exactly what happened:
The loaded default values for the BIOS  didn't work with the values for the CMOS loaded by autodetection and  I also had to change those values for a set of values without LBA mode, very different from the ones that were present before I touched anything. But this last values didn't work before the loading of the default values that you kindly suggested me to do.

and...well, about my ideas about linking Grub's error 17 with th BIOS, its limit and its upgrades may be 'cause I'm nuts, but I think that this prob. drives many people nuts. and one reads all sorts of things out there... Searching "grub error 17" in google.com I read:

> "When a system has multiple HDDs the /boot partition has to be on the first hard disk that BIOS boots from and preferebly on the first 1024 cylinder (~8.5GB area) some system BIOS cannot reach any further"
--
"Stupid, stupid me. A collegue of mine suggested updating the bios. Voila! now it works  

But along the way I had a little adventure- I suspected that the mbr was messed up, and that grub was installed incorrectly, so I did a Code: 
dd if=/dev/zero of=/dev/hda count=1 bs=512 
to erase the mbr. 

What I didnt think about was that this would clear the partition table as well. *woe*. So there I was, with no partition table, and apparently no hope. 

But then the same collegue who suggested updating bios found an application called gpart ([http://www.stud.uni-hannover.de/user/76201/gpart/](http://www.stud.uni-hannover.de/user/76201/gpart/)), which tries to recover lost partition tables by reading the drive. And wonder of wonders, it worked  

so now my system is up and running again, hurray!"
--
in ubuntuforums (there's a thread dedicated to this problem):

<<Re: GRUB Error 17 - me too.
You may need to go into your BIOS and set the disk type to LBA (take it off AUTO. Windows, I believe, defaults to CHS even though it says "AUTO").>>
--
<<Why is there a "linear" option? That is used usually for SCSI. I would just remove that line. After some research I think even the newer distros have problem booting from the 1024 cylinder, but I swear I saw in a forum somewhere that said they had fixed that in newer versions of LILO. The 1024 cylinder is usually past the 2GB mark on a drive so if "hda3" is within that space it shouldn't be a problem>>
--
there's also a confusing thread at:
[http://ubuntuforums.org/showpost.php?p=8933&postcount=1](http://ubuntuforums.org/showpost.php?p=8933&postcount=1)
The questions always ask 4 an explanation not only a solution. The package is always solution+explanations, one thing is nothing without the other one.
--
After reading in the web all sorts of solutions to all sorts of similar problems to this, I have 100 different explanations of what happens, 100 ways how to fix it, 20 must be wrong, 20 are incomprehensible, 30 don't apply at all and 20 might not apply enough, and a few could cause a disaster to think is right. The problem is which is which


It wouldn't surprise me much to see that after my installation I  needed to configure GRUB in order to configure correctly a dual boot or if I hadn't installed grub in the MBR, to need to configure after the win200 loader to be able to boot [COLOR=DarkOrange]**ubuntu**[/COLOR] . But what surprises me is that having installed grub in the mbr, having received a message that everyhting will be ok, not even [COLOR=DarkOrange]**ubuntu**[/COLOR] boots. Besides the process didn't ask me if I wanted a boot diskette, which i do.

Now, if i'm right,  the solution must be:
Replace the MBR (i hope it works what I think), install (grub in hda2, the /boot partition) if it's not thre (how? reinstall over?)  rewrite the boot.ini of win2000 so that an option points to a file with the boot sector of [COLOR=DarkOrange]**ubuntu**[/COLOR]. But for this file I need to boot Linux . Do this without diskette (because the installation didn't geve me one)
But if I want to boot from grub?

Of course I'll get out of this some day, i was joking when I suggested as a solution to give up. I'll solve the problem, but naturally I don't want bother much during a couple of weeks more. My main interests are not in HW,  tough systems administration, and the like.

---

### Post by tacubuntuforums on 2004-12-05
I' ve made a copy of the following files of my **[COLOR=DarkOrange]UBUNTU[/COLOR]** installation ....

```
[COLOR=DarkOrange]**/boot = hda2:**[/COLOR]
      config-2.6.8.1-3-386
      System.map-2.6.8.1-3-386
      menu.lst

<?don't remember>/device.map

[COLOR=DarkOrange]**/ = hda6:**[/COLOR]
      /etc/fstab
      /etc/mtab
     [COLOR=DarkOrange]/var/log/debian-installer/[/COLOR]
             hardware-summary
             messages
             package-versions
             partman
             syslog
             hardware-summary
             messages
             package-versions
             partman
             syslog
             [COLOR=DarkOrange]cdebconf/[/COLOR]
                    questions.dat

**The output of the following commands**:
     [FONT=Courier New] lspci
      lspci-n[/FONT]
```

I Attach here the entire [***[I]/var/debian-installer/syslog***[/I]](http://ubuntuforums.org/attachment.php?attachmentid=149)   file zipped.

which seems to be the only one with relevant info. And show some "syslog.errors"

I would like to know if someone sees if there's something not correct in here or knows how to see if something is not correct in the files i've go or if everything is ok and there's only a problem at the MBR level.

[SIZE=2][B][COLOR=DarkRed]Then my questions are:
How to know what's the problem?
Why happened that?
How to fix it?[/COLOR][/B][/SIZE] [SIZE=1](Obiously accompained with a little bit of explanations, because every day more thn one is ruined by following blindly some instruccions that were either wrong or were not 100% adequate in his case because he didn't undertood exactly what was the case for those steps or the other person didn't  understood exactly if the problem was the same situation, or maybe he learned from a place where they describes a slightly different situation, etc. ..........[/SIZE]
Thankx a lot.

_____________________________________
[SIZE=1]*People and OS's form operating systems and a good operating sistem is that with a good information system about the OS and about itself*[/SIZE]

---

### Post by tacubuntuforums on 2004-12-08
According to GNU's GRUB manual, **error 17** means:
> Cannot mount selected partition 
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB

Ok. But which partition was selected or which file system type can't be recognized?

I have already posted the partitions I made durinfgi the nstallation process

---

### Post by p!=f on 2004-12-08
As said by Magneto you lack essential knowledge of computers. Playing with BIOS and hardware like you do always ends with problems. Play with fire and you get burned. :)
To be on your place I would reset the BIOS by the jumper. 
Install both systems and don't touch anything until you **R**ead **T**he **F**riendly **M**anuals and get some point what you want to do, what it is good for and how to do it without breaking your current working setup.

Btw, your root partition is set up as logical. No good.

---

### Post by TravisNewman on 2004-12-08
OK this is what I suggest you do...

fdisk /mbr or fixmbr, whatever is available to you. Wipe out everything on the drive. Leave the BIOS at its defaults.
Install Windows 2000. Be sure to save room for Ubuntu
Install Ubuntu. Tell Ubuntu to automatically partition the remaining free space.
Yes, install Grub.

Don't try to do anything crazy.

The last part of this is for p!=f, you can ignore it:
My root partition is set up as logical and it works fine. I don't think it matters as long as there's a separate boot partition that's primary.

---

### Post by tacubuntuforums on 2004-12-08
**Thank you 1!=2**.

1. As Magneto does lately, you mostly (90%) criticize me.  Doing this without answering any questions or focusing in other ways of approaching the situation, doesn't help to solve my problem.
2. Why can't my root partition be "logical"? My root partition is as any other partition as regards the booting procedure, isn't it?. My root partition is not a boot partition. Besides, if the root partition couldn't be logical, then the installation program would be wrong by accepting what it obviouly won't work. Are you suggesting that? Why don't you tell say clearly that there's a bug in the installation process which I should be carefull with?
3. The **Friendly Manuals ** don't talk about my problem (as far as I've read) or maybe they do, but there's no way to know (whether they do) from the info within them. If you think I'm wrong, please tell which one does?
4. If you read what i've posted recently, you'll see that the only thing that you suggest is exactly what I did:
   (a) reset the BIOS
   (b) stop touching (or, if you like it, "playing with") the bios anymore
   (b) Install both systems.  (First win2000 which booted ok, then Ubuntus)
   (c) ReBoot and write down the boot error prompted by grub.
   (c) Since then, I haven't touched anything else, but try to find which are the _essential_ **Friendly Manuals**, especially for my case and try to get in touch with experts that might help me understand what's wrong or why I'm wrong?. To solve this problem and/or learn I don't need people to remind me that there's people that know more about computers than me.

Ok, thank you again. But is there anyone else who knows which filesystem might not be recognized by GRUB? or, if this is not relevant, what extra info might be relevant or needed to understand what happens, why and how to fix it?

**panickedthumb>**
After formatting the whole disk and leaving the BIOS to it's defaults, I installed Win2000, exactly as you suggest and as I described. Moreover, if you understand my case, you'll understand that there was pretty enough room for Ubuntu and much more. I asked the ubuntu installation prog. to partition the remaining free space, but I didn't like the partitions suggested. Besides I'd like to have a separate boot partition as suggested in the **Friendly Manuals**. Is it possible?
After the partitioning, Ubuntu will _suggest me_ to install grub in the MBR and _ASK ME_ if I want to do it. If answering "yes", as I did and as I think you suggest, can't be the cause of my problem, as implied in your answer, then the only thing I did wrong should be within the partitioning...

Where exactly?
what _exactly_ you insinuate is crazy about what I did?
what partitioning that distributes the SPACE as implied in the one I posted, you suggest?.

--
Finally I want to thank you all, I'm sure you are trying to help, but a different thing is to achieve it. 

(a)I might be completely wrong, but I think that the answer to any of these questions could be much shorter than any of your answers while it would help  solve the only problem in my installation that you are pointing out here.

(b) I might know "nothing" about computers as I have already stated, but I know about many other things and since I'm a mathematician, I know very much about logical reasoning, about what is a precise statement and about what is a precise and complete answer to a question.

(c) Why should I ignore panickedthumb's  last remark? ... A matter to be meditated.

---

### Post by Magneto on 2004-12-08
[QUOTE=tacubuntuforums]**Thank you 1!=2**.

1. As Magneto does, you mostly (99%) criticize me.  Doing this without answering any questions or focusing in other ways of approaching the situation, doesn't help to solve my problem.[/QUOTE]

I tried to help for awhile but you refuse to learn about what you are doing, that isn't my fault. I told you PRECISELY how to fix your pc, but you don't understand because you don't want to learn what you are doing.

You make me not want to help people in all honesty. Logic seems to allude you IMO. I find it totally illogical for a mathematician to not study for 5 minutes the rudimentary innerworkings of a non-complex system in order to get the disired result from said non-complex system.  You are not devoting the same brain power toward this problem as you would a mathematical formula. Or you are a poor mathemetician.

---

### Post by tacubuntuforums on 2004-12-08
[QUOTE=Magneto]I tried to help for awhile but you refuse to learn about what you are doing, that isn't my fault. I told you PRECISELY how to fix your pc, but you don't understand because you don't want to learn what you are doing.

You make me not want to help people in all honesty.[/QUOTE]

I'm sorry to tell you Magneto, but after your suggestion to reset the BIOS, I reset it as soon as I could, reported the result to you and thanked you. From there on, you have _ONLY_ suggested me, like a teacher,  to read, read and search in google and other forums ..and that's PRECISELY what I've been doing, as much as I can.  Leaving other things behind, that's the truth.
Please don't take me wrong just because I tell you clearly how you have helped me as well as how/why I feel you aren't helping much. Let's be mature.

Of course that reading and searching will help me, It's s a very good way to learn, but it's not always the fastest way to learn to avoid and to solve probs.. Besidees, everybody knows how much effort/time they want to spend in any matter relative to computers as well as in any of the infinite there are in this universe. I'm just not interested in knowing everything about installations. I think it's easy to understand.

And now it's me who would tell you, read, read your postings and tell me what is that I don't want to learn, what is that you say and I don't pay attention to, what have you suggested, what question have yopu answered me...honestly.
Searching out there, I found a girl in Malasia who answered so well and clarly (more than any post I've found till know) to someone with a problem similar to mine, that I wrote her directly... She kindly answered me that she will help me as soon as she finishes with her project which will take her a few days. Meanwhile I continue reading, whenever I can here and there, believe me...

---

### Post by Magneto on 2004-12-08
[QUOTE=tacubuntuforums]I'm sorry to tell you Magneto, but after your suggestion to reset the BIOS, which I did, you have _ONLY_ suggested me, like a teacher,  to read, read and search in google ..and that's PRECISELY what I've been doing, as much as I can. Leaving other things behind, that's the truth.[/QUOTE]
 good luck man

---

### Post by tacubuntuforums on 2004-12-08
[QUOTE=Magneto]good luck man[/QUOTE]
We all react emotionally towards things/situations/people. Emotion is behind all reactions. Even logical reason has an emotional background, but we should try to see how they guide us and try to be able to read what we say and others say clearly and fairly in order to buils a better home/world and in order to learn to help others, thing  that will help us in turn.


**[SIZE=1]Don't let _the real_ ubuntu spirit abandon you. Build love, not war.[/SIZE]**

---

### Post by TravisNewman on 2004-12-08
I wasn't saying anything you were specifically doing was crazy, just saying not to do anything fancy basically, just do it as defaults. Honestly I have no clue what the heck is going on. The grub error seems to say that it can't find the partition, that was why I suggested you wipe the mbr.

Have you tried installing everything with the same drive in another pc?
Have you tried installing everything with the same pc but a different drive?

---

### Post by tacubuntuforums on 2004-12-08
[QUOTE=panickedthumb]I wasn't saying anything you were specifically doing was crazy, just saying not to do anything fancy basically, just do it as defaults. ...QUOTE]


No I haven't
Why these questions?.

I've been critizied in a way that insinuated that I was obviously doing something wrong, that I don't understand what I'm doing and i don't want to learn, nor understand. How can that be true? Just take a look to the whole thread and if you want read it thoroughly.
I'm asking questions and nobody anwsers me. I'm asking questions not only about things that you might not know or that you can't guess from far away, but I'm asking questions about what you tell me, about where would you start from if it's really so easy and obious as you are stating.
OK, you have just answered me something, but obviously I don't want to repeat what i've just done and seems to have been done without problem.

I have asked in this thread if you think my partitions are right...just take a look to the answers...no way to progress. I might know nothing about computers, so what...what are the answers.

OK, my answer to your questions, both, is NO for these reasons: 

1. I've heared that often installations on one PC sometimes can't  be taken to another PC. In my case (I might be wrong to consider this, but I can't operate without having certain prejudices when I don't know what's going on and what's the real prob.) the PC where I want to install ubuntu has a rather old BIOS (**1995**, which _seems_ to have a 8GB limit) and the other one is quite new.

2. I haven't tried the same PC with another HD because if it works it will only prove me that the ubuntu installation can go right is some cases, something I'm already completely shure it does in most cases. Besides, this installation won't help me for nothing else, because I don't want it in that drive. I would delet it.

3. Magneto suggested that everything seemed to be ok (at least that's what I understood). That the only problem was me and that what was needed was to read and learn how to retouch things.

Now if experts really think I should try first of all the point nr 1 before touching or configureing anything in the PC where I've installed win2000 and ubuntu and where NOW (after ubuntu) neither boots, then I would try it.
I would try it. If it works I'll be happy, on one hand, but on the other, I would not learn/understand what was going wrong.
Now, obviously, after having been criticized so hardly about doing things so badly and spoiling the installation of ubuntu, I'd like to know (to receive concrete answers about) which things I've done so badly before trying this, in orther not to repeat them.
As I said before, I'd like to distribute the space as I had posted, not as ubuntu does by default. What is the problem? what are the dangers? are my filesystems ok?
Receving answers to these questions by people to whom these are trivial, really helps me to start seeing things clarly, otherwise is to remain exactly in the same way.

Finally, .....I would really appreciate your help, i think you know it and i'll make you know much more when i'm through. I have always thanked your answers, but if I talk like this is because I try to be extremely clear for the only reason that it seems to me that the lack of correspondence between questions and answers is making this thread much longer than needed. It seems what, in my language we call "a deaf's dialogue" and that does not interest me at all.

---

### Post by bob k on 2004-12-08
Read the three book set " THE ART OF PROGRAMMING" by KNUTH. I think he will talk your language, as a large part of Unix/Linux design is based off of his principals.

---

### Post by Magneto on 2004-12-08
[QUOTE=panickedthumb]I wasn't saying anything you were specifically doing was crazy, just saying not to do anything fancy basically, just do it as defaults. Honestly I have no clue what the heck is going on. The grub error seems to say that it can't find the partition, that was why I suggested you wipe the mbr.

Have you tried installing everything with the same drive in another pc?
Have you tried installing everything with the same pc but a different drive?[/QUOTE]
 Panicked - he tried to input the precise drive geometry into his bios because he believed it to be inaccurate based on the BIOS's display, even though everything was completely operational.  He could not change the drive detection back to auto and restore the prior working condition.  He never reset the bios at the point of his initial posts.  He finally reset the BIOS but during his many attempts at installing different operating systems to fix his BIOS problem he altered his mbr.  He now seems to be in need of accurately installing grub with the right partition information.  

He needs to run grub setup now.  His issue now is grub error 17 - and there are many threads addressing fixing grub in regard to mbr and dual boot systems 

[http://ubuntuforums.org/showthread.php?t=6132&highlight=grub+setup](http://ubuntuforums.org/showthread.php?t=6132&highlight=grub+setup)

[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-natively.html)



> Then my questions are:
How to know what's the problem?
**I dont know all the precise things youve done, but at some point during your continuous installations of windows and ubuntu while trying to fix your problem you hosed the MBR**

Why happened that?
**Any number of reasons, its hard to tell with all that your PC has been through now**

How to fix it? (Obiously accompained with a little bit of explanations, because every day more thn one is ruined by following blindly some instruccions that were either wrong or were not 100% adequate in his case because he didn't undertood exactly what was the case for those steps or the other person didn't understood exactly if the problem was the same situation, or maybe he learned from a place where they describes a slightly different situation, etc. ..........
Thankx a lot.
[B]To fix it-  you need to install grub manually- the Ubuntu grub installation does not seem to be working for you. Here is the grub documentation regarding that precise operation.
[http://orgs.man.ac.uk/documentation/grub/grub_3.html](http://orgs.man.ac.uk/documentation/grub/grub_3.html)

15. I installed GRUB, but it just hangs up.
[http://www.gnu.org/software/grub/grub-faq.html#TOCq15](http://www.gnu.org/software/grub/grub-faq.html#TOCq15)

[http://www.linuxgazette.com/issue64/kohli.html](http://www.linuxgazette.com/issue64/kohli.html)

I would suggest creating a grub boot disk and running setup from it. That suggestion is also mentioned by the creators of grub. The exact instructions on how to do that are above.  You need to know the layout of your partitions on your hard drive to set this up. 
/dev/hda1 is equal to hd0,0 in grub
/dev/hda2 is equal to hd0,1
/dev/hdd4 = hd3,3

Other people have had issues with grub and dual booting but I dont know if that is your issue since the other circumstances here are substantial. [/B]

---

### Post by p!=f on 2004-12-09
[QUOTE=panickedthumb]
The last part of this is for p!=f, you can ignore it:
My root partition is set up as logical and it works fine. I don't think it matters as long as there's a separate boot partition that's primary.[/QUOTE]
Do you have dual boot setup?
I had my root partition as logical and had bad times with GRUB then. It refused to boot Linux (Debian Sid by that time). And yes, I had (still have) /boot as a separate primary partition.
I'm sure it would not matter if you have all disk space dedicated for Linux.

---

### Post by p!=f on 2004-12-09
[QUOTE=tacubuntuforums]**Thank you 1!=2**.

1. As Magneto does lately, you mostly (90%) criticize me.  Doing this without answering any questions or focusing in other ways of approaching the situation, doesn't help to solve my problem.
[/quote]
I can see most of your questions answered. 
[QUOTE=tacubuntuforums]
2. Why can't my root partition be "logical"? My root partition is as any other partition as regards the booting procedure, isn't it?. My root partition is not a boot partition. Besides, if the root partition couldn't be logical, then the installation program would be wrong by accepting what it obviouly won't work. Are you suggesting that? Why don't you tell say clearly that there's a bug in the installation process which I should be carefull with?
[/quote]
My bad. I forgot to add I had problems with dual booting when root partition was setup as logical even with boot one as primary. 
What partitions have boot flag?
[QUOTE=tacubuntuforums]
4. If you read what i've posted recently, you'll see that the only thing that you suggest is exactly what I did:
   (a) reset the BIOS
[/quote]
How? By entering the BIOS and selecting "Load BIOS defaults" or by the jumper on the motherboard? See? Describing the steps exactly would help.
[QUOTE=tacubuntuforums]
Ok, thank you again. But is there anyone else who knows which filesystem might not be recognized by GRUB? or, if this is not relevant, what extra info might be relevant or needed to understand what happens, why and how to fix it?
[/quote]
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

If you don't want give up I would suggest to try to set up root partition as primary. It solved my problem but the result can differ in your case.
Also, trying to replace GRUB with LILO could help but I have no clue how to replace bootloader when system is in unbootable state. Anyone?
You may also try another HDD and install Ubuntu only onto it. Just for testing.

I'm sure we all try to help you but it's not our fault your system cannot boot. 
Unfortunately, we don't have a crystal ball. At least not me.

---

### Post by tacubuntuforums on 2004-12-09
Ok thanks to all. I haven't much time now to answer. It will take me time to read, think and try things you suggest.

**Magneto>** Thanks!
I have been browsing GNU's grub's manual, I'm familiarizing with it. I had already downloaded a couple of files (files:grub.img and rawrite.exe) to make a rescue grub floppy.

Many insist in bios problems. I think like you, that my bios (a 1995 bios) after that reset ([COLOR=DarkRed]although NOT from the jumper[/COLOR]) is working ok. With win2000 everything works fine. The only thing that still troubles me are the many texts I've read in many, many places stating that using a bios with an 8 GB limit (as mine seems to be, although I don't know how to be 100% shure), the boot partition (even using grub) can't be placed further than the 1024 cylinder.
In my case, the win2000 partition is 16GB. That's why I asked, many posts ago, your opinion about that.
Since you have already helped me once and I saw you were right, I confide in you. I prefer to follow the opinion of a person that seems to be right than to try all the different solutions people suggest throughout the internet, even though by all chances one is correct for my case. Intechanging disks, changing the BIOS again, reinstalling and testing everything by trial and error would be chaotic,  would take me a lot of time, I don't manage many tools to do many things so I can't try everything I read, etc. I prefer to follow a suggestion until it proofs to be right or wrong and use that feedback for a next "hypothesis" follow a plan until, again, it proofs to be right or wrong , etc.
Excuse me, but I don't know if you payed enough attention when I asked you this,  so I'll repeat the question for the last time, and I hope is my last question, since I don't want to bother anymore.
My bios supports LBA, but I don't use it (even if I always read that I should use it)because I could never boot with it. I could only boot a win2000 installation with "normal" mode and "user" type settings, as it is right now.
My question now, is if you think the 8 GB limit and placing my boot partition beyond the first 16 GB, might be the problem, a problem that I may not solve configuring or reintalling grub manually as you suggest and as, of course, I'll try. I hope this question makes sense and I'm not asking you for the truth, just what it seems to you.

**To ALL>**
Just one aclaration, as I've said before: after the bios reset: I installed win2000 then ubuntu and nothing else. Not many installations, not mbr fixes or boot fixes, NOTHING! except using a knoppix CD to _read_ files. If it took me time to reset the bios (thing I thought from the first day) it because i've been PRUDENT and that's the same way I'm operating now. I'm not playing with the computer, as some have believed, I'm not trying crazy things. Nothing!! My decision have been these: decided to do a default ubuntu installation, decided the partitions layout during the installation and answered YES to install ubuntu in the mbr at the end of the installation.
(AND still don't know if I did something unusual, except from having a logical root partition and still don't know what was all the fuss about my installation)


**p!=f >** No, I didn't boot _from the jumper_, since things worked ok and Magneto didn't suggest me anything different I was happy with that.
OK, some people have substituted lilo for Grub and it helpred them (who knows if they touched something else). Besides, I'd llike to use Grub and there must be s solution. Another solution is to use win2000's loader and I'm almost sure it'll work. For that it seems that I have to do what i posted: fixmbr install a bootfile in windows partition for linux and modify the boot-menu  file (boot.ini) I have already talked about this. But since I'd rather boot with grub I don't want to try this now.

I'll also try and set the boot partition, as you suggest,  as primary (but one thing at a time).
I know you try to help, I know how difficult it is without checking everything I do or interacting directly with the computer. I just said that non constructive criticism, and there was a lot, won't help me. Maybe you weren't aware enough that was happening.

---

### Post by TravisNewman on 2004-12-09
The reason I asked if you tried swapping the disks and PCs is this:
If you put the same drive in a different computer and everything worked, you'd know the drive was good, but if it didn't you'd know the drive was bad.

If you tried a different drive in the same computer and it worked, you'd know the problem wasn't the bios, and if it didn't work you'd know the problem IS the bios. I think it is personally. And yes, Magneto, I knew all that you told me, I'm just throwing in new ideas to get to the bottom of this.

Let me revise what I would do now that there's new information.
DO THIS ONLY IF MANUALLY INSTALLING GRUB DOESN'T WORK
Be sure you haven't changed the BIOS defaults.
Boot off of the Ubuntu install CD.
When you get to the partitioning section, do this.
1. Make a /boot partition, primary, ext3, 50 megs or so
2. Make your Windows partition, primary, ntfs or fat32, doesn't matter, 8 gigs or so
3. Make a / partition, primary, ext3, 7.5 gigs or so
4. Make an extended partition, fat32, the size of the remaining space minus 500 megs.
5. Make the swap partition, extended, using the rest of the space.
You can adjust the size of those to your needs, as long as you have at least 2 gigs for Ubuntu.
Accept the changes, wait for it to write the partition tables, then reboot.
Now, you don't have to worry about anything being extended/logical. 

Install Windows on to the second partition you created, which will probably be the only one that doesn't say "unknown filesystem" or something like that during installation. Just remember the size you gave it and choose that one.

Now install Ubuntu, and during the partitioning section, just assign /boot to hda1 and / to hda3. 

That's more complicated than the other way, but you won't have to worry about the 8 gig limit, or the possibility of the extended partitions causing you trouble.

---

### Post by Magneto on 2004-12-09
[QUOTE=tacubuntuforums]
My question now, is if you think the 8 GB limit and placing my boot partition beyond the first 16 GB, might be the problem, a problem that I may not solve configuring or reintalling grub manually as you suggest and as, of course, I'll try. I hope this question makes sense and I'm not asking you for the truth, just what it seems to you.
.[/QUOTE]

Well I know grub doesnt have a problem with that setup since it resides in the mbr which is at the beginning of the disk and can look for the boot partition wherever. 

Let's all understand one thing, ** YOUR BIOS IS FINE NOW AS EVIDENCED BY WINDOWS 2000 BEING ABLE TO BOOT FROM THE DISK ** 
Just wanted to put that out there first since we have  addressed that issue.

Now for your setup I'd suggest the following.

Create a /boot partition on the beginning of the disk
/dev/hda1  is what Linux will call it and grub will call it hd0,0  if this is the master drive on the first ide channel.

Create a partition for windows last at the end of the freespace.

To do this, install windows again, during the setup erase everything.
It will then ask you where to make a new partition - create 1 partition  that will cover all of your linux needs  

you previously put this up
[Color=RED][SIZE=2]IDEmaster (hda) 40 GB:
#1  primary  16.7 GB NTFS
#2  primary  31.9 MB  ext3(*)   /boot
#5  logical  500  MB  swap      swap
#6  logical  9.9  GB  ext3(*)   /
#3  primary  12.7 GB  ext3(*)   /home[/SIZE]
[/color]

Change that to something like this

+----+------------------+------------------+-----+------------------------+
|boot| 9.9 GB /(root)--| 12.7GB /home--|swp-| 16.7GB NTFS----------|
+----+------------------+------------------+-----+------------------------+


So when installing windows 2000 

1.manually create a 50mb partition and a 23gb partition 

that will cover the space for linux - you can change that later during Ubuntu's installation

2.create the 16.7gb partition -  

3.then choose install on the 16.7gb partition 
it will tell you it needs to do something to that 50mb partition that's fine we can deal with that later during linux installation

****note ***** for easy sharing of files between both operating systems as Panicked suggested you might want a Fat32 partition, in linux its called vfat, although you can read safely all of your 16.7gb ntfs partition within Ubuntu.*****

Now proceed with your windows installation- when it is done make sure you can boot straight into it without floppys ;)

Now install Ubuntu
When you get to the the disk setup section delete the two windows partitions at the beginning of the disk - the 50mb and the 23gb partitions

create your new partitions for linux using the sizes you had laid out so when your done it should look similar to this

[Color=BLUE]IDEmaster (hda) 40 GB:
#1  primary  31.9 mb ext3 /boot
#2  primary  500mb  swap      swap
#3  logical  9.9  GB  ext3   /
#5  logical  12.7 GB  ext3   /home    
#6  primary 16.7 GB NTFS
[/color]
****you might want to resize 3 or 5 for adding that vfat/fat32 partition if that's what you want****

now install GRUB to the mbr

IF you have problems like error 17 again after everything is done-  we need to manually reinstall grub and I can help you with that . The same goes for windows not automatically booting. These are small although painful problems that can be easily solved.


Now I didnt specifically lay out each and every step but I think you have those installation details covered, if you have a question about a certain step or action let me know and I'll try to help

---

### Post by tacubuntuforums on 2004-12-10
[COLOR=DarkGreen]**ONE STEP FURTHER  !!**[/COLOR]

This is just to inform you. You don't need to answer if you have nothing new to say,  correct, inform, etc. You've already answered me enough for now. It's like a newspapaer of my case. Comments to your new suggestions follow.

1. Reinstallation of ubuntu (win2000 remains). For the partitions I set same partitions I had before (remember: /boot is a primary & bootable partition)  but I change this:

```
/     is now primary   (as suggested by p!=q)
/     home is now logical
```
I  reformat all partitions and I choose again to install grub in MBR.
Install process reboots for the second stage:
**---->same grub error mesage (Error 17)**

2.  Reinstallation of ubuntu. Deletion of all partitions.
This time: Tell the partitioner to set an _automatic partition_.

result is: one swap and one for root.

I reformat and I choose install grub in MBR.
Install reboots:
**---->same grub error mesage (Error 17)**

3. Try to fixmbr with win2000 rescue console just to check if it's true that after that win2000 is able to boot again from the HD (without floppy help), as many people say. 
**----> negative.** (New) error mesg: press intro to reboot.

4. Try to fixboot with win2000 rescue console, just to check, if after that win2000 is able to boot without floppy help.
** ---> negative.** same error.

5. Download PartitionMagic-demo in order to resize without spending much time the win2000 partition with it. Trying to make it much smaller. The demo doesn't save the changes because it's only demo (f***!)(stupid of me!)

6. Reinstall win2000. delete all partitions and use a 6 GB partition at the beginning of disk.
---->reboots ok and settings and configuration can proceed. OK
(finally MBR is fixed from win200's point of view)

7. Reinstall ubuntu with a default installation and autopartitioning. Try to install GRUB in floppy first (not MBR anymore). I write: /dev/fd0 and (fd0) .[COLOR=DarkRed] Both give an error message, but the floppy has just been formated and is not protected. The drive doesn't even try to read. (??!!!)[/COLOR]. Therefore, I install GRUB in (hd0,1), the second partition which is the root and bootable partition at the end of the first stage of installation.
Reboot: grub loads and shows its prompt.

I type:
grub> root (hd0,1)
**---->Error 18: Selected cylinder exceeds maximum supported by BIOS.** (Note: that's still the situation whenever I boot from the Hard Disk)

8. In order to continue installation I build a generic grub boot diskette and now boot from there. At the grub promt I type same thing:
```
grub> root (hd0,1)
grub> configfile /boot/grub/menu.lst
```
**------>A correct boot menu is shown.**
IF I choose to boot ubuntu normaly from the menu list:
 ----> **[COLOR=DarkOrange]I go to Installation's second stage: configuration and settings start (at last!)[/COLOR]**. 
During the configuration I choose not to automatically download packages (Since there's no more info, I don't have an idea how is this going to be held, if it will bother me or what, and since this is to be used mainly with a slow internet connection, I choosed no in order to do it manually)

[COLOR=DarkOrange][B]Ubuntu boots ....   the graphic login screen appears and I login, but
---> As it has happened to other people: The mouse is frozen.[/B][/COLOR]
I log in!

I dont find any keyboard support to move around the GUI. ([COLOR=DarkRed]is there any??[/COLOR])
I switch to command line session and can login. ok!

9. Same as number 8, but I choose to boot Windows (whose script in the menu.lst seems to be ok.) 
----> **Error message: filesystem type unknown. Error 29. Disk write error**

(Maybe I have to declare that is an NTFS in the menu.lst, I'll check out.)

10. [...removed]

_To sum up:_
Ubuntu has been installed completely, the second stage with grub-in-floppy help. But I still can't boot from hard disk.
No mouse.
¿No keyboard support on GUI?

I don't understand why there isn't mouse. Without mouse there's nothing. OK this mouse is a bit old Genius one, with three buttons and an old (not circular) connector. Nevertheless, in my opinion the priorities should be: First mouse for everybody, then graphic design details and many other things.

**Note:** When I say I tried something 'just to see' is because obviously sometimes I'm looking for clues. I try to find any clue that reveals the problem of directly booting from the HDisk. But the truth is that I don't know very well where to look and the clue might be infront of my nose without I being able to see it. That's the main reason I write all this.

---

### Post by tacubuntuforums on 2004-12-10
**panickedthumb >**  Yes, I agree about trying your partition layout. that's one thing I was thinking to do and some people suggest (in the case of any xxx MB limit problems and dual booting). Also, your details help me to see things clearer. That would have been better than my reduction to 6GB for win2000. I tried what seemed faster. 
Unfortunately each change, without appropiate tools takes much time, so I've got to choose and there's not a chance for everything. I think I'll try that or exchanging drives soon. Another option is to flash the damn BIOS and forget about considering always the remote possibility that the problem might be the BIOS. Reducing factors would drive me less crazy. I haven't done it to try the might-be-easiest way. Flashing a BIOS is dellicate and a totally new matter for me.
Note: You say I'd better check I haven't changed the BIOS default values. Well, as I posted earlier, I changed the CMOS setup: cylinders, heads, mode, etc. just after reseting the BIOS because with the default values th HDD couldn't boot (that's another thing I don't understand; unless I made a mistake). That is, as Magneto sugested me, I reset to the Default Setup values, but then I changed the geometry values because the autodetection (= default) values didn't work (I use "normal" mode mode, even though the cover of my hard disk says: use LBA mode whenever possible and the autodetection values gives LBA mode).
Anyway right now Win2000 boots from the HDD and is working now fine (Needless to say, I believe ubuntu would if installed alone).


**Magneto >** Same to you, your suggestion is similar and the procedure faster. I really appreciate the details. Everything you said is clear. I'm beginning to familiarize with the language and concepts and I'm shure you're trying to be clearer too. I've already read the instructions to install grub and yes, maybe I'll ask you. It's a bit confusing. But I thought that would do the same effect as installing from ubuntu's installation CD. Is it not like that? or you are suggesting that the installation from the CD might have gone wrong, or more precisely, be going repetedly wrong, since I've tried more times?

**I'll try this, unless there's another suggestion, and give you feedback**

---

### Post by Magneto on 2004-12-10
You can't boot from the HD because you never successfully installed grub into the mbr.

You can't get a working linux system because you referenced the kernel in your menu.lst/ grub boot commands but didnt reference the initrd file that contains all the modules for your system, which is also why the kernel panic occurred.

>  I type:
grub> root (hd0,1)
---->Error 18: Selected cylinder exceeds maximum supported by BIOS. (Note: that's still the situation whenever I boot from the Hard Disk)

8. I build a generic grub boot diskette and boot from there. At the grub promt I type:
Code:

grub> root (hd0,1) grub> configfile /boot/grub/menu.lst




**This is due to the fact the you didn't follow instructions.  install grub to hd0,0 for mbr- otherwise you are just priming it to be started by another boot device such as lilo in the mbr, Win2000's boot app in the mbr, a grub boot floppy etc.**

---

### Post by tacubuntuforums on 2004-12-11
[QUOTE=Magneto]You can't boot from the HD because you never successfully installed grub into the mbr.

You can't get a working linux system because you referenced the kernel in your menu.lst/ grub boot commands but didnt reference the initrd file that contains all the modules for your system, which is also why the kernel panic occurred.
 ...[more....][/QUOTE]

Exactly! Now the only thing that should remain is to install grub manually in the MBR.

Yes, the kernel panic ocurred giving wrong/deficient comands manually to grub (initially booted from floppy). But using the menu.lst (configfile) the entry for ubuntu worked and works ok.

[COLOR=Navy]I fixed the entry for windows in the same menu and now I can also boot Win2000 from the menu [/COLOR] (which now displays in the ubuntu colors too).

**[COLOR=DarkOrange]I already configured the serial mouse. Entered to the xsession and moved arround.[/COLOR]**

Therefore, I'll try first what Magneto has been suggesting: install manually grub in the mbr, and only later, if this fails, try the repartitioning as suggested before.

---

### Post by tacubuntuforums on 2004-12-14
**[COLOR=DimGray][SIZE=5][FONT=Verdana]Magneto !!!![/FONT][/SIZE][/COLOR]**

[COLOR=DarkOrange]I'm online with ubuntu!!![/COLOR]

(here  in this computer I called pc2 at the very beginning)

I've benn moving around + taking a look to everything. Next will be to see how all the management of packages works. The first hour I missed a whois client. 

I still haven't tried anything else about the booting. I decided to try instead the connection, Well, it w asn't easy. I tried to use the Networking Administration program and failed, then the modem lights and the same...so I started to use man, move around all directories, a lot of sudo, cat, nano, etc.... and deleting to restart again, but nothing worked.  in the end I used the pppconfig tool and it went fine in the third trial. I connect with pon, etc. ..POOOFF! I thought I was going to open another interminable thread.

OK, this was just to greet all the people that's trying to help, especially you. I hope I'm through with the booting soon, I haven't got much time yhese days, besieds some family is starting to come...so visits...etc.

Bye.

---

### Post by pipeline_1957 on 2005-11-24
did u  ever  find out  how 2 repair this  prolme  please e-mail me with how i can repair  mine as well  at  [email]pipeline_1957@yahoo.com[/email]

---

### Post by pipeline_1957 on 2005-11-24
> **tacubuntuforums][FONT=Arial]I'm very sad I hadn't been able to install and try my recently downloaded **[COLOR=Sienna]Ubuntu[/COLOR] [COLOR=DarkRed]Linux[/COLOR] **.

I'll explain the circumstances in the hope that someone might help.

Does someone knows whether the following Bios fully supports interrupt 13 extensions and if that is relevant in order to continue using it with this Seagate hard disk device:

**-My BIOS:**
ROM PCI/ISA  TX97-E 
Award Modular Bios v4.51PG (c)1984-95
#401A0-0106e
(with LBA and Autodetect supports)

**-My HARD DISK:**
Seagate ST340810A
Cyl: 16,383,    Heads:16,    Sectors: 63,    LBA: 78,165,360
40 GB

**-My PC:**
intel PentiumII-MMX
97MB RAM

The point is that I don't believe that an upgrade is necessary (or maybe it is, in order to make things easier) because that same hardisk with that same BIOS was running a Windows2000 installation using the whole drive in a single partition.

My problem is that after a slight change in the BIOS CMOS geometry of the drive, there had been no way to turn back (undo the changes) and reboot the system from the same hard disk. Booting from a floppy with the basic boot files ("ntldr" converted to a *.bin, "ntdetect" and  "boot.ini") was possible but I couldn't fix the problem with any available tools.

Moreover, no reformatting, no repartitioning, no "fixmbr" or "fixboot" instructions, could help said:**
> - "Ntldr is missing" (the first message after the first change mentioned above).
- "Primary disk error".
- ntoskrl does not exist or it's corrupted (it was false! - but appeared when trying to start the recuperation console).
- "GRUB" (after Ubuntu Linux installation).
- sometimes no message at all.
- "1. No emulation system -Type(00)" just before booting from CD-ROM"
- something like "the automatic system recuperation  found an internal incoherence (A2210) and can't continue", when trying to repair a recen't installation on the clean drive.[/INDENT]

However, I believe the solution must be quite simple. I would appreciate very much your help to determine whether the BIOS supports interrupt 13 extensions and what would help solve this problem. I'm addressing to you after days of effort, search, trials,.. trying by all means to find the solution.

Thank you very much.

Regards from Barcelona.

Toni[/FONT]
e-mail: barcelona(at-nospam)mail(dot)com
 hello i need  the same help  to  this question ,   on start  i get  a few error messages 1  no emulation system type(00) 2  NTLDR missing , what are they  an  how  do i correct  the issues  , please e-mail me the answers at : [email]pipeline_1957@yahoo.com[/email]

---

