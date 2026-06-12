---
title: "3th soundcard and still no working mic"
date: 2005-10-10
forum: Hardware &amp; Laptops
---

### Post by klausi banausi on 2005-10-10
hello folks,
since weeks I'm trying to get the microphone working but without success.
the onboard sound card does not work at all - then I tried a card with an Ensoniq Es1370 chip. here I get sound but the mic does not work. now I'm trying a terratec aureon fun 5.1 and still nothing. please help I have no idea how I could fix this problem - thanks klaus

lspci | grep -i audio
0000:00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

cat /proc/asound/cards
0 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
C-Media PCI CMI8738-MC6 (model 55) at 0x9800, irq 17

---

### Post by Zelut on 2005-10-10
I can't get a mic to work on two of my Ubuntu machines.  If someone has a solution to this I sure would appreciate it as well.  This is the ONE missing link between a dual-boot XP and getting rid of those shackles altogether.

---

### Post by kpturvey on 2005-10-10
[QUOTE=kuyaedz]I can't get a mic to work on two of my Ubuntu machines.  If someone has a solution to this I sure would appreciate it as well.  This is the ONE missing link between a dual-boot XP and getting rid of those shackles altogether.[/QUOTE]

I too have the same problem.  When I run lspci | grep sound I nothing, but if I run lspci | grep Audio I get the following:

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

I'm running a Inspiron 5100 from Dell.  

What's your configuration?

---

### Post by kpturvey on 2005-10-10
OK, I found the problem with my configuration.  The settings under alsa have
to be just right.  Here's what I did to get things to work:

Run alsamixer
Unmute all the outputs by hitting "m"
Hit tab to go the capture settings
Highlight the "Mic" setting my using the arrow keys.
Hit space to enable the microphone.
Highlight the "Capture" setting using the arrow keys.
Hit space to enable capture (note that just because you have volume bar
	here doesn't mean it is enabled.  
Hit escape.  

To test it out use the following command:

arecord -f cd test.wav

It should work.

---

