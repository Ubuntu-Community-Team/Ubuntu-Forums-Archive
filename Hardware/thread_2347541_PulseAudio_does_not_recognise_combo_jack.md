---
title: "PulseAudio does not recognise combo jack"
date: 2016-12-26
forum: Hardware
---

### Post by stazthebox on 2016-12-26
[COLOR=#242729][FONT=Arial]I have an Acer E-15 series laptop dual booting Ubuntu 16.10. The only port audio port on my laptop is a combo jack for headphones and microphone. On Windows, the Realtek software recognise the combo jack and I can plug in a headset and use the microphone on it. On Linux it does not recognise the microphone part of the jack, and I've use hdajackretask and I've modified[/FONT][/COLOR]
/etc/modprobe.d/alsa_base.conf 
[COLOR=#242729][FONT=Arial]and added options snd_hda_intel model=laptop-dmic and it still doesn't recognise the port. But I can plug in a headset into the jack and it works.[/FONT][/COLOR]

---

