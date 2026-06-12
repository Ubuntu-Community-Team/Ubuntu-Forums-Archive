---
title: "Front audio port not working"
date: 2015-08-05
forum: Hardware
---

### Post by asher3 on 2015-08-05
My front audio port is not working. I have a ALSA log but I don't know how to read it to tell me what to do. Here is the link [http://www.alsa-project.org/db/?f=cb6832828437df10f73fe441f86b325795303e23](http://www.alsa-project.org/db/?f=cb6832828437df10f73fe441f86b325795303e23) Thank you.

---

### Post by Yellow Pasque on 2015-08-05
I'm guessing you want this to say true, but I'm not sure how to change it:
```
	control.43 {
		iface CARD
		name 'Front Headphone Jack'
		value false
		comment {
			access read
			type BOOLEAN
			count 1
```

Maybe try toggling/disabling Auto-Mute in alsamixer? Usually, you want the feature enabled (to automatically silence speakers when you plug in headphones), but sometimes, it causes issues.
```
Simple mixer control 'Auto-Mute Mode',0
  Capabilities: enum
  Items: 'Disabled' 'Enabled'
  Item0: 'Enabled'
```

---

### Post by asher3 on 2015-08-06
Does anyone know how to change these settings?

---

### Post by dino99 on 2015-08-06
both programs: paref & pavucontrol will let you tweak the input devices and settings (install them first, then go to the menu to use them)
note that pulseaudio is very sensitive and wants the jack(s) plugged without error (same color)
indeed the bios may use 'hda' not 'ac97'

---

