---
title: "line-in/external microphone on Dell Studio XPS 1340"
date: 2009-12-17
forum: Hardware
---

### Post by potiphera on 2009-12-17
I have a Dell Studio XPS 1340 with Jaunty installed from Dell's ISO.  I can record from the internal microphone, but I can't seem to get the line-in jack working, even when I mess around with the volume control -- I would think changing "digital input source" to "analog inputs" would work, but it doesn't.  Does anyone know anything about this?  Thanks!

---

### Post by potiphera on 2009-12-19
(bump)

---

### Post by potiphera on 2009-12-20
bumping again

---

### Post by Wollombi on 2009-12-22
I'm having the same/similar problem, but on an HP DV5t.  No idea on the reason/fix yet, though.

---

### Post by potiphera on 2009-12-22
Not sure if the fix is the same or if it's hardware-dependent.  My card is an HDA NVidia.  I've never had any success with getting microphones/line-in input to work on laptops with Ubuntu; I was surprised that even the internal microphone worked on this one.

---

### Post by potiphera on 2009-12-26
Also, I found [this thread]("http://ubuntuforums.org/showthread.php?t=385739") on getting microphones to work, and I'm not about to read all 75 pages, but the OP is from 2007, so I don't know if it still applies in the Pulseaudio world.

---

### Post by srix on 2010-01-30
I have the same problem on a Dell Vostro 1500 - internal mic works fine, external headphones work fine, but external mic. is not recognized. I also found that when the external mic. is plugged in when booting, it is recognized and works. Once I pull it out and plug it back in, it's never recognized again. 

There was some other post that did acknowledge broken external mic. support and said fixes are coming in Lucid, but "patches are too invasive for Karmic".

---

### Post by potiphera on 2010-02-25
Excellent, I'll try that and try installing Lucid when it's released.

---

### Post by srix on 2010-03-02
Update: I've installed Lucid Alpha 3, and it doesn't help any :(
I'm pretty sure the external mic used to work with Intrepid or earlier, but ever since I moved to Karmic and beyond this problem has persisted.

---

### Post by felsss on 2010-04-23
Same for me on a Dell XPS 1330. Ext mic not working on Karmic or Lucid RC.
Tried with Linux Mint 7 (based on Jaunty) and works OK so I believe it would work with Jaunty as well.

---

### Post by rosegarden78 on 2010-04-30
When I upgraded to Lucid from Karmic (AMD64 Ubuntu Studio / 2-step partial upgrade) the alsamixer terminal program was different.  It no longer allowed me to change the microphone input with Line Jack.  It disappeared.

So I fiddled around a bit, found a forum post about upgrading ALSA, and took a look at ALSA in the Synaptic Package Manager.  ALSA has many parts I'm told: libs, plugins, OSS, firmware, driver, utils, and a few more.  Some of these parts were missing from Synaptic.

Therefore I looked for some of these parts.  I found that alsa-firmware-*, alsa-oss, and alsa-utils were missing.  I installed them through Synaptic.  Then I left the external mic plugged in, rebooted, and voila!

Not only did alsamixer have Line Jack again, but now alsamixer remembered my settings, at least for the session.  Which is something I don't recall happening in Karmic.  It was probably the firmware loaders that did it for me.

---

### Post by Steve White on 2010-05-15
Mine is a Dell D420 (Intel Corporation N10/ICH 7 Family High Definition Audio Controller)

With Ubuntu 9.10, the preferred solution was to uninstall PulseAudio and install the whole ALSA suite.  Then an external mike would work.

In Lucid however, PulseAudio has become as integral to Gnome as Explorer is to Windows.  So you have to live with it, like it or not.

In the Gnome Sound Preferences panel, have under Hardware:
     Internal Audio
     1 Output / 1 Input
     Analog Stero Duplex
choose Profile:
     Analog Stereo Duplex
Under Input, the only device listed is:
     Internal Analog Audio Stereo
Choose the "Microphone" connector, and the input level reflects tapping on the built-in mike.  Even with the external mike plugged in, it still shows the internal mike only.
Choose the "Line-In" connector, and the Input Level shows zero, regardless of whether or not the external mike is plugged in.

I had been using this mike successfully before upgrading, and have checked it on another device.  It is working.

In the Gnome Multimedia Systems Selector, I see several Input options: ALSA, OSS, PulseAudio, Test Sound, Custom, Silence.
With ALSA, OSS, and PulseAudio, the "Test" button produces an awful racket that might be an overdriven version of the fan noise in the internal mike.  Only Test Sound makes a nice beep.

I re-booted using a clean Lucid Live system, and ran the Hardware Test.  There, only, did the external mike work.
Now... did I misconfigure something, or is something not installed right?

---

### Post by uhurusurfa on 2011-03-07
Use the GTK+ version of Alsa Mixer Settings app (NOT GNOME one which has no effect) and set "Capture" sliders up high and "Mic Jack Mode" as "Mic" Also make sure the options line for snd-hda-intel in /etc/modprobe.d/alsa-base.conf is set to correct model: eg
options snd-hda-intel model=dell-m44    # For Inspiron laptops

Above solved my external mic not working issue.

---

