---
title: "CD burning very slow in Hoary"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by unrock on 2005-04-25
Having looked at the forums for a couple of days now, I haven't been able to find a situation like mine. The problem is - K3B and Gnomebaker both burn normal CDR's (and CD-RW's) at a very slow speed. The rated speed for my burner is 52x (although actually 40x without having to press buttons on the front of the writer - it's a Sony CRX230ED, according to cat /proc/ide/hdc/model). The speed obtained is generally 4.5x when burning an audio CD using K3B, and 12x when creating a data CD. I've set K3b to burn at 40x, but when it starts burning, it warns me that this speed is not supported by my drive and it's switching to 4x.

I've got dma on, in case you ask:

/dev/hdc:
 IO_support   =  3 (32-bit w/sync)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

I'd love to get this sorted! Thanks

---

### Post by crmanski on 2005-04-25
The wiki mentions that you should use gksudo to run the k3b app...
[http://www.ubuntulinux.org/wiki/K3BHowto](http://www.ubuntulinux.org/wiki/K3BHowto)

I'm not sure this would slow things down,  but was wondering if you were running k3b as root.

---

### Post by unrock on 2005-04-25
Just tried running K3b through gksudo. It does seem marginally faster and there was definitely more buffer movement (previously the buffer would sit at 98% throughout the burn.)

The average speed reported was 6.67x, which is some improvement, although not quite the advertised speed!

---

### Post by phen on 2005-05-08
Hello!

I got the same problem. I tried gnomebaker, k3b and xcdroast. Xcdroast gave me a warning: My Cd-Recorder was set up as an ATAPI device and that would highly affect the burning speed. Xcdroast proposed to improve speed by using SCSI Emulation. I am at the moment looking for a proper way to do that under ubuntu (or any other solution, as the xcroast warning might be depreciated, might it not?)! Any help is very appreciated :-)


have a nice sunday!

Kai

---

### Post by no neck joe on 2005-08-06
Bump for exact same issue.

---

### Post by crane on 2005-08-06
I've noticed this as well. I don't burn very open though. I usually burn ISO's.
Before I just right clicked and select burn. Now if I don't set my burn speed to 2x or 1x I get errors with the burn. :???:

---

### Post by no neck joe on 2005-08-08
Bump.

---

### Post by phen on 2005-08-08
ok. scsi emulation didn't work. it was not making things faster here. maybe its fixed in breezy :-) 

cheers

---

### Post by no neck joe on 2005-08-09
Upgraded to Breezy, no dice. Between this and my nightly locking up issue I think I'm  done.

Perhaps in 6 months I'll try again. 

Ciao!

---

### Post by drizek on 2005-08-09
[QUOTE=no neck joe]Upgraded to Breezy, no dice. Between this and my nightly locking up issue I think I'm  done.

Perhaps in 6 months I'll try again. 

Ciao![/QUOTE]
 why do people give up so easilly?

go to distrowatch.com and make your way down the list.

---

### Post by no neck joe on 2005-08-09
A month and a half of trying to resolve an issue isn't giving up easily. I can't have an OS that locks up for no apparant reason a couple of times a day residing on my machine.

Trust me, I really don't want to go back to Windows.

---

### Post by drizek on 2005-08-09
[QUOTE=no neck joe]A month and a half of trying to resolve an issue isn't giving up easily. I can't have an OS that locks up for no apparant reason a couple of times a day residing on my machine.

Trust me, I really don't want to go back to Windows.[/QUOTE]
 nobody is forcing you to use ubuntu. there are a lot of other great distros out there that will most likely not have these problems with them. 

also, the locking up thing happened to me. it went away after i installed proper drivers for my nvidia card.

---

### Post by no neck joe on 2005-08-09
You're right. I shouldn't give up so easily. Thanks for the pep talk.

---

### Post by Lem on 2005-08-10
Does gksudo still work in KDE?.. I'm a linux newbie, so excuse me if this really is a daft question, but most info on here is gnome-specific.

---

### Post by phen on 2005-08-10
don't know how this question is connected to cd burning :-), but anyhow: no. i think you have to use kdesu!

cheers,
kai

---

### Post by Mozzer on 2005-10-24
Massive bump.

I'm trying to use GnomeBaker to burn an iso but it says it won't go any faster than about 12x. On windows it will go at the full 52x. Is there any way of curing this?

Thanks,
Mozzer

---

### Post by djSeverin on 2005-12-31
Hey guys and girls - I hope this helps. I also have been having problems getting my burner to burn above 4x. I enabled DMA, 32 bit transfer etc and nothing helped, till I ran into this:

[http://www.ubuntuforums.org/showthread.php?t=58426]("http://www.ubuntuforums.org/showthread.php?t=58426")

If you're using KDE, try the above link - did wonders for me!  :KS

---

