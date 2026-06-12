---
title: "No sound ( 

No sound - vt8233/A/8235/8237 AC97 Audio"
date: 2005-04-11
forum: Hardware &amp; Laptops
---

### Post by jcdotnet on 2005-04-11
After install hoary , i can not hear sound  (vt8233/A/8235/8237 AC97 Audio  , on board sound )

But it work on warty.

---

### Post by hiruzzo on 2005-04-11
Same problem! It can see the via 8233 and it uses alsa to make it work, there is even the volume window working, but still no sound!! what can we do about it? :-x  :???:

---

### Post by cabu on 2005-04-11
Bring up a terminal and type the following:

sudo alsamixer

Then mute "IEC958 Capture Monitor"

Then quit alsamixer and type the following in a terminal:

sudo alsactl store

That should fix you up.

Edited to change unmute to mute

---

### Post by jcdotnet on 2005-04-12
Thank you very much.  Now it's work !

---

### Post by bobterri on 2005-04-16
I don't have "IEC958 Capture Monitor" as an option to mute or unmute in alsamixergui.  Any suggestions anyone?

---

### Post by unempirical on 2005-04-16
I have the same problem.  My sound card is an Avance AC97 for VIA.  Alsamixer says it's VIA 8235.  I don't get sound from any program, including the Multimedia Systems Selector test for ESD, ALSA, or OSS.

I have no "IEC958 Capture Monitor" option in alsamixer.  I do have "IEC958" and "IEC958 Output", which I have muted.  I also have "IEC958 Playback AC97-SPCA", which has no mute option.

After running "killall esd" in a root terminal, I get no output from "lsof /dev/bsp" or "lsof /dev/snd/*".  Still no sound from either ALSA or OSS in Multimedia Systems Selector.  (Predictably, ESD produces an error after the ESD daemon has been killed.)

I have sound working in Sarge.  Any idea how to get it to work in Ubuntu Hoary?

---

### Post by Magneto on 2005-09-07
[QUOTE=unempirical]I have the same problem.  My sound card is an Avance AC97 for VIA.  Alsamixer says it's VIA 8235.  I don't get sound from any program, including the Multimedia Systems Selector test for ESD, ALSA, or OSS.

I have no "IEC958 Capture Monitor" option in alsamixer.  I do have "IEC958" and "IEC958 Output", which I have muted.  I also have "IEC958 Playback AC97-SPCA", which has no mute option.

After running "killall esd" in a root terminal, I get no output from "lsof /dev/bsp" or "lsof /dev/snd/*".  Still no sound from either ALSA or OSS in Multimedia Systems Selector.  (Predictably, ESD produces an error after the ESD daemon has been killed.)

I have sound working in Sarge.  Any idea how to get it to work in Ubuntu Hoary?[/QUOTE]
 thank you for this reminder

---

### Post by Onajourney on 2006-08-16
finally threw out windows
New at this
hi hope this helps, I had the same problem as above but i went in to alsa mixer via the speaker icon on desktop. Once in there in the playback tab I had added some other options via the preferences which displayed the following.
VIA DXS
VIA DXS 2
VIA DXS 3
VIA DXS 4
they were all muted, when i unchecked VIA DXS 2 
sound nearly blew me out of seat
 :D 
hope it helped it did me 
me mobo is VIA KM400, 8237 chipset based
with latest ubuntu 6.06 LTS. luvit

---

### Post by ciprian on 2006-08-20
I have the same problem, no sound on ASRock/KM266Pro/8235 motherboard, in Ubuntu or Knoppix

---

### Post by Frankoh on 2006-09-08
I have the same problem with complecations.  I have a Trios machine, meaning it has 3 separate hard drives which boot up separatly and make it look as though there are 3 different machines.   I have XP Pro on the first HD, Xu
xubuntu 6.6 on the middle HD (this one) and Mepis 6.0 on the last one.
XP Pro and Mepis have sound and came up right out of the box.   I cannot get the sound on this one.   I opened the sound in the Settings Manager and saw where it was showing "Default" and then all of the boxes listed were checked.
The second choice was #0 Via 8237.  I have tried both settings to no avail.

I am running a MACHSPEED motherboard with on-board audio.   What do I need to do?
BTW I am BRAND NEW to Linux based with my only exposure is a week of Mepis.
I am looking for an easy load to put on machines I build for Not-for-profit 
(Like senior citizen trainingm, churches, etc) and it need to be solid.

Xubuntu looks solid enough and runs well otherwise (after I figured how to set up the printer) but some may be blind and we will need sound.

Regards
Frankoh

---

### Post by geopandas on 2006-09-29
I repair, "not sound" problem

open terminal...

> sudo asoundconf list     <-write this
Names of available sound cards:
camera
UART
modem
V8235   <- bingo, my soundcard :) 

now write this

> asoundconf set-default-card V8235

Ready ! :D

---

### Post by GalloGlas on 2007-02-10
I also have VIA 8235 chipset of AC97 onboard sound.  

Every solution I have seen involved unmuting channels.  This simply does not work.  

Every channel is unmuted and turned up.  I also do not have that IEC958 Capture monitor in alsamixer. 

The card is detected, and set as default.  

But no sound comes out.  I have double checked speakers and the work.  I have also double checked the port they are plugged in to.  That as well is correct.  

The sound card is operational in windows.  

I have been reading that this may be a problem with kernel past 2.6.10.  

Anyone know how to get this working?

---

