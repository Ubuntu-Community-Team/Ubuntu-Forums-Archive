---
title: "Sound Problems w/ outputs"
date: 2005-03-21
forum: Hardware &amp; Laptops
---

### Post by psoulocybe on 2005-03-21
I have a ca0106 (SoundBlaster Live! 24bit) based card.  I compiled the alsa kernel and such... got it working.

However, there is no output from my rear and center channel outputs on the card.  I've tried making sure they are not muted, but still no luck.  The mixer sees them, but doesn't actually produce any sound when playing mp3s... is there a way to make sound come out using xmms from the center and rear channels?

---

### Post by IdoMcFly on 2005-03-21
[QUOTE=psoulocybe]I have a ca0106 (SoundBlaster Live! 24bit) based card.  I compiled the alsa kernel and such... got it working.

However, there is no output from my rear and center channel outputs on the card.  I've tried making sure they are not muted, but still no luck.  The mixer sees them, but doesn't actually produce any sound when playing mp3s... is there a way to make sound come out using xmms from the center and rear channels?[/QUOTE]
 I'm using a 5.1 speakers set from Cambridge Soundworks and to get all my speakers on I did this:

in alsamixer (gnome-alsamixer for a better view) I enabled "SB Live Analog/Digital Output Jack" (I have a SBLive 5.1) then on my speakers panel I've selected some specific options (Fourpoint/5.1 DIN and Multi-channel Digital-in).

Your cas is quite different so maybe you have to tweak a bit. good luck

---

### Post by psoulocybe on 2005-03-21
i'm in kde, and have both alsamixergui and kmix installed.

neither have any options for the soundcard for enabling anything.

does xmms have output to your rears and mid?

---

### Post by IdoMcFly on 2005-03-22
yes it has.

try gnome-alsamixer, maybe it will show up more options.

---

### Post by filemanager on 2005-07-12
[QUOTE=psoulocybe]I have a ca0106 (SoundBlaster Live! 24bit) based card.  I compiled the alsa kernel and such... got it working.

However, there is no output from my rear and center channel outputs on the card.  I've tried making sure they are not muted, but still no luck.  The mixer sees them, but doesn't actually produce any sound when playing mp3s... is there a way to make sound come out using xmms from the center and rear channels?[/QUOTE]
 How did you compile the alsa kernel? And where did you d/l the driver?

I'm having trouble installing this driver =\

---

