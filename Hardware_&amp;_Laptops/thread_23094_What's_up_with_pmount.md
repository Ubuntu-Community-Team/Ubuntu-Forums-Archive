---
title: "What's up with pmount?"
date: 2005-03-31
forum: Hardware &amp; Laptops
---

### Post by bigzak on 2005-03-31
Hi all,

I know that there are various 'my usb device won't mount' threads, and possibly one or two discussing USB automount, but I couldn't find anything to fix my particular problem.

I have upgraded from Warty to Hoary, and so I expected that new USB storage devices would just magically work. Unfortunately, they do not. I have an old flash based MP3 player that used the usb-storage driver to connect, so I plugged it in with /var/log/messages running, and sure enough /dev/sdc appeared (I have a couple of card readers already hard-coded from warty).

Unfortunately, no automount. Nothing. However, if I do:

```

pmount /dev/sdc

```

as myself, an entry in /media is created and the drive is mounted! Unfortunately, it does not appear in my 'Computer' nautilus window. Gnome-volume-manager is running.

Basically, it looks like an end to end automount failure - pmount is not being run when the HAL picks up the new device, and g-v-m does not pick up when the new device does finally get mounted. Any clues would be greatly appreciated!

Thanks!

---

### Post by bigzak on 2005-04-01
I've given up ;) Just reinstalled to Hoary from the preview CD. Had one or two problems with ESD causing XMMS and RhythmBox to crash hideously, but replacing that with polypaudio and setting gstreamer to ALSA seems to have left me with a fully functional box.

---

