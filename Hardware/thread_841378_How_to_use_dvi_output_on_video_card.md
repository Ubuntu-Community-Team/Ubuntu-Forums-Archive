---
title: "How to use dvi output on video card"
date: 2008-06-26
forum: Hardware
---

### Post by Afkpuz on 2008-06-26
I just got an hdmi cable and have an adapter that changes it to dvi.  When I tried booting up with just the hdmi>dvi cable plugged into my high def tv, I get nada.  Yes, the tv is on hdmi input.  Is there something special I have to do to get dvi output?  My system was originally vga out, so I'm thinking that maybe there is a setting somewhere that I can change.  Also, this was a very cheap hdmi cable, so there's a chance it's a bad cable.  So can anyone help?

---

### Post by phidia on 2008-06-26
If you are getting no output check your TV setting for source. There is usually a way to select different inputs. On the sharp aquos for instance there are 6 inputs try selecting a different input # and see if you get a screen.

It may help others to help you if you list the hardware you are using too.


***Off topic; HDMI cable prices purchased locally are absurd. I recently purchased an HDMI cable through one of Amazon's partner businesses. With shipping I paid less than $3.00 yet if I purchased that same cable locally it would cost $40.00
BTW the $3 cable works great.

---

### Post by Afkpuz on 2008-06-26
Here are my specs:

OS: Ubuntu hardy
Video card: 8400 GT (maybe GS, I'm not at that computer right now)
TV: AOC L32W761 32" LCD HDTV  with only 1 hdmi

I'm positive that I had hdmi selected because there is only 1 hdmi plug and the notification showed hdmi input.  I just want to know if there are any settings I would need to change on the computer to get dvi output, since when I installed, I used vga

---

### Post by oldsoundguy on 2008-06-26
You do have to have a DVI or HDMI outlet on your card.  You can not "reverse" a VGA out and turn it into a DVI/HDMI.  Just because you have a DVI input on your set does not mean that you can drive same with a computer set up without software tweaks.

It is a bit more complicated than swapping speakers or such. And sometimes it takes a NEWER video card that supports the toob! (such as an nVida 8600GT .. What I use .. dual DVI outputs.)

Also, unless your card supports dual controlled output, you will be stuck with the clone of your desktop resolution.  So, IF your desktop is a VGA (not digital), the signal sent to the toob will be VGA.

---

### Post by Afkpuz on 2008-06-26
Ok, so where can I change the settings to use the dvi out on my vid card instead of vga out?

---

### Post by phidia on 2008-06-26
> **Afkpuz said:**
> Ok, so where can I change the settings to use the dvi out on my vid card instead of vga out?

Try typing nvidia-settings in a terminal or perhaps you have the applet under System/Administration. I'm guessing you have a monitor to work with on the system while you figure this out.

I know on my older computer w/nvidia and a sharp aquos TV I had to use xvidtune to adjust the screen size, but all I did was plug in the cable and select the correct input-works in both zenwalk and ubuntu, but screen rez isn't exactly perfect-took a lot of playing with because TV's don't use the same resolutions as computer monitors. There are several threads about that in the [multimedia & video section]("http://ubuntuforums.org/forumdisplay.php?f=334").

---

### Post by oldsoundguy on 2008-06-26
The screen settings and card settings are in system> administration. screens and graphics.

Now, you will also have to know the resolution of your television.  Those figures will be in the manual for same.

And, of course, that will become your computer monitor.  (if you only have one output, no way to use a splitter or "y" cord.)

the SPDIF output will also drive a television, but only one with standard aspect ratio (won't do a wide screen).  And that also takes some doing.

You really need to sit down and use Google to find out about what you are attempting to do.  It is NOT an easy thing when you have no clue as to what is what and as to what will or will not work.

Manuals and how to's will be the first thing you need. Plug in your make and model number of the equipment involved.

In the past, I have even had bunches of trouble trying to dual screen on Windows without the proper card(s) and software.

---

