---
title: "Compiling ALSA 1.0.9 on Ubuntu"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by hettar on 2005-08-01
I need to use the newest alsa to get support for my intel high definition audio card on my laptop, but have been unable to get it to work. Everything compiles correctly but when I try to load the modules it fails with unknown symbol errors for each of the alsa modules (see below). Has anyone manged to get this to work and if so what steps did you have to take ?

Thanks.

Aug  1 12:41:52 localhost kernel: snd_hda_intel: Unknown symbol snd_pcm_new
Aug  1 12:41:52 localhost kernel: snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
Aug  1 12:41:52 localhost kernel: snd_hda_intel: Unknown symbol snd_card_register
Aug  1 12:41:52 localhost kernel: snd_hda_intel: Unknown symbol snd_card_free
Aug  1 12:41:52 localhost kernel: snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
Aug  1 12:41:52 localhost kernel: snd_hda_intel: Unknown symbol snd_hda_bus_new
Aug  1 12:41:52 localhost kernel: snd_hda_intel: Unknown symbol snd_hda_build_pcms

---

### Post by Xian on 2005-08-01
Breezy has the alsa 1.0.9 [packages](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=alsa&searchon=names&subword=1&version=breezy&release=all). 
You might try and see if they are compatible.

---

