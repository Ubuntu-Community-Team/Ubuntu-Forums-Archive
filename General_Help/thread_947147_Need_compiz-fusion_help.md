---
title: "Need compiz-fusion help"
date: 2008-10-14
forum: General Help
---

### Post by spkenny on 2008-10-14
Wasnt sure where to post this exactly, but I am a complete noob at ubuntu and linux.  I am seeing lots of videos on beryl, now called compiz-fusion.  Can anyone direct me on where or how to download the software that creates the effects on the desktop such as a cube, wobbling windows, and flames that appear when closing the windows.  How do I even install this stuff?  Lot of confusion for an ex-windows user, so if anyone can help direct me at all.... By the way, I believe I have the basic version of ubuntu installed, so if I need a different version to do all this, let me know too.

---

### Post by phoenix49 on 2008-10-14
There's generally only two versions of Ubuntu: desktop and server. Probably, you are using desktop version. To enable compiz-fusion first you need to install drivers for your video card. You may already noticed "restricted drivers" applet near your clock. After installing them, go to System -> Preferences -> Appearance. Select Normal or Extra from Visual effects tab.

For more configuration of compiz, install "ccsm" package from Add/remove (Applications menu). Then you'll have extra configuration options available from System->Preferences->Advanced desktop effects settings

---

### Post by alwez_loner_TZ on 2008-10-14
Hello,

You can also go to Synaptic Manager and search for Compiz and then download all the packages.

After you install them you will have to install the video card driver. After which you will find the Advanced Desktop Setting at the Settings and you change it there.

---

### Post by shabs on 2008-10-14
I would also recommend running this handy little script. Not important but tells you more about the hardware compatibility. Its found here:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by rick08 on 2008-10-14
First you need to download compiz and compiz fusion icon from the Add/Remove thing under applications.  After that finishes you need to go to preferences and somewhere in there is appearance and from there you can access the additional compiz effects.  The cube that you see is a little difficult if you are a complete noob.  It took me about 3 hours to figure it out, but if you search the forums you can find how to do it if you cannot figure it out.

---

### Post by spkenny on 2008-10-14
Thanx for the info, some good leads there to do some more digging on how to work all this.  As for my video card, I see no icon next to the clock stating anything about installing drivers for the video card.  Is there somewhere else I need to look?  How do I check the driver for the video?  And I already have gone through the settings for the compiz stuff, although it is a bit confusing.  As far as I can tell everything is installed.

---

### Post by REDace0 on 2008-10-14
If everything runs fine, your card might be supported without restricted drivers. Or maybe you already set it up when you first installed. If Compiz is working, then your video card is working.

---

### Post by SteveNorman on 2008-10-14
right click your desktop, change desktop background>visual effects>set them to extra

then in system>preferences>advanced desktop effects you will see a menu of effects. 

if none of that works you probably need a graphics driver for your vid card.

If that is the case open a terminal and type glxgears

applications>accessories>terminal

then at the prompt $ type```
glxgears
```

tell us what happens please

---

### Post by shredder12 on 2008-10-14
> **shabs said:**
> I would also recommend running this handy little script. Not important but tells you more about the hardware compatibility. Its found here:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)
It was a really good article..i was having a bit of ambiguity about my system compatibility for running compiz..
I m clear with it now..
thanx..

---

### Post by spkenny on 2008-10-14
Ok, first, ran the compiz-check on my system.  everything checked ok except the last check.  But in the explanation on the error, it said the particular error did not mean compiz would not run with the card as the first 4 checks were ok, and only the 5th check an error.  Am I missing some command to run the compiz program?

---

### Post by overdrank on 2008-10-14
> **spkenny said:**
> Ok, first, ran the compiz-check on my system.  everything checked ok except the last check.  But in the explanation on the error, it said the particular error did not mean compiz would not run with the card as the first 4 checks were ok, and only the 5th check an error.  Am I missing some command to run the compiz program?

What is the model of the graphics card? You can find with the command lspci in the terminal and look for VGA.
What was the error from compiz check?

---

### Post by spkenny on 2008-10-14
the card reads as VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev al).  The message that I reported as an error on the compiz check, was actually a 'skip'.  The reason stated for the skipped check was 'Couldnt check the amount of memory on your Nvidia chip'. I will find out what card I have, but I know its a 128 meg card.  Anyone know how good of a card u need to run compiz?

---

### Post by overdrank on 2008-10-15
> **spkenny said:**
> the card reads as VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 AGP 8x] (rev al).  The message that I reported as an error on the compiz check, was actually a 'skip'.  The reason stated for the skipped check was 'Couldnt check the amount of memory on your Nvidia chip'. I will find out what card I have, but I know its a 128 meg card.  Anyone know how good of a card u need to run compiz?

Ok I am using that same card now in my system. Have you installed the drivers for the graphics card, you can look under system, administration, hardware drivers.

---

### Post by spkenny on 2008-10-16
Update: Some time after I installed the nvidia drivers, I installed some games that run on linux.  Shortly after installing the games, my video was streaking, and the system would freeze up.  Assuming I had downloaded a bad program or something, I re-installed my ubuntu.  The glitches started happening once again, right after I selected to use the nvidia accelerated graphics driver for my card.  If I dont have the driver installed, everything runs fine.  This leads me to believe I have a faulty card.  So this leads to my final question on this post.  What card do I look for to get for my system using linux?  As far as I've read, and can see, nvidia is the most compatible.

---

### Post by phoenix49 on 2008-10-16
Intel is best supported, drivers are included in Ubuntu by default.

Nvidia and Ati both has good drivers (though some ati cards, in some specific configuration may not work perfectly). Recently I used Nvidia 6200, and worked perfectly. Now I'm on ATI 3850, which also works flawlessly with restricted drivers from Ubuntu.

---

