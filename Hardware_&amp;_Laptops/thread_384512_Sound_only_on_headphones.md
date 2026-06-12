---
title: "Sound only on headphones"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by dw09577 on 2007-03-14
OK, so I know there's a sound thread every 20 minutes on here, but this one seems different.  Hopefully it's easy.

Dell Inspiron 700m w/ Edgy

I got Beryl installed and working great ([http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60#Beryl_-_fancy_3D_desktop)](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60#Beryl_-_fancy_3D_desktop)), and the sound was working well over the weekend.  I was playing internet-based games and using the Beryl cube, sound was great.  I shut the laptop off Sunday night...first time being shut down or rebooted since installing Beryl.

I bring the laptop to work, boot it up, and not only does the cube function in Beryl not work any more, but the only way I can get the sound to come out is through the headphone jack.  The sound from there is perfect, no problems, but the onboard speakers are dead.

I uninstalled Beryl with Synaptic to see what would happen, no change.  I went through the entire sound troubleshooting sticky twice with no change.

I downloaded a fresh 6.10 ISO and booted into it as a LiveCD, same problem - no sound from speakers, but when I plug headphones in, sound is great.

This makes me think it's not Beryl, but maybe the xorg.conf modifications for Beryl that broke the sound?
I've also checked in the BIOS, no options relating to sound.

I've only been on Linux/Ubuntu for a few weeks, so I need help.  :confused:



edit: no change when loading the .17-10 kernel instead of the .17-11.  No change when loading XGL instead of GNOME.   ...and now my WXGA resolution is screwy...  it was OK with the 915resolution fix before...  getting a little frustrated, hope I don't have to rebuild this weekend...  :(

---

### Post by dw09577 on 2007-03-16
OK, for anyone with the problem of no sound through speakers, but sound through the headphone jacks on a Dell 700m (or maybe other Dell laptops) stop messing with Ubuntu and check out the speaker cables.  Apparently there is a major flaw with the way the speaker cables are run from the motherboard to the speakers, resulting in broken speaker wires in the area of the right hinge on the laptop screen housing.  The wires literally break after a year or two of use.  [Apparently this is pretty common with the 700m's.]("http://www.google.com/search?q=dell%20speaker%20wires%20broken%20700m")

If they've recently stopped working, try playing some music and closing the lid about 80-90% of the way shut.  The broken ends of the speaker wires usually will make contact, and you'll hear the sound.  Open the laptop up more than that, ad the wires don't touch any more, so no sound.

If your laptop is under warranty, make Dell fix it, but if you are out of warranty or can't wait to have them fix it, there's [a decent write-up here on how to patch the wires yourself]("http://64.233.167.104/search?q=cache:s9g7lEcajrkJ:www.lukemiller.org/journal/2006/06/broken-speaker-wires-on-dell-700m.html+%22+Broken+speaker+wires+on+a+Dell+700m%22&hl=en&ct=clnk&cd=1&gl=us").  It's pretty ugly, but it gives you the idea of what needs to be done.  I'm sure it can be done cleaner.

---

### Post by scompany on 2007-07-23
I have the same problem with Toshiba notebook... I sound only works on headphones. It's not hardware problem because sound works well in windows. I tried changing all switches but it doesn't help. While I was on Edgy Eft, laptop speakers worked normally...

Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller

---

### Post by scompany on 2007-07-23
I found fix for intel sound card.

This is fox for all of you who have** laptop / notebook** with** intel sound card** and are able to get **sound only through the headphone jack**.

Go to terminal and type:
> sudo gedit /etc/modprobe.d/alsa-base

In that file at the end copy and paste this:

> options snd-card-0 enable=1 index=0 model=basic
options snd-hda-intel enable=1 index=0 model=basic

Save!

If still doesn't work, run gnome-volume-control and go to Switches tab. Now try to check/uncheck Speaker and Headphones.

---

### Post by louaym on 2007-08-13
thank you ¨scompany¨ your tip help my problem.

now I have sound coming from my laptop speaker too (Toshiba-Tecra-A8_ Intel sound card


Louay

---

### Post by dsmithpdx on 2007-08-16
Thank you so much scompany!  That worked on my Sony Vaio PCG-TR3A.  I think that was my only remaining issue with my new Ubuntu install.  Woohoo!!!

Doug

---

### Post by clio66 on 2007-08-24
thanks DW for the helpful post

my problem was also the broken wires, which was identified by (a) confirming sound could come through headphones, and (b) tilting screen down slightly to make sound come through internal speaker

went through several other diagnostics, troubleshooting, setting adjustments, etc.  apparently the computer is not designed to tell the user when the speaker wires are broken

---

### Post by Metaljaz on 2007-08-28
thanks for the post. It worked for me as well. Dell XPS Intel 82001EB/ER (ICH5/ICH5R).
The only thing is the volume button on the laptop has no effect on the volume. I have to use the volume control on the panel. This is manageable because i benefit from my subwoofer.
thanks

---

### Post by jorge87 on 2008-06-28
thanks for the tip, I spent nearly a whole day looking at the volume control settings and the alsa drivers, etc...just to find out that the speaker wires in my 700m are broken!  (i tilted the screen like you suggested and the sound played)

---

