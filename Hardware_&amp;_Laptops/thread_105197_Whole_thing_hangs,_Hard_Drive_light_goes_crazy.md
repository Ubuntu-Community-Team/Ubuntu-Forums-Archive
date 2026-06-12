---
title: "Whole thing hangs, Hard Drive light goes crazy"
date: 2005-12-17
forum: Hardware &amp; Laptops
---

### Post by tabinin on 2005-12-17
I have had a problem the last few days where my system starts reallys slowing down and then eventaully freezes.  The hard drive light is going koo koo bananas like it is trying to do something, but it stays hanging and I can't use the mouse or keyboard.

Here is what is running:
KDE 3.5
Amarok
Opera
Firefox 1.0.7
Konqueror
Kopete
Konsole
Azureus

So here are the questions:

1) anyone able to guess what is causing the thrashing/hangup?
2) is there a log I can look at to answer the above question myself?  (or is there something I can run to capture such a log?)

---

### Post by mlomker on 2005-12-18
I'd recommend booting up to one of the linux CD's (I like Knoppix) and seeing if the partition is accessible.  You may want/need to run fsck to check the disk.

---

### Post by tabinin on 2005-12-20
[QUOTE=mlomker]I'd recommend booting up to one of the linux CD's (I like Knoppix) and seeing if the partition is accessible.  You may want/need to run fsck to check the disk.[/QUOTE]

I booted into Knoppix and was able to access my Kubuntu partition (hda3), but didn't have much luck running fsck.  Did you have a particular command in mind to run?  The drive should be unmounted, right?

---

### Post by mlomker on 2005-12-20
If it is a ext3 drive (the default) then you should be able to run **fsck.ext3 /dev/hda3**.  **man fsck** would give you all of the options.  You do want it unmounted but that's the default with Knoppix until you click on the icon.

---

### Post by tabinin on 2005-12-21
[QUOTE=mlomker]If it is a ext3 drive (the default) then you should be able to run **fsck.ext3 /dev/hda3**.  **man fsck** would give you all of the options.  You do want it unmounted but that's the default with Knoppix until you click on the icon.[/QUOTE]

Thank you.  It is good to know I was doing it right.  I ran the command and it took like 1 second and exited with almost no info.  I guess that is a good sign.

By process of elimination, it seems Azureus is the culprit.  I haven't been running it for the last few days and everything has been fine.  I guess Java could be at fault too...

---

### Post by thieummm on 2005-12-22
I am having the samei issue: sometimes the hard drive starts making reads or writes and then never stops.... It prevents me from accessing the console to see what's happening.... it is very annoying..............

---

### Post by megamania on 2005-12-22
The first thing that comes to my mind is that it could be the slocate job running.

If you don't have much ram the apparent freeze might be justified, especially if you have other applications running when the job starts - at least that's what happens on one old computer that I have (P2 with 128Mb running Breezy).

You might try to have TOP running on a terminal shell, so you'd be able to tell what is running when the h.d. light goes berzerk.

Hope that helps, I'm just guessing though.  :-)

---

### Post by km4hr on 2005-12-22
Firefox 1.0.7 has caused similar problems on my system,  usually when several tabs are left open over a period a of day or so. Memory usage goes way up and the system starts swapping to disk, I presume. Stopping Firefox fixes the problem.

---

### Post by regomodo on 2007-03-22
I know this is an old post but my ubuntu is doing the same thing. However, i have 2GB of RAM so it can't be that. Try to ctrl+alt+backspace but it getsto the login screen after 5minutes. Try and log back in. Not a sausage.

I am getting unbelievably stressed out with Ubuntu. 1 thing after a f**in other.  Beryl with Emerald caused my screen to go to white screen of death. Followed the guide to the word. Thats probably because a Compiz install wouldn't go all the way, despite following what it said in the guide. Ktorrent and Amarok placing its topbar icon in random places or not at all. GUI apps not appearing in applications section.

Sweet Jesus, all this faffing around makes me want windows so much (cus i can't afford a mac) which is a crap situation to be in.

Here we go again,  a complete sodding Ubuntu install again for the umpteenth time. Been trying to get Ubuntu working for a week now.

Whoever said linux is easier than windows is a liar

---

### Post by Zephrin on 2007-06-06
> **regomodo said:**
> I know this is an old post but my ubuntu is doing the same thing. However, i have 2GB of RAM so it can't be that. Try to ctrl+alt+backspace but it getsto the login screen after 5minutes. Try and log back in. Not a sausage.

I am getting unbelievably stressed out with Ubuntu. 1 thing after a f**in other.  Beryl with Emerald caused my screen to go to white screen of death. Followed the guide to the word. Thats probably because a Compiz install wouldn't go all the way, despite following what it said in the guide. Ktorrent and Amarok placing its topbar icon in random places or not at all. GUI apps not appearing in applications section.

Sweet Jesus, all this faffing around makes me want windows so much (cus i can't afford a mac) which is a crap situation to be in.

Here we go again,  a complete sodding Ubuntu install again for the umpteenth time. Been trying to get Ubuntu working for a week now.

Whoever said linux is easier than windows is a liar

I'm having the exact same problem.. typically only when running Ktorrent... everything else runs fine but when I run Ktorrent on Ubuntu Feisty after 30 minutes to an hour or so the hard drive just goes nuts!
Any help would be greatly appreciated.

---

### Post by maestrobwh1 on 2007-06-15
Wow... this is happening to me too.  Drive seems okay when in use but when the monitor shuts off after15 minutes, the drive just goes nuts.  I can get back in, although when left for a long time, it can lock the machine.  2GB ram and athalon xp 2.1 ghz.  Shouldn't be doing that.

---

### Post by maestrobwh1 on 2007-06-15
You running kerry beagle?  It seemed to cause my hd to go nuts when I accidentally added a folder that I should not have (usr)  yikes.  I emptied the optional folders and just let it index my home folder and it went to somewhat normal.

---

