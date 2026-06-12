---
title: "Low sound on laptop."
date: 2009-07-20
forum: Hardware
---

### Post by RubenK on 2009-07-20
As the title says, I have pretty low sound on my new laptop (fully up-to-date Ubuntu 9.04 install). I've tried all the obvious solutions (even made the full switch to Pulse, no difference). I did the alsamixer (both GUI and Terminal) but nothing seems to work. Even with headphones, especially when playing movies sound is just annoyingly low. I can still hear the environment even with in ear and on ear headphones! Anyone else with this problem? Anyone who knows a fix? My audio card is just the standard Intel stuff:
lspci -> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

---

### Post by komputes on 2009-07-20
This is a confirmed bug. There are a few workarounds that tweak the audio for different computer models. These usually involve adding a line to the alsa-base configuration file. You can find these recommendations here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286610](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/286610)

If you find a solution please post your computer model and which alsa-base configuration line fixed it for your computer.

---

### Post by RubenK on 2009-07-20
I have no files called /etc/modprobe.d/options or /etc/modprobe.d/sound . Should I create them non the less?

Creating the file seems to have worked. It's still not super loud, but louder and loud enough! This is what I did:
sudo nano /etc/modprobe.d/options (which in my case was not yet existing)
and type
options snd-hda-intel model=laptop
at the end of it.
Reboot and done.

---

### Post by komputes on 2009-07-20
I don't know about the options file, usually I make the modification in /etc/modprobe.d/alsa-base.conf ( /etc/modprobe.d/alsa-base before Ubuntu 9.04)


So you would run
sudo nano /etc/modprobe.d/alsa-base.conf


And then you would add the following line under "options snd-pcsp index=-2"


 options snd-hda-intel model=laptop


-OR-


options snd-hda-intel model=laptop enable=1 index=0


and then reboot and check if that fixes your audio issue. If you find a fix, please share your computer make/model as to confirm that there is a bug and to assist future ubuntu users.

---

