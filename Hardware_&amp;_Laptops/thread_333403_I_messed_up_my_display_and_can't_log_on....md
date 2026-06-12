---
title: "I messed up my display and can't log on..."
date: 2007-01-07
forum: Hardware &amp; Laptops
---

### Post by sqlplus on 2007-01-07
I'm one of those who keeps meaning to make the move to using Linux as my main work environment, yet havn't yet done so.    So, when I needed to make a dvd presentation from my laptop, and the dvd wouldn't play well on xp, yet would on kubuntu, I was excited about using kubuntu for the dvd presentation.  However, in trying to get it to work I ended up breaking my kubuntu.  Here's what I did:

First, my system - kubuntu dapper, dual boot with xp on an hp pavilion dv8000 laptop.

I needed to get my laptop working with a projector. In windows this is pretty much automatic, just plug it in to the external monitior port and it works. Not in kubunutu, at least  it didn't work for me.   So I tried to poke around and figure out how to set it up -  of course with it being last minute 1 hour before the presentation, and with no internet connectivity to google or ask for help!   I went to system settings, display, and on the hardware tab (I think) set the secondary monitor (which I thought would be the projector) to be primary, and the 1st monitor as secondary.    Then, after rebooting the system hangs on restart, I assume when trying to load x-windows.

So two questions - 

1) Most importantly, how do I get my system back up and running? I  assume I will need to boot into command line mode (how?) and edit some config file, but I need the details.

2) For future, how do I get my laptop (or desktop for that matter) to work with an external projector/monitor?  

Thanks in advance!

---

### Post by meng on 2007-01-07
You may be able to get into console (commandline) mode by pressing ctrl-alt-f1. Then logon with your username/password. Then:
sudo dpkg-reconfigure xserver-xorg

---

### Post by Omnios on 2007-01-07
You can also choose recovery mode from grub and log in and do the reconfig

---

### Post by teaker1s on 2007-01-07
not sure on kde but providing it's cocked up xserver. At grub select recovery mode.
then log in and
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]
to reset kde to defaults see this thread
[http://ubuntuforums.org/showthread.php?t=333090]("http://ubuntuforums.org/showthread.php?t=333090")

---

### Post by sqlplus on 2007-01-07
Looks like that did the trick.  Thanks for the quick help!

---

### Post by teaker1s on 2007-01-08
sorted:mrgreen: , edit your first post and you can tick to show thread resolved:biggrin:

---

