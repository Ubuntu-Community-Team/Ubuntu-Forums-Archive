---
title: "re-installing 9.04 or waiting for 9.10 in order to clean install"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by aboatwri on 2009-10-22
I have been playing with my 9.04 install as I was having the well documented skype sound issues. When I did that I did loads of mods especially around the sound. It is all kinda of working but not as intended or it worked when I had first installed 9.04 clean. 

So I was thinking, could I re-install 9.04 clean but was concerned that: 
a/ the machine is dual boot at moment and could not re-install XP
b/ the machine has (ubuntu) data that I do not want to loose.

Would a 9.10 upgrade "clean" the whole sounds issues I am experiencing? If If not then how do I get back to a "known good state". 

Thank you for any help.

---

### Post by phillw on 2009-10-22
Clean installs seem to be the most recommened route.

Whichever way you decide to go - do a backup !!!!

[http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)

To just re-install ubuntu - follow the procedure for installing ubuntu on a dual-booting system, choosing to format the unbuntu partition.

check the forums re: your sound problem before you jump to 9.10 to see if your sound system is supported easily in 9.10 the same for wi-fi etc.  If in doubt, use a liveCD to 'test-drive' it.


Phill.

---

### Post by earthpigg on 2009-10-22
i agree with the poster's advice above me.

especially about backing up.

you said you have data you do not want to lose.

if you do not have that data backed up, then you are acting as if you wanted to lose it. regardless of operating system.

> **phillw said:**
> If in doubt, use a liveCD to 'test-drive' it.

yes. if you cannot get it to work on the live cd, do not assume it will work when installed.


what i would do in your shoes:

wait till 9.10 comes out. try the live cd.

if my hardware was still not supported, i would move to a different distribution on that computer.

i myself am not using Ubuntu on my primary desktop because it does not support my motherboard very well at the moment. all of my other computers use Ubuntu, but i'd rather use a distro that supports my hardware with***_out_*** workarounds or undue effort on my part.

don't fear the learning curve. a package manager is a package manager, a linux terminal is a linux terminal, a graphical installer is a graphical installer, and GNOME is GNOME. all distributions shamelessly steal ideas and processes from each other all the time, so the end result is that distros with similar objectives (ie: "Home User's Desktop") all end up very similar.

if 9.10 supports my hardware well, good! i'd prefer to use ubuntu.

if not, no major loss to me. 

as long as you have your /home folder, you can be at home in any distro.

---

### Post by aboatwri on 2009-10-23
Thank you for all that advice. It is broadly what I thought. I know 9.04 supports all my sound stuff becuase it did in the past before I installed SKYPE and it went all crazy. 

The only question I would like to know though is, how do I keep my XP install. will re-installing from a live CD delete that too? 

Thank you

---

### Post by AlphaLexman on 2009-10-23
> **aboatwri said:**
>  The only question I would like to know though is, how do I keep my XP install. will re-installing from a live CD delete that too? 

Thank you

No, XP is on a seperate partition. Grub will know.

---

### Post by phillw on 2009-10-23
> Thank you for all that advice. It is broadly what I thought. I know 9.04 supports all my sound stuff becuase it did in the past before I installed SKYPE and it went all crazy.

WHAT ???!!!! --- OMG...

I've just put skype onto my system - not fully tried it out yet .... I can feel a FULL BACKUP coming on :)

and, BTW, for a little 'tip-ette'... When you've decided on how you're going to do things. Have a good read of that article. If you have a decent sized disk, slice a partition called 'backup', format it ext3 (And, before you all flame me - ext3 is considered more stable than ext4 for this purpose) large enough to hold a backup(s) of your working system. When you're installing new stuff, use the backup routine to take a 'snap-shot' of your system (A bit like System Restore in windows). 
This has the added advantage that you can tweek your script to backup to an external drive as all you need to alter is your output path name.

Phill.

---

### Post by mikewhatever on 2009-10-23
Actually, the newer version of Skype seems to play nicely with pulseaudio. Is that the problem you were referring to?

---

