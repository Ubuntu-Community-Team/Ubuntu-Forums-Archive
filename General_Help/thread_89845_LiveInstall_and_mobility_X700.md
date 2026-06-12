---
title: "Live/Install and mobility X700"
date: 2005-11-13
forum: General Help
---

### Post by cpinfdp on 2005-11-13
I am new to linux, been told forever to try it out so my brother pointed out this was a good distro.  

**Problem:**

Tried live cd, xserver will not load, so I get a fun console, of course I don't know what the hell I am doing, so you know my linux experience so far is going great.

From what I have read, xserver does not like radeon mobility X700.  I have found a 'patch' of sorts that has the pci id's for the newer radeon chips, hopefully letting me start xserver and see what linux runs like on my computer.

I want the **radeonpciids.diff** file to be included in the live/install dvd so that when I decide to try it, xserver will load, hopefully. I don't know where in the actual setup files, packages, or wherever that I actually need to put it in order for the install or live portions to actually use it. 

**Questions:**

-Ubuntu is based on Debian, yes?
-Do I need a debian package, say a package of radeon drivers?
-How will debian know it can use this new 'package'/'patch'?
-Gnome vs. KDE? (This might start a war, I have heard)
-Where is my penguin damnit!?

I don't know how to log the output that the live gives me, I am guessing you have to install to do that. Tried Kubuntu live, didn't work, just figured that distro was old; that's when I went to Ubuntu.  I haven't tried other distros (heard Knoppix supports everything Live).

---

### Post by brim4brim on 2005-11-13
I had a similar problem with the X600 Mobility.  ATI does not support the mobility lines drivers and it's up to the laptop vendor to give you proper Linux drivers or make them compatable with ATI's.  Of course Dell didn't do this but anyway this is how I got it to work although I only end up using the Mesa drivers and not the proper ATI ones they work well for most things except games.

When given the prompt to hit enter for default or type a command when CD first boots type this:

linux vga=771 noapic nolapic

This worked for me although I can't promise it'll work for you.  I was also using the install cd and not the live cd when I did this.  I assume it'll work for yours too but you might have to substitute "live" for "linux" in the command.

---

### Post by cpinfdp on 2005-11-13
Tried the above command, but it didn't work.  I also tried sudo **dpkg-reconfigure xserver-xorg**, but I don't know how to restart xserver, so that kind of put a damper on that.  Could someone tell me how to start xserver after I reconfigure xserver. 

I know that sounds like such a newbie thing to ask, sorry, just my 26th hour trying linux.
Would also appreciate insights on other questions, thanks all.

---

