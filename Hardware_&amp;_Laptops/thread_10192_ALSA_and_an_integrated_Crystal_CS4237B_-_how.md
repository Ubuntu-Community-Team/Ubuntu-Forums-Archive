---
title: "ALSA and an integrated Crystal CS4237B - how?"
date: 2005-01-05
forum: Hardware &amp; Laptops
---

### Post by AndyGates on 2005-01-05
I've got an old Dell Workstation with an integrated Crystal CS4237B soundcard.  I'm having trouble getting it set up.  

I believe the ALSA driver for the CS4237B is snd-cs4236, and if I *modprobe snd-cs4236*, it seems to accept that.  But I have no volume controls, no system sounds, and if I try to play an MP3, Totem just sits there and looks blankly at me.  

Invoking alsamixer to get a volume control gives the following error:

*alsamixer: function snd_ctl_open failed for default: No such file or directory*

I'm a bit confused and would appreciate any help that's on offer!

---

### Post by tragek on 2005-01-30
[QUOTE=AndyGates]I've got an old Dell Workstation with an integrated Crystal CS4237B soundcard.  I'm having trouble getting it set up.  

I believe the ALSA driver for the CS4237B is snd-cs4236, and if I *modprobe snd-cs4236*, it seems to accept that.  But I have no volume controls, no system sounds, and if I try to play an MP3, Totem just sits there and looks blankly at me.  

Invoking alsamixer to get a volume control gives the following error:

*alsamixer: function snd_ctl_open failed for default: No such file or directory*

I'm a bit confused and would appreciate any help that's on offer![/QUOTE]

Ahh, the hell chip. Sorry, but thhat's what I discovered about the CS4237B. I have it in my laptop, and for all the trouble it is to get working, I usually don't try. That said, I have had sucesses with alsaconf (the program), and the following module paramaters. Yours may vary. 
options snd-cs4236 port=0x530 cport=0x210 isapnp=0 dma1=1 dma2=0 irq=5

---

