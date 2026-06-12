---
title: "vt8251 sound problems"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by mathijs on 2005-11-28
Getting ubuntu to work on a mobo (asus A8V-MX) with the new via 8251 southbridge is quite hard. The dma support (without which the DVD player couldn't read the ubuntu install cd) only worked after compiling a custom kernel including the patch mentioned here:
[http://comments.gmane.org/gmane.linux.ide/6599](http://comments.gmane.org/gmane.linux.ide/6599)

The next problem is the sound, which is supposed to be VIA AC'97. I had disabled the onboard sound in the BIOS during install, but now when I re-enable it, ubuntu hangs when it's trying to play a sound during GNOME startup. acpi=off, noapic, nolapic, etc. doesn't help. Does anyone know if I need to patch the ALSA driver to get this running?

---

### Post by jamuir on 2005-12-09
I also have an asus a8v-mx with the infamous vt8251 southbridge.

Can you tell me how you were able to get ubuntu installed on your system?  I would be interested to know more about the patch you mentioned.  Is there a way to apply the patch during the install process?  you used to be able to do that in mandrake.

-James

---

### Post by jkb on 2005-12-09
Have the same problem with a compaq presario 5000.
Also have the VIA AC97 onboard sound.I must disable it to get the live cd to work but I would realy like to have the sound work.

Is there anyone who know the answer???

/Jimmy

---

