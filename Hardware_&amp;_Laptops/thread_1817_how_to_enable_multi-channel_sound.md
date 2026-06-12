---
title: "how to enable multi-channel sound?"
date: 2004-10-23
forum: Hardware &amp; Laptops
---

### Post by negativ on 2004-10-23
I have a Turtle Beach Santa Cruz (Cirrus Logic CS4630) with a 4.1 speaker setup.  So far, I can only get sound from the front speakers.

I don't care if I get "true" surround sound, but I would at least like the rear channel to work when playing CDs and MP3s, etc.  I would be perfectly happy if the rear channel was playing the same thing as the front channel, but right now I get nothing.

Any help would be appreciated.

---

### Post by negativ on 2004-10-24
anyone?   :-k

---

### Post by claymore on 2004-10-25
If you get a player that will use alsa (xmms is recommended), you can set the engine to alsa, then use the alsa control panel in your volume control to echo the stereo in the rears.

---

### Post by negativ on 2004-10-25
I'm using xmms with ALSA, but I don't see anything in the ALSA section of the volume control that has anything to do with the rear channel.  I've unmuted and cranked the volume on everything I have available, and still no rear channel.

---

### Post by tambooki on 2004-10-25
I believe the problem is the fact that mp3s, etc are generally only stereo sound, so alsa will only play them through 2 speakers. However, this page on the alsa pages has info on duplicating the sound to the back speakers:
[http://alsa.opensrc.org/index.php?page=SurroundSound](http://alsa.opensrc.org/index.php?page=SurroundSound)
Hope it's helpful.

---

### Post by claymore on 2004-10-25
[QUOTE=negativ]I'm using xmms with ALSA, but I don't see anything in the ALSA section of the volume control that has anything to do with the rear channel.  I've unmuted and cranked the volume on everything I have available, and still no rear channel.[/QUOTE]

If you right click on the volume control icon on the taskbar and choose "open volume control", you will get a page of sliders.  Above the sliders is the ALSA mixer, which should have an option somewhere that says "duplicate front".  Make sure you turn that off when you have sounds coming from a surround source, though, or you won't be getting the rear information.

---

### Post by BugsyMalone on 2004-10-26
I have the same card with the same problem. I've got AlSA installed and I looked at all the sections, but there's not one that says "duplicate front."

---

### Post by negativ on 2004-10-27
[QUOTE=BugsyMalone]I have the same card with the same problem. I've got AlSA installed and I looked at all the sections, but there's not one that says "duplicate front."[/QUOTE]

Yeah, no "duplicate front" here, either...

Also, I tried the stuff at [http://alsa.opensrc.org/index.php?page=FAQ028](http://alsa.opensrc.org/index.php?page=FAQ028) and it sort of worked, but it wasn't useful because the rear channel was about 1 second behind the front channel.

---

### Post by sparky on 2004-12-06
Hi, this is sort of an old thread, but it applies to my problem so here goes.  I only get sound through one of my 2 speakers, and yes, I have checked all   the sliders on the sound mixer.  Have any of you fixed your sound problems yet?

Cheers,
Sparky

---

### Post by Berti on 2005-04-01
I've solved the problem for me by launching alsamixer in a console
and enabling ("m" to unmute & the arrows to raise the volume) Surround, center & duplicate.

---

### Post by Whiffle on 2005-04-01
Mine doesn't have a duplicate? 

The reason is because TB won't give linux any decent drivers, the ones we have have been more or less reverse engineered and they aren't perfect yet.  MP3's won't do surround because they are stereo, although you can get them to mirror the sound to the back with some creative hacking.  I've never tried though (only 2 speakers).  If you look at the mplayer audio config in the alsa section however, there are options for Surround40 and Surround51.  I've gotten them to work somewhat, but they really bog down my computer.

There is thread after thread about this issue on the gentoo  forums.  Turtle Beach doesn't plan on issuing linux drivers either, so AFAIK the easiest way to get surround is to get an audigy.  I still love my TB though, it sounds great, i got it for 12 bucks, and it hasn't fried like the audigy i had before it.

---

