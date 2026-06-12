---
title: "Installing New Sound Card"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by duckamuck on 2005-09-19
I've set up an older machine to record vinyl records.  Got the sound card currently installed to work, but it is far too noisy for quality recordings.  I'm looking to try the other sound cards that I have laying around.  
How do I go about getting ubuntu to recognize new cards, without doing a full reinstall?

---

### Post by karuptdata on 2005-09-19
hello this may help you a little bit once you install the card you could follow these instructions its what i used to get my new card installed..[https://wiki.ubuntu.com/forum/hardware/OldSoundCard?highlight=%28sound%29%7C%28old%29](https://wiki.ubuntu.com/forum/hardware/OldSoundCard?highlight=%28sound%29%7C%28old%29) Hopes this helps some..

---

### Post by duckamuck on 2005-09-19
Thanks for the link.
One problem:  one of the sound cards that I want to try is not listed.  The card has an AOpen AS9200 chip on it and the card shows model number AW200.  The ALSA page does not list a known Linux driver for it.

---

### Post by duckamuck on 2005-09-19
Thanks karuptdata!  Your link provided the necessary clues.

I decided to use an old SoundBlaster 16 card instead of the AOpen card.  

Here's what I had to do:

Gnome->System Tools->Terminal
sudo modprobe snd-sb16
exit

Gnome->Sound & Video->Volume Control
File->Change Device->1 Sound Blaster 16 (Alsa mixer)
Playback tab: unmute speaker and turn up volume on Master and PCM
Capture tab: unmute speaker and microphone for Line-in and adjust volume

That's it!

---

### Post by duckamuck on 2005-09-20
Sigh...
Seems that once I reboot, the sound card setup has to be rerun.  I have to go further to make them stick.
However, I am giving up since my old Soundblaster card developed a noise problem as well.

Now looking for a USB audio device to eliminate the potential for computer noise.

---

