---
title: "microphone doesn't work - Gutsy - HP nc2400"
date: 2007-11-24
forum: Hardware &amp; Laptops
---

### Post by dormant on 2007-11-24
I've updated my hp Compaq nc2400 from Feisty to Gutsy.

The only problem seems to be the microphone. It doesn't work.

I recall having microphone problems when I first installed Feisty, but can't remember what I did to fix them.

Any suggestions what to check - I've tried various options in the volume control applet, but nothing worked.

All hardware is OK - the microphone works in Windows.

This is how far my debugging has gotten, before I got confused:
> $ cat /proc/asound/card0/codec#* | grep Codec
Codec: Analog Devices AD1981
Codec: Conexant ID 2bfa

---

### Post by catfishk on 2007-11-25
maybe open a terminal, and run 'alsamixer'.  hit TAB and see if 'capture' is muted?  i needed to bring up 'mic boost' as well for mine to work

 good luck!

---

### Post by legend2440 on 2007-11-25
I had the same problem with not being able to record with audacity or Sound Recorder.
I would get error messages and sound recorder would not even start up.
I noticed that when pulseaudio was installed I got the errors and when I uninstalled it everything worked again.
Hope this helps!

---

### Post by dormant on 2007-11-26
yeh, it was that capture was muted.

i fixed it in the gnome Volume Control.

thx

---

