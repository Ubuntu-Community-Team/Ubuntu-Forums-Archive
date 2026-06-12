---
title: "Deactivate my soundcard!"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by coral on 2007-01-21
Hello, i have two soundcard. One Audigy ZS 2 and a Intel Onboard hidef piece of junk.

Having 2 sound cards causes problems sometimes, so i think the best would be to deactivate the intel piece of junk and just run on the Audigy. How do i do this?

---

### Post by sgx on 2007-01-21
enter your bios by pressing key or combo indicated during bootup, its usually del or F1
navigate bios screens by arrowkeys, tab, spacebar etc...
-go slowly- read the onscreen promps, and onscreen directors, no hurry, one of the several
pages will have the option to enable/disable sound, feel free to become familiar with all
the pages, and options, and follow the prompts to save and exit, often F10 will yield that
option...it may look like primitive dos, just study the option, and note on paper any changes
you make. For booting Live cd/dvd distros, a boot options, boot priority type of page is
in there, put cd or dvd ahead of your harddisk, for Knoppix, Dynebolic, Mepis, Suse etc
live distros to start your computer...hope this helps...mainly, go slow, and read the options
carefully...

---

### Post by coral on 2007-01-21
Nono, i dont want to deactivate it that way. I am using it in windows as a secondary soundcard linked to the other with some special ASIO driver i managed to got hold of..
And yes, i am Quite familiar with bios.

What i am looking for, is a way to just tell the kernel or ubuntu itself to not load the drivers at all and just let the soundcard be.

---

### Post by folteanu on 2007-01-25
Same problem here. I have a sound card  Creative Labs SB Live! (emu10k1) and a TV tunner Genius (SAA7134). After I've installed Kubuntu 6.10, my primary sound card became the tv tunner. I've fixed my problem using method 2.

You can try one of the following:

Method 1 (for a specific user)
a) (as user)> asoundconf list
[ that will list you your available sound cards ]
SAA7134
Live

b) (as user)> asoundconf set-default-card Live
(for me, Live is  Creative SB LIve! - the one I want as default)
(Obs:from man asoundconf:
        asoundconf configures the ALSA library for the user.  It does  this  by
       reading the values of parameters from and writing the values of parame&#8208;
       ters to the special file .asoundrc.asoundconf in the user’s home direc&#8208;
       tory.  The .asoundrc.asoundconf file should not be edited by hand!

c) reboot

Method 2: (for every users)
a) added in   /etc/modprobe.d/alsa-base  the following rows

  #Creative
   alias snd-card-0 snd-emu10k1
   options snd-emu10k1 index=0

  #Tv tunner
  alias snd-card-1 saa7134-alsa
  options saa7134-alsa index=1

b) reboot

Now it works fine. I have both sound card working and I can adjust my sound volume with kmix, xmms and tv time.

I took the ideea from  [http://www.linuxquestions.org/questions/showthread.php?t=499520](http://www.linuxquestions.org/questions/showthread.php?t=499520)

---

