---
title: "Sabayon Linux 3.3 Mini-Edition is here!"
date: 2007-03-25
forum: Gentoo and derivatives
---

### Post by RAV TUX on 2007-03-25
You can get the torrent here:

[http://linuxtracker.org/torrents-details.php?id=3810](http://linuxtracker.org/torrents-details.php?id=3810)

---

### Post by LookTJ on 2007-03-25
that link is 64bit version

this is the [x86 version](http://linuxtracker.org/torrents-details.php?id=3808)

---

### Post by igknighted on 2007-03-26
Using the mini now... thank god this is here :).  I love sabayon but the DVD version is just too slow.  Mini is where its at.

PS, thoughts on the theme?  I'm not a big fan.  Why not add the red/black fade as an image to put on the panels.  Now that it's part of the background I can't move my panels to the side without it looking really bad.  Plus with the custom Beryl caps they used and the black background w/ no skydome its a bit of a black hole.  Overall its nice, I like dark themes, but this one seems overboard.

---

### Post by RAV TUX on 2007-03-26
> **igknighted said:**
> Using the mini now... thank god this is here :).  I love sabayon but the DVD version is just too slow.  Mini is where its at.

PS, thoughts on the theme?  I'm not a big fan.  Why not add the red/black fade as an image to put on the panels.  Now that it's part of the background I can't move my panels to the side without it looking really bad.  Plus with the custom Beryl caps they used and the black background w/ no skydome its a bit of a black hole.  Overall its nice, I like dark themes, but this one seems overboard.I usually just customize everything anyway

---

### Post by mips on 2007-03-26
> **igknighted said:**
> Using the mini now... thank god this is here :).  I love sabayon but the DVD version is just too slow.  Mini is where its at.

PS, thoughts on the theme?  I'm not a big fan.  Why not add the red/black fade as an image to put on the panels.  Now that it's part of the background I can't move my panels to the side without it looking really bad.  Plus with the custom Beryl caps they used and the black background w/ no skydome its a bit of a black hole.  Overall its nice, I like dark themes, but this one seems overboard.

Personally I prefer the previous theme. I find this one to morbid.

---

### Post by WalmartSniperLX on 2007-03-26
ahh thanks for posting :D I remember coming across Sabayon at distrowatch but forgot what it was called. Call me a NIX noob :D

---

### Post by FuturePilot on 2007-03-27
> **mips said:**
> Personally I prefer the previous theme. I find this one to morbid.
Indeed. A little too much black. The black does look nice it's just that there's too much of it. Overall though I think it's an improvement over the last version. It's noticeably faster at boot up and even running programs from the live CD they all launched extremely fast. The only thing is that I tried it on 2 different computers and it couldn't get the screen resolution right:( I'm sure it's a matter of just tweaking xorg.conf a bit but that's a little more difficult on the live CD.

---

### Post by .aku on 2007-03-27
> **FuturePilot said:**
> The only thing is that I tried it on 2 different computers and it couldn't get the screen resolution right:( I'm sure it's a matter of just tweaking xorg.conf a bit but that's a little more difficult on the live CD.

Have you tried pressing F5 at the boot, and using the 'cheatcode' (all of which are found in the Sabayon wiki)
```
res=1280x800 
```or whatever your resolution is..
Worked for me..

Didn't like 3.3 though... 
The DVD is bloated, and I struggled for too many hours to get X running with the miniEdition (no screens found), so it was straight back to old trusty **Arch**. <3

//aku

---

### Post by FuturePilot on 2007-03-27
Hmmm, now I'm going to have to give that a try:lolflag:

---

### Post by .aku on 2007-03-27
> **FuturePilot said:**
> Hmmm, now I'm going to have to give that a try:lolflag:
Which one, the cheatcode or Arch ? :lolflag:

//aku

---

### Post by .aku on 2007-03-30
Edit

---

### Post by mips on 2007-03-30
I [COLOR=Red]**STRONGLY**[/COLOR] suggest mini users run the the following:

```
/scripts/emerge-kernel.sh
```

The mini edition comes without kernel sources and at times emerging stuff will fail on you. The above script will save you endless hassles.

---

