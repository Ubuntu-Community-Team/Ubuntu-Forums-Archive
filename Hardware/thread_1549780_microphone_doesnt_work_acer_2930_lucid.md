---
title: "microphone doesnt work acer 2930 lucid"
date: 2010-08-10
forum: Hardware
---

### Post by Alexthecrate on 2010-08-10
I had read that there was an issue with the microphone on the Acer 2930.  I thought it was solved and bought a machine but have failed to make  any sense out of the info that is all over the place on the forum.
Does anyone have a clear explanation of how to sort out this problem?  Will it be sorted out in the next version I wonder as this has been gong  on for some years it appears?
Thanks in advance...

---

### Post by gabrielcik on 2010-08-10
Hola,

My internal microphone doesn't works out of the box with Ubuntu and i had to add:

options snd-hda-intel model=auto in /etc/modprobe.d/alsa-base.conf. and reboot.

after this it started to work again :) 

(Note: u may need also to activate it in alsamixer).

---

### Post by Alexthecrate on 2010-08-10
> **gabrielcik said:**
> Hola,

My internal microphone doesn't works out of the box with Ubuntu and i had to add:

options snd-hda-intel model=auto in /etc/modprobe.d/alsa-base.conf. and reboot.

after this it started to work again :) 

(Note: u may need also to activate it in alsamixer).

Hi Gabrielcik... thanks for your help. Unfortunately this is not a working solution on my machine. The mic does not work apart from giving lots of hissing noise. On top of that when the system closes down there is a nasty hum out of the speakers. So I deleted the line in the conf file and will have to wait for another answer... anyone???
Thanks...

---

