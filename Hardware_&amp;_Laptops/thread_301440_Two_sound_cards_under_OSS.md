---
title: "Two sound cards under OSS"
date: 2006-11-17
forum: Hardware &amp; Laptops
---

### Post by stuart.crouch on 2006-11-17
Hi

The basic premise of this request for help is that I have two soundcards, and I cant get linux to settle happily on the one I want. Infact my current situation after some fiddling is both humourous and annoying.  But first some history on why it has to be the way I've done things

I play Eve-online.  It works via WINE.  The repository version of WINE crashes when I try to set the sound, so I compiled it from source (and wrote a howto on it).  Compiling from source only lets me choose OSS as my sound source in winecfg.  I then went into ubuntu settings -> preferences -> sound and set everything to use OSS.

This worked (yey for me!) and I had system sounds, and eve sounds, and music from amarok and it was "all good(tm)".  Then I rebooted.  The sound from WINE stopped working. I followed the sound configuration guide on these forums, telling everything to use my santa cruz plug in soundcard, rather than the on-board sound.

This worked (yey for me!), until I rebooted.  Now I had no sound at all.  I plugged the speaker cable into my on-board card and I had sound again (yey for me!)... until I rebooted.

And this is my problem, each time I boot up linux picks the other soundcard as the one for OSS sound ](*,) . eg it will always go-

1 onboard sound
2 santa cruz
3 onboard sound
4 santa cruz
5 onboard sound
6 santa cruz
7 onboard sound
8 santa cruz

So how do I tell the system to 

1) Ignore the onboard sound (Im thinking of the disable/ignore hardware option in windows) 
or
2) Tell linux to always use the santa cruz for everything 
or 
3) Configure OSS to always use the santa cruz (I can find no documentation on how to configure OSS using google)

I have no idea what you'd need to know for this, so ask for configuration files or console dumps and I'll provide them as needed.

Thanks
--
Stuart

---

### Post by DeusEx on 2006-11-17
[http://ubuntuforums.org/showthread.php?t=178661](http://ubuntuforums.org/showthread.php?t=178661)

good luck ;)

---

### Post by stuart.crouch on 2006-11-18
Excellent. I edited the alsa-base and added the two snd- modules I've been messing with.  I rebooted twice and it stayed on the santa cruz card. Thanks for your help.

---

