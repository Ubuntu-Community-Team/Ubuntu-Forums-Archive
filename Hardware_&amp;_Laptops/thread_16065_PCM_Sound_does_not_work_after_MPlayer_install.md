---
title: "PCM Sound does not work after MPlayer install"
date: 2005-02-18
forum: Hardware &amp; Laptops
---

### Post by chrismc on 2005-02-18
Hi,

I Installed Ubuntu---mp3 worked with rhythm box. TV sound worked with xawtv with my tv card (old Hauppauge pci card). The soundcards listed in my gnome volume control were: Realtek ALC650 rev 3 [OSS Mixer] and VIA 8235 [Alsa Mixer].

Then I installed MPlayer from source and it worked--sound worked fine. When I rebooted I had no sound with MPlayer (/dev/dsp: not found even though it does exist). I also have no sound with rhythm box for mp3s. I now have 2 new entries in gnome volume control: bt87x [OSS Mixer] and Broketree Bt878 [Alsa Mixer]--these are for the tv card, but the tv worked fine before and they were not listed. These are in addition to the 2 I already had. the sound from the tv still works fine.

I have looked around and have no idea what happened. It seems that PCM sound no longer works. I think maybe that the sound module for the tv card is being loaded before the regular onboard sound card module. Any advice is greatly appreciated.

Thanks,

Chris

---

### Post by chrismc on 2005-02-20
OK--I got sound back in MPlayer by changing the audio driver to oss and changing the Device from /dev/dsp to /dev/dsp1 (in Preferences). Rhythmbox (or "music player" as its called in Ubuntu) still does not work. Does anyone know how to configure Rhythmbox to look for /dev/dsp1 instead of /dev/dsp?

Thanks,

Chris

---

