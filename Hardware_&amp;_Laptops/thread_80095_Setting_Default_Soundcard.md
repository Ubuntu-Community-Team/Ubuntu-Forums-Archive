---
title: "Setting Default Soundcard"
date: 2005-10-21
forum: Hardware &amp; Laptops
---

### Post by JustRandomName on 2005-10-21
Hi,

I have a laptop with a built in soundcard and an external (usb) sound blaster 24-bit live! card.

Both cards work independatly, and allow more than one app playing a sound at the same time, the problem is that Ubuntu (or GNOME?) defaults to using the internal laptop one so all of the sounds work through that.

I have managed to get various programs (like XMMS, MPlayer etc) to use the other sound card by going into the audio options, changing the way of playing audio by using Alsa and then changing the device to hw(1.0).

The problem is that this is just for that application, how would I set it so that all the applications use the externel (including gnome)?

I thought I could disable the internal card via the BIOS but there is no such option.

Thanks in advance

---

### Post by sciolizer on 2005-10-21
Under GNOME, you can set A default sound card by going to "System -> Preferences -> Sound", however this has not worked for all applications for me (basically it only works for the GTK ones).  I still can't get programs like frozen-bubble to work, so if anybody knows a more rudimentary way of changing the default sound card (not afraid of command line), I'd be happy to know as well.

---

### Post by JustRandomName on 2005-10-22
I tried via gnome, but it seems to ignore it so I tried blacklisting the module, but it is still getting loaded somewhere else.

---

