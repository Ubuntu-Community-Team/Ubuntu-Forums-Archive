---
title: "Need soundcard help!"
date: 2007-08-06
forum: Hardware &amp; Laptops
---

### Post by Ub1476 on 2007-08-06
When I try to use XMMS it tells me to configure my soundcard. Amarok just beeps and tells me something is wrong. Although I can hear sound and change the volume, I cannot listen to music trough my PC, and I also noticed  sound from movies on YouTube wont play.

So alright, I downloaded and installed the latest ALSA. [(Guide)]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

What it fixed: Able to change volume.

Except for that I'm stuck and sorta need to configure my soundcard, I guess. I might be I need drivers or something, but I can't find any which is for the newest kernel:(

Here's what I get rom lspci:

Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

I think it have Realtek codec, something like 8800.

Well, please help. It's sorta an annoying problem:neutral:

---

### Post by moore.bryan on 2007-08-06
*first, chances are if you're running fawn, intel sound is already in the kernel, so you don't need to worry about that.  after you unmute the speakers, does xmms play sound?*

---

### Post by Ub1476 on 2007-08-06
Nope, as I said, it tells me to configure the soundcard first.

---

### Post by moore.bryan on 2007-08-06
[I]and there were no errors during the ./configure, make, and make install?  that's strange...
what about audacious?
[/I]

---

### Post by Ub1476 on 2007-08-06
Here's the friendly reply I got from audacious

**Couldn't open audio.**

Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.

Oh, and I had no errors during installation.

---

### Post by moore.bryan on 2007-08-06
*that's good.  try specifying alsa as the output plugin in audacious and try playing the sound again...*

---

### Post by fredj on 2007-08-06
Open the Alsa mixer (double click on the speaker icon). Go to the File->Change Device
menu and make sure that the correct device is selected. Then go to the Edit->Preferences
menu and add all the possible volume controls and switches for both record and playback.
Make sure everything is unmuted and the suitable volume levels are set.
Configure the correct output device in Amarok etc.

---

### Post by Ub1476 on 2007-08-06
Still doesn't work. I choose ALSA as the output. I'm uploading a print-scr at imageshack if you are curious to look.:)

[[IMG]http://img467.imageshack.us/img467/6485/audioproblemkh0.th.png[/IMG]](http://img467.imageshack.us/my.php?image=audioproblemkh0.png)

---

### Post by Ub1476 on 2007-08-07
bump

---

### Post by Ub1476 on 2007-08-07
bump

---

### Post by Ub1476 on 2007-08-08
bump

---

### Post by moore.bryan on 2007-08-08
[I]easy on the bumps!  ;-)
i'd check to make sure you have all the codecs installed for what you're trying to play... speaking of, what kind of file is it?
[/I]

---

