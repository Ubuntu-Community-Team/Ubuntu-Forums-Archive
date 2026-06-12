---
title: "Brand New to Linux software. Have some questions"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by InnovatedMind on 2009-06-08
Hey mates.

So a month ago I did a fresh install of Windows 7 RC (x86) and love it, though I found out that some of my games wouldn't work (that implement GameGuard) so I decided to install Windows XP on the partition of Windows 7. I renamed it Windows2 and I wen't into XP (since it wouldn't show the MBR) downloaded this program called 'EasyBCD' to add in Windows XP to the MBR so now the Seven MBR screen pops up allowing me to choose which windows I wan't to boot up in.

Anyways, getting past that brief summary of recent events, I was thinking about adding in a 3rd OS, a Linux OS. Though, I don't want it to hurt my other OS's I was thinking that maybe I can delete everything on my Second Drive (D:\) and do a fresh partition while installing ubuntu so ONLY ubuntu is on that drive. My question is.. simply, Would it work? And if it does work, after I install Ubuntu will I have the same problem that I've had with Windows XP, where only Ubuntu would boot and wouldn't show me options of which OS I would like to boot.

I don't know anything about Linux, I am an EPIC Noobie. 

BTW, I already downloaded;
Ubuntu 9.04 Desktop; AMD64

Computer specs are;
AMD 64 3000+
GeForce 8400GS
1GB RAM
SoundBlaster Audigy 2 ZS

Thank's!
- Joey

---

### Post by Partyboi2 on 2009-06-08
Hi, yes you can install Ubuntu as a 3rd operating system, Ubuntu uses grub as its bootloader which you may find easier to use then using EasyBCD. 
During the installation grub should should find all your operating systems and add them, if not you may need to do some minor tweaking.

---

### Post by InnovatedMind on 2009-06-08
Thanks mate :D

Is there any software that I can use on XP right now to clean my Second HD, and delete the partition aswell?

---

### Post by clarsek4 on 2009-06-08
Good day to everyone here):P
Brand new to Xubuntu, now 4 days old, and not getting anywhere.

Don't want to spoil this thread, but I need help as well.

Seems to me, that issues with W-lan and graphic's are the weak points in Linux. And of course I'm not lucky, and also stucked in this part. I seriously considder to leave the Linux again, as I can't figure out how to get new drivers installed.
During my, now 7th installation of xubuntu 9.04, I can still not get the w-lan configured, despite I have 9 different usb wireless sticks here on hand. Not one is supported by xubuntu? Weird! Wireless are so much in common, and yet linux have not included drivers for this. And my sticks range from 3-4 years old up to the latest, Netgear for vista.
I have the new driver, on a usb stick, no problem. I can find the folder, it's a "tar.bz2" extension. I have figured out that means something like a compressed file.
I can uncompress the folder to 2 files.
But nothing more. Where should they be copied to? And how to install them? I have now for 4 days been harvesting the web for advises, but still with no luck. 
I might have had a chance, if the folder I've got was a packet, but this seems just to be 2 files. Meaning packet manager is good for nothing. 
I have tried to follow a training, using the terminal, but honestly, if I must spend 2 or 3 weeks writing codes, before I can copy a file, Linux will leave my computers right away, and my very much hated XP go back on again.
Ain't there someone out there, who can give me a little advice, so I will be back on track again? Please!

clarsek:cry:

---

### Post by zubin71 on 2009-06-08
if you find partitioning your hard disk difficult at present, install ubuntu using wubi and try it out. 
just boot into XP and run your ubuntu CD. the wubi installer launches and installation is a breeze from there on...

cheers!!!

---

### Post by zubin71 on 2009-06-08
1. uncompress your folder into the Desktop
2. open a terminal and change the current directory to the extracted folder.
3. run the following commands sequentially

$ sudo ./configure
$ sudo make
$ sudo make install

this should install the wireless driver. restarting your system after this is recommended. 

And to get graphic card drivers do the following:-

go to System>Administration>Hardware Drivers

your hardware driver must be listed in there... click and download ! as easy as that!

cheers!!!

---

### Post by clarsek4 on 2009-06-09
Hi Zubin71

Thanks for your help. I'm embarrased to continue, but it wont work. 
I'm that much a newbie, like a baby has to learn breathing, before it can live.
I did as you described, couldn't get the 2 folders right where I wanted them, so I used the filemanager to copy all the files into one folder.

First, $ sudo ./configure says not such a file or path is found. (I was in the right folder!)
So much for that. I can "make" and "make install", but all ifconfig and iwconfig tells me, that the module "RT73" don't exist.

Nothing more about that crab. I can see, the more I trawl the web, that Linux are loosing many potentional users, just at their first introduction, as they never will get their network running. Here I must admid, Microsoft are light years ahead.

I will though not give up, I just need the time, that's weeks or years, to get myself into all that terminal coding. I code C++ and a lot Visual Basic stuff, so that must just be like learning a new lenguage. Just a little frustrating.

Now a couple of questions: 
Any out there, who can link me to a list of existing wireless usb dongles included in xubuntu 9.04? I will purchase my now 10th dongle, but be sure the installation can find it!
Can someone link me to terminal programming phrases? The build in help is worth nothing.
Will open office installation be just as funny as my wireless? Or will that just work "Out of the box?"
How to avoid xubuntu just to build new installations up on top of each others? I have now 8 possible choises in my loader, at start up? (Don't know if they allworks)
Can i use "Ghost" to make a recover of my installation? Or will there be an equal program for that?

All for now, Hope for some replys

Clarsek

---

