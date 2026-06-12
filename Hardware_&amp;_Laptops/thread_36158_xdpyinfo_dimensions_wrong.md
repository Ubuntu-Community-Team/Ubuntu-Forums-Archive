---
title: "xdpyinfo dimensions wrong"
date: 2005-05-22
forum: Hardware &amp; Laptops
---

### Post by rhy7s on 2005-05-22
Got a Compaq N800v with a 15" SXGA+ screen. I've been trying to enter the displaysize of 304 228 (the measured size and also 4:3) in xorg.conf but xdpyinfo still reports 307 330. Probably finicky, but it just annoys me that it isn't precise and it isn't 4:3.

Don't really know where it's getting these dimensions from but I tried commenting out the Load ddc module and adding Option NoDDC to device but that didn't do anything.

I assume something automatic is overriding these edits to xorg.conf, but what?

---

### Post by jonrkc on 2005-05-23
Here is the relevant section from my own (desktop) xorg.conf file.  I had to add "DisplaySize" myself by hand.  I got the dimensions from the owner's manual that came with the monitor.  kdpyinfo reports the screen size accurate to within one millimeter, which is good enough for me.  

The modeline that concludes the section I also put in by hand: I obtained it by running xvidtune.  My display was shifted slightly to the right even with auto-adjust on the monitor itself.  With xvidtune I nudged it to the left and applied that modeline and afterward the display has always been perfectly centered.  

It is possible to mess things up with xvidtune, so care is needed, but it can be useful.

I hope typing in the DisplaySize parameter will fix your problem for you.

```

Section "Monitor"
        Identifier      "VL 1916"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
        DisplaySize     376.3 301       
   ModeLine "1280x1024"   108.00   1280 1332 1444 1688   1024 1025 1028 1066 +hs
ync +vsync

```

---

### Post by rhy7s on 2005-05-26
Yeah, I have DisplaySize set to 304 228 but that's not what xdpyinfo is reporting.

---

### Post by jonrkc on 2005-05-26
Hmm.  I read the man page for xdpyinfo and also the ones it suggested, and I'm out of ideas, sorry to say.  Is your display behaving OK in terms of usability under X?  If there's something that appears not quite right about it, maybe you could post about that and somebody else would get a clue from it.  Otherwise, I wish I could help but seemingly can't at this point.

---

### Post by jonrkc on 2005-05-29
I found something that might fix your problem.  Look at
[http://www.x.org/X11R6.8.2/doc/chips3.html](http://www.x.org/X11R6.8.2/doc/chips3.html)
and the option "FixPanelSize."  Sounds to me like this might be what your machine requires.

---

### Post by rhy7s on 2005-06-04
Thanks for the follow-up, just got back and saw your message. I'm just trying to track down what the correct modeline would be to use in conjunction with this option, can you point me  in the correct direction by any chance? Panel is the SXGA+ option on the Compaq N800v.

---

### Post by jonrkc on 2005-06-04
[QUOTE=rhy7s]Thanks for the follow-up, just got back and saw your message. I'm just trying to track down what the correct modeline would be to use in conjunction with this option, can you point me  in the correct direction by any chance? Panel is the SXGA+ option on the Compaq N800v.[/QUOTE]
 I got my modeline by using xvidtune.  It needs to be used with caution, as witness the warning box that displays and has to be checked "OK" before the program even lets you use it.  But I've used it many times and never damaged anything yet.  The modeline I finally got has caused my display to be correctly centered for the first time (even the hardware "auto adjust" built into the monitor couldn't do it).  It also seems to have made my display sharper-looking than the monitor's default adjustment.

You just run xvidtune and nudge your display to the correct position on the screen (if necessary) or just leave everything alone, either way--and select "show" and it will write its modeline to the terminal you started xvidtune from.  Then you can cut and paste that into the appropriate place in the xorg.conf file.  Just back up the xorg.conf file first so you can restore it in case you find out it's not going to work after all.  (In fact, I always keep a copy named xorg.conf.good or xorg.conf.this_one_works or something like that, for that very purpose.)*

Put that in plus, I guess, the option "UseModeline" (though I didn't need this one) and "FixPanelSize" (which is the one that caught my eye on that page in regard to your problem).

Then be sure to report back if it worked!  I hope it does.

-----
* I found out recently that some program or process--I don't know what--is capable of removing the permission section for direct rendering from the xorg.conf file, thus disabling direct rendering.  I've had to put it back in manually two or three times.  So I imagine other undesirable changes could also be made by programs without my knowledge, and having a copy of an xorg.conf that I know works well, can be valuable then, too.

---

### Post by rhy7s on 2005-06-05
OK, I'll have a crack at it. I've just been mucking around and noticed that when I comment out the DisplaySize option the reported dimensions are 301x232 (vs the 307x230 that is reported when I specify 304x228).

---

