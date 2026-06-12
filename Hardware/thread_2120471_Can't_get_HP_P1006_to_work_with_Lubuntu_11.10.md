---
title: "Can't get HP P1006 to work with Lubuntu 11.10"
date: 2013-02-26
forum: Hardware
---

### Post by sampsonrepair on 2013-02-26
Hello all,

I have Lubuntu 11.10 running on a Dell Latitude D600 laptop.  I can't get my HP P1006 Laserjet to work with this computer.  P1006 works fine when the D600 is booted to Windows XP and it works fine with my Panasonic CF 29 booted to Xubuntu 12.04.

I can see the printer from the print setup page, and the computer goes through the motions of printing, but nothing happens at the printer.  The job remains stuck in the print que until manually deleted.  Browsing around, these types of issues appear common with the HP printers.

I have tried the hplip 3.13.2 driver install steps as outlined in a post begun by bung 2 on March 13, 2011.  The problem seems to be missing dependencies.  Some I was able to install by searching in Synaptic Package manager.  The ones I installed no longer show as missing.  The ones still missing I can't find in Package Manager.  Any suggestions?  I intended to attach a screen shot, but either can't figure out how, or don't have sufficient privileges.

Thanks!

---

### Post by mörgæs on 2013-02-26
> **sampsonrepair said:**
> it works fine with my Panasonic CF 29 booted to Xubuntu 12.04.

The straightforward solution is to give the Dell a fresh install of 12.04 or 12.10. You have to let go of 11.10 anyway in two months time.

---

### Post by sampsonrepair on 2013-02-26
Thanks for the suggestion.  It won't run 12.10 (Pentium M, PAE kernel issues.)  I might try 12.04.  I was going to try updating to 12.04 as my first solution, but came across a lot of information indicating that upgrading might be more trouble than it's worth.

---

### Post by mörgæs on 2013-02-27
Usually it is. Go for a fresh install.

Xubuntu 12.04 is supported through april 2015.

---

### Post by sampsonrepair on 2013-03-02
I'm still working on this.  I've now installed Ubuntu 12.04 LTS on the Dell 600.  What a nightmare.  Had to use the mini ISO because of PAE compatibility issues.  Spent over an hour trying to get Unity to function.  The computer can't even see the printer now.  I'm out of time to research this any further today.  Will try again next week.

---

### Post by mörgæs on 2013-03-02
I would guess that Unity is too heavy for the Dell. My choice would be Xubuntu or Lubuntu. 

Both support non-PAE processors using the standard ISO (12.04)

---

### Post by sampsonrepair on 2013-03-05
Agreed.  Unity is too slow.  Later on, would not boot at all (black screen).  I wanted to try "straight" ubuntu, though.  I loaded Xubuntu 12.04 into the Dell and the printing issue is resolved.  I can even network print from my other laptop through this computer (what I wanted to happen.)  How do I go about marking this issue as "solved?"

Thanks!

---

### Post by mörgæs on 2013-03-05
You're welcome. 

The 'solved' flag does not work, but there is a workaround: [http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

