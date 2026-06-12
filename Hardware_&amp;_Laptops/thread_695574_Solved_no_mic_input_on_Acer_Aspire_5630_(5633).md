---
title: "Solved no mic input on Acer Aspire 5630 (5633)"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by ryukent on 2008-02-13
To all those who might be having difficulty making the internal microphone work on your Acer Aspire 5630 series laptop using the 82801G (ICH7 Family) High Definition Audio Controller, this worked for me:

gksu gedit /etc/modprobe.d/alsa-base

Add this line to the bottom:

options snd-hda-intel model=acer

Then restart.

Now double click on the volume control on your systray. Goto edit / preferences.

Turn on 'capture', 'capture 1' and both 'input source' options.

Go to the recording tab and put both 'Capture' sliders to max.

Go to the options tab and set both input sources to 'Mic'

Sound should now work. In skype, it seems that letting it do its own levels results in better quality sound.

Just for the record, the sound card runs on  Realtek ALC883 codec.

---

### Post by jan quark on 2008-02-14
it would be better if you post solutions and guides in the right section:
tutorials and tips

thank you

---

### Post by lizardmenke on 2008-03-28
ryukent  you're a genius! It works like a charml on my new acer. Thank you for this tut.

---

