---
title: "No OS"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by altocumulus on 2009-05-17
Hi,   ):P

After successfully installing Ubuntu 9.04 as a dual boot option on my main PC, along with XP, I decided to do a complete Ubuntu install on an 'old' Toshiba Laptop. :p

All seemed to install OK; XP was removed and Ubuntu installed seemlessly. The only issue was with the wireless link to my router.

As an interim stab at a solution I re-booted the laptop to be greeted with the statement .....

"**Operating System not found**" :redface: 

I am, also, unable to boot from the CD ....

Thoughts on a solution would be much appreciated .....

---

### Post by mechdave on 2009-05-17
First thing to confirm would be is the boot from cd in the BIOS enabled? Also make sure the hard drive is configured in the BIOS as a bootable device...

---

### Post by altocumulus on 2009-05-17
Thanks for your reply **mechdave**, much appreciated.

The settings in the BIOS are all as expected.....

As this is a Toshiba laptop, I'm wondering if there is something 'special' about how they configure their machines that could be a problem.

---

### Post by altocumulus on 2009-05-17
Me thinks description should now read 'lost cause'.

**Boot on CD-ROM :**

"Ubuntu" disc in drive results; [COLOR=Red]Toshiba welcome screen[/COLOR], boot facility and the error message "No Operating System" (or similar). 
No reaction, either to a 'forced' boot on CD-ROM.

**Boot on Floppy :**

DOS startup floppy results; blinking cursor, but no prompt for command.

**Boot on HDD, with no floppy nor CD :**

Results in blinking cursor, no prompt for command.

At least CTRL ALT DEL works ! - but seemingly little else ....

Seems Wubi deleted XP Pro satisfactorily, gave the impression it had installed a working Ubuntu - whereas in reality it has left me with a machine that wants to do nothing. Admittedly there could be something wrong with the CD/floppy drives - otherwise I'm up the creek without a paddle, nay without the proverbial canoe .... !


(Life is but a bowl full of cherries, some fresh and juicy - others a bit on the mouldy side)....

---

### Post by m3asmi on 2009-05-17
hi 
how i can hav an ubuntuOs 
it's whith update of ubuntu ?
rep

---

### Post by coffeecat on 2009-05-17
> **altocumulus said:**
> Seems Wubi deleted XP Pro satisfactorily

Point of information: wubi doesn't delete Windows. It installs Ubuntu inside the Windows C:\ partition. I think you're mixing this up with the conventional Ubuntu installer that does delete Windows - **if** you ask it to.

Be that as it may, this sounds like a BIOS problem. I've installed Ubuntu to half a dozen laptops and a dozen or more desktops and never seen anything like this. I know you said that BIOS settings are as expected, but I wonder if the BIOS coincidentally became corrupted somewhere - the Ubuntu installer wouldn't have done this. Try going into the BIOS screen and resetting to defaults and saving.

Also, on a desktop at least, you can clear the CMOS with a jumper on the motherboard. I don't know whether that's possible with a Toshiba laptop but in any event it would be a blighter to get to. Nevertheless, worth doing if you can.

---

### Post by altocumulus on 2009-05-17
> **coffeecat said:**
> Point of information: wubi doesn't delete Windows. It installs Ubuntu inside the Windows C:\ partition. I think you're mixing this up with the conventional Ubuntu installer that does delete Windows - **if** you ask it to.

Ok, so the Ubuntu installer deleted the windows because **I** asked it to, as I wanted the Ubuntu as the only OS on the lappie....  ;)

> 

Be that as it may, this sounds like a BIOS problem. I've installed Ubuntu to half a dozen laptops and a dozen or more desktops and never seen anything like this. I know you said that BIOS settings are as expected, but I wonder if the BIOS coincidentally became corrupted somewhere - the Ubuntu installer wouldn't have done this. Try going into the BIOS screen and resetting to defaults and saving.

Okay I'll give that a try and see....Thanks...

> 

Also, on a desktop at least, you can clear the CMOS with a jumper on the motherboard. I don't know whether that's possible with a Toshiba laptop but in any event it would be a blighter to get to. Nevertheless, worth doing if you can.Opening up a laptop is probably more than I am competent to do. I'll do a PC, but not that .... :shudders:


Thanks for your reply - I shall investigate ...... :popcorn:

---

### Post by Enter t'Ibex on 2009-05-17
I don't think there will be a jumper.  But before you break out the screw drive, simply reload the bios defaults.  That may clean up any garbage in there.

If you are still have boot problems, then you are in the same boat as me (laptop with no removable media).  Right at the moment, I consider myself somewhat of an expert on removing the laptop drive sticking it into a desktop and loading a bootable partition on it. (I think I have had every issue that there could be)

Let us know how what happens

---

### Post by altocumulus on 2009-05-17
It was a very worthy suggestion, but unfortunately the default BIOS settings have made no difference....(tried 3 times just to triple check)...

I'll still paddling down the swanee without a canoe and any paddles.....

---

### Post by Enter t'Ibex on 2009-05-17
You can take the HD drive out, get a 2.5" to 3.5" converter and install it into your working desktop, then use netbootin to create a small partition with the loader on it, and retry the installation.

I just did that, and I know that we can get your laptop to boot again, but booting and running are two different things, and like my tablet it may just be dead as well.

---

### Post by altocumulus on 2009-05-17
Aye, dead might be right - this machine was £1500-2000 new some years ago - probably get a better spec one these days for £300 ? with linux installed too .... 

Ah well - I'll give some thoughts to my next step - hammer and chisel anybody ?

:p

---

### Post by coffeecat on 2009-05-17
One thing I forgot to mention/ask. When you go into the BIOS, it should list all the hardware, including all drives: floppy, CDROM, hard disc. Is it? Because if those drives aren't appearing, you've got yourself one dead BIOS or dead motherboard there.

Nailed to the perch and all.

Hang on a minute.... Floppy did you say? :shock: Blimey. It doesn't have a carrier pigeon loft as well, does it? :p

---

### Post by altocumulus on 2009-05-18
Yep, the BIOS says everything is there as expected, including the coffee-maker and the ice cream scoop .... ;)
After all it's an 8-9 years old machine ......

To all appearances everything is 'there' except any operating system. Though there is no guarantees on the BIOS, of course......

I shall continue to "investigate" ....

---

### Post by altocumulus on 2009-05-18
Okay .... Laptop will boot on an XP Pro disc.
Went through the setup procedure as offered.
Setup did not like the existing partition on C:, so I chose the option to delete.
Setup then formatted this partition. 
Setup allowed to continue (hoping I can get away with not knowing the registration details).

Machine switches off !

On reboot, Error NTLDR missing ....

Tried bootcfg /rebuild, but this command did not work due to 'errors on disc'

chkdsk - no errors detected
chkdsk /p - Some errors on disk 

!

Reboot again on XP disc ...
Watching it set windows up - it gets about 1/2 way and then switches off...

Me thinks either a hard disc problem or perhaps a power issue (battery's been defunct for a couple of years!!!!)

Obvious solution, now, seems to be to get a new lappie....

Thanks for all your help and suggestions .....

:popcorn:):P

---

### Post by coffeecat on 2009-05-18
> **altocumulus said:**
> Obvious solution, now, seems to be to get a new lappie....

If, by chance you're looking for recommendations, Jaunty 'just works' on my new Sony Vaio VGN-NS20S - £550 from PCWorld. Well, to be honest, I haven't tried the dial-up modem or the ethernet connection, but everything else - Webcam, SD card reader, Wireless, suspend, hibernate, special FN key combinations ( :shock: ) - simply worked out of the box. Big disappointment - I was looking forward to many happy hours of hacking things trying to get them to work. :lol: 

The biggest problem I had was trying to get the damn Vista partition shrunk as much as I wanted.

I think you can also get it from Comet, which is worth a visit anyway, just to look at a £50 cheaper Sony model that comes in shocking pink. The most extraordinary thing I've seen in a long while.

---

### Post by altocumulus on 2009-05-18
Shocking Pink !!! LOL - almost as bad as a Kindle in green and red !!!

---

### Post by altocumulus on 2009-06-03
2 weeks on and after hair tearing and nail biting, have discovered Toshiba Product Recovery (2001) discs and now have a working laptop.....

Yes, OK I can save myself further anguish by installing a dual boot Windows Home 2001 & Ubuntu. But with Windows so much out of date, it would make sense to just load on Ubuntu (yes?).

So I'm back to the stage before I first started on this journey. Can anyone think of where I might have gone wrong the first time that resulted in a lappie that refused to work because of a missing ntdlr?

OR am I likely to have this problem because it is a Toshiba and they have installed their own software packages with little idiocyncrasies?

---

### Post by presence1960 on 2009-06-03
> **altocumulus said:**
> 2 weeks on and after hair tearing and nail biting, have discovered Toshiba Product Recovery (2001) discs and now have a working laptop.....

Yes, OK I can save myself further anguish by installing a dual boot Windows Home 2001 & Ubuntu. But with Windows so much out of date, it would make sense to just load on Ubuntu (yes?).

So I'm back to the stage before I first started on this journey. Can anyone think of where I might have gone wrong the first time that resulted in a lappie that refused to work because of a missing ntdlr?

OR am I likely to have this problem because it is a Toshiba and they have installed their own software packages with little idiocyncrasies?

Why chance it. Defrag windows at least once prior to installing Ubuntu. Yes even after you just restored it, because that is when windows has some bad defragmentation.Shrink the windows partition during guided install to the bare minimum you need and give Ubuntu the rest of the space. Simple & effective solution. No shame in having Windows on your drive...especially if you hardly ever use it. :p

---

### Post by lisati on 2009-06-03
My old laptop (about 3-4 years old, recently donated to my nephew and with a dud battery) is a Toshiba. Jaunty ran on it, just......I had to use the alternate install disk when I installed Feisty (which was the first distro I used)..... *sigh*

---

### Post by altocumulus on 2009-06-03
:KS  :popcorn:


Thanks **to you both** for your responses, I shall ruminate on them - minimising the windows installation would decrease it's space on the disc.


This lappie also has a dud battery .... ;)

---

### Post by altocumulus on 2009-06-03
it never gets any better !!

the burned disc is OK, at least it allows me to install on my main pc, but I cannot get anything to work on the laptop. 
I can read disc contents on the laptop. 
despite CD/ROM being first boot device, and also forcing boot from CD, windows insists on loading.

rawwritewin.exe runs on floppy, but maintains it cannot find sbm.bin (manually checked its existence).

cannot run wubi.exe either from double-click on icon [**this application has failed to start because the application configuration is incorrect], nor from a d: command prompt

---

