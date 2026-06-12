---
title: "Screen tearing when watching DVDs using VLC"
date: 2008-10-09
forum: General Help
---

### Post by belovedmonster on 2008-10-09
I've been using different flavours of Linux without compiz turned on for about a year and I've never had any problems watching DVDs using VLC. But now I'm using Ubuntu with Compiz on I'm finding I'm getting screen tearing.

If I turn Visual Effects to None the screen tearing goes away, so I know this is a Compiz issue. 

Is screen tearing likely to be a hardware problem, given that I am using an old computer? AMD XP Athlon 1.8Gz, 1GB Ram, 64mb Geforce4 MX.

---

### Post by billgoldberg on 2008-10-09
> **belovedmonster said:**
> I've been using different flavours of Linux without compiz turned on for about a year and I've never had any problems watching DVDs using VLC. But now I'm using Ubuntu with Compiz on I'm finding I'm getting screen tearing.

If I turn Visual Effects to None the screen tearing goes away, so I know this is a Compiz issue. 

Is screen tearing likely to be a hardware problem, given that I am using an old computer? AMD XP Athlon 1.8Gz, 1GB Ram, 64mb Geforce4 MX.

In vlc, try selecting a different video output.

It could be that it's output is set to opengl and opengl and compiz don't play well together.

I suggest you try either "X11" or "XVideo".

---

### Post by medic2000 on 2008-10-09
Hmm in Compiz there is a thing `Detect Refresh Rate` Change this and write it manually. And look for Vsync in Compiz

---

### Post by belovedmonster on 2008-10-09
> **billgoldberg said:**
> In vlc, try selecting a different video output.

It could be that it's output is set to opengl and opengl and compiz don't play well together.

I suggest you try either "X11" or "XVideo".

It changed the way the tearing looked, but didn't eliminate it. 

I should mention as well that if I play the video full screen then there is no tearing, it is only when I bring up the controls again that it tears.

---

### Post by belovedmonster on 2008-10-09
> **medic2000 said:**
> Hmm in Compiz there is a thing `Detect Refresh Rate` Change this and write it manually. And look for Vsync in Compiz

I don't know how to do that. :(

---

### Post by belovedmonster on 2008-10-09
Just an update to say that I've downloaded some videos to try and they seem to be tearing as well, so its not just a DVD video issue.

---

### Post by belovedmonster on 2008-10-09
> **medic2000 said:**
> Hmm in Compiz there is a thing `Detect Refresh Rate` Change this and write it manually. And look for Vsync in Compiz

I found the option to change this the detect refresh rate but I'm not sure what to change it to. It's set to 50 at the moment, i turned it up to 200 and it didnt make a difference. Is Vsync the same as Sync to Vblank? if not then I dont know where that option is.

I thing I did notice is the Output says 640+480+0+0 is this supposed to represent my resolution or something? :confused:

---

### Post by medic2000 on 2008-10-09
If you are using a laptop you should do it 60 not 50 :) Default it makes it 50 and it was causing slowness. Maybe it is a bug in Compiz. Say activate the Sync to Vblank in Compiz Config Setting Manager.

---

### Post by belovedmonster on 2008-10-10
There seems to be a lot of people reporting similar problems when using nVidia cards (which i've got). There is a bug on launchpad. I think my only solution is to wait for the bug to be fixed, but I think that is nVidias responsibility so it might be a while. Any chance of there being an updated driver in 8.10 ?

---

### Post by chapterthree on 2008-10-11
I had this issue after a fresh install of Ibex 8.10 Beta and Compiz 0.7.8.  I was able to fix this by doing the following:
[LIST]
[*]In Compiz Settings Manager -> General Options -> Display Settings enable the checkbox for 'Sync to VBlank'
[*]Also under Display Settings uncheck the box for 'Detect Refresh Rate' and set the Refresh Rate to 100
[/LIST]

Solution found in the following thread:
[http://ubuntuforums.org/showthread.php?t=572906](http://ubuntuforums.org/showthread.php?t=572906)

Hope this helps somebody else.

---

### Post by stinger30au on 2008-10-12
there could be a number of things causing this. i have seen this caused by incorrect video codec being used. happened to me


go to the add/remove and search on avidemux (going by memeory here, not at home to test) and install it. restart pc and try again. 

worked for me

---

### Post by gnulogic on 2008-10-12
turn off compiz by right clicking on the desktop - change desktop background - visual effects tab and put to none.

---

