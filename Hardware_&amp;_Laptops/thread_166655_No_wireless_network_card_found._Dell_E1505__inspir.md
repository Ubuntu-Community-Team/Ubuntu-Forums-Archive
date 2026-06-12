---
title: "No wireless network card found. Dell E1505 / inspiron 6400"
date: 2006-04-26
forum: Hardware &amp; Laptops
---

### Post by siDDis on 2006-04-26
Im having trouble getting my network card on this laptop to work. I've been googling and found two solutions that is not very newbie friendly.

The first one is this
[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)
But I cant get it compiled because it lacks some files.

Second is ndisgtk which install the windows driver. But neither that work for me :(

Suggestions?

---

### Post by hunter186 on 2006-04-27
You should check out this thread:  [http://www.ubuntuforums.org/showthread.php?t=140085&highlight=e1505](http://www.ubuntuforums.org/showthread.php?t=140085&highlight=e1505).  There are several posts by wheelspin.  He's written a script that installs the driver necessary for your wireless card.  Get the most recent version of that script and try it out.  It worked on my e1505.

---

### Post by siDDis on 2006-04-28
Awesome, it worked flawless =)

I quote it here so its easier for peeps to find it instead of diggin through 500 replies.

[QUOTE=wheelspin]This is the official stable drivers from intel, Intel PRO/Wireless 3945ABG Driver for Linux 1.0.0 The installer now includes ALL the needed files (except dependancies) including the latest ieee80211-1.1.13 subsystem. Just extract it and run the install script. 

Update: these drivers are based on the 0.0.69 development snapshot, the 0.0.74 installer posted earlier has been fixed (I think) the "make install" had been disabled

```
./ipw3945install
```

I would like to narrow down the dependancies listed in the first couple lines of the script, I'm pretty sure some of them are not needed to get it compiled and installed, (if someone could help out here that would be great) that way it will be easier for some one without an active connection to get up and running by copying the installer to a floppy or cd. I don't have time right now to do a fresh install to check what they are but I will do so as soon as I finish up a couple of other projects.[/QUOTE]

[http://www.ubuntuforums.org/attachment.php?attachmentid=8223&d=1144780156](http://www.ubuntuforums.org/attachment.php?attachmentid=8223&d=1144780156)

---

