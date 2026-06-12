---
title: "Game problem - Lbreakout2"
date: 2008-07-25
forum: General Help
---

### Post by txHarleyMan on 2008-07-25
Hi all,

I cannot seem to figure this out.  My video card is an Nvidia 8600GT.  I installed the current driver using Envy.  Everytime my wife tries to play lbreakout2 the game will freeze after 10 minutes or so.  Anyone know how to resolve this or point me in the right direction?

Thank you.

Mike

---

### Post by DirtDawg on 2008-07-26
> **txHarleyMan said:**
> Hi all,

I cannot seem to figure this out.  My video card is an Nvidia 8600GT.  I installed the current driver using Envy.  Everytime my wife tries to play lbreakout2 the game will freeze after 10 minutes or so.  Anyone know how to resolve this or point me in the right direction?

Thank you.

Mike

Try running lbreakout2 from a terminal. That should provide an error message when it crashes that you can post here and, hopefully, provide enough info so maybe someone can help you out.

---

### Post by txHarleyMan on 2008-07-26
Well.. I started it for her from Terminal, it froze and no errors reported in terminal.  Odd.

---

### Post by txHarleyMan on 2008-07-28
Never mind.  Went back to Kubuntu where it works just fine.

---

### Post by PerfectReign on 2009-08-23
My mom's computer has - apparently - the same issue. She's been complaining for some weeks. Pretty much since I upgraded her from openSUSE 10.1 (KDE) to Ubuntu (GNOME) 9.04.

You can run the game for ten or twenty minutes, then it simply goes to the screen "PAUSE" and does not allow for further game play. I ran it from the CLI to see what I got. 

I've included a screen shot and a command line listing.

Any ideas??


[FONT=Courier New]francie@francie-desktop:~$ lbreakout2
LBreakout2 2.5.2
Copyright 2001-2005 Michael Speck
Published under GNU GPL
---
Looking up data in: /usr/share/games/lbreakout2
Looking up custom levels in: /home/francie/.lgames/lbreakout2-levels
Loading theme 'AbsoluteB'
Saving highscore chart in: /var/games
Yexter v1.00: 40 levels
Time: 151.77, Frames: 14507 -> FPS: 95.58
Yexter v1.00: 40 levels
ERROR: cannot open slot 0!
Time: 787.65, Frames: 75146 -> FPS: 95.41
!FREAKOUT! v1.00: 1383 levels
ERROR: couldn't delete file /home/francie/.lgames/lbr2_save_0
ERROR: cannot open slot 0!
Time: 146.65, Frames: 13603 -> FPS: 92.76
Arcade v1.00: 13 levels
ERROR: couldn't delete file /home/francie/.lgames/lbr2_save_0
ERROR: cannot open slot 0!
Time: 225.25, Frames: 21023 -> FPS: 93.33
ERROR: cannot open slot 0!
Arcade v1.00: 13 levels
Time: 16.14, Frames: 1472 -> FPS: 91.19
Bombs v1.00: 25 levels
ERROR: cannot open slot 0!
Time: 208.10, Frames: 19472 -> FPS: 93.57
CalendarFun v2.30: 16 levels
First chart query for 'CalendarFun'. Creating this chart.
Time: 328.25, Frames: 19091 -> FPS: 58.16
Color v1.00: 40 levels
Time: 7.03, Frames: 476 -> FPS: 67.69
Family v1.00: 20 levels
First chart query for 'Family'. Creating this chart.
^CTime: 701.79, Frames: 65572 -> FPS: 93.43
Client finalized
GUI finalized
Audio finalized
STK finalized
SDL finalized
francie@francie-desktop:~$ [/FONT]

---

### Post by elhamdilulah on 2009-11-18
I turned off the screensaver, and now it works fine.

---

### Post by PerfectReign on 2009-11-18
Thank you. I had her do that. I will report back results.

BTW, it was a bit difficult - in GNOME - to turn off the screen saver. I was used to right-clicking the desktop in KDE and going from there.

---

