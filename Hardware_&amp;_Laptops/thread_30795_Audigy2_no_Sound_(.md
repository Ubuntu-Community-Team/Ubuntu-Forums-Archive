---
title: "Audigy2 no Sound :("
date: 2005-04-30
forum: Hardware &amp; Laptops
---

### Post by ksudbury on 2005-04-30
Ok to start off this sound deff works in Linux as i have had it working in gentoo for ages. 

Now i have install ubuntu hoary and i have no sound at all not at startup not from a cd or dvd nothing.

lspci outs puts the following...

0000:01:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:01:0a.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (re v 04)
0000:01:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04 )

lsmod outputs the following... 

emu10k1_gp              3840  0
gameport                4608  1 emu10k1_gp
snd_emu10k1            81668  2
snd_rawmidi            22944  1 snd_emu10k1
snd_seq_device          8332  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         64608  1 snd_emu10k1
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  1 snd_emu10k1
snd_hwdep               9220  1 snd_emu10k1
snd                    50276  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore               9824  5 emu10k1,sound,snd

====================================================


Ok i have tried alsamixer from cmd line and i have tried the gnome mixer, i have checked to see if any thing is muted and it is not, the onmly thing i have not checked is the kernel config , but i presumed it wooud have support for a Audigy2 by default. (will check that now) 

I really like ubuntu and would like to be able to have some sound :D

Thanks in advance for your help!

---

### Post by tUrtleAE86 on 2005-04-30
Are you sure you turned on the "Audigy Analog/Digital Output Jack" in alsamixer?

---

### Post by ksudbury on 2005-04-30
Oh wat a muppet !!! I belive the saying goes some thing like...

 'My Bad'


Thanks alot mate now i have funky beats   \\:D/

---

### Post by Briggzee on 2005-04-30
I am having the same issue.
When I check alsamixer I can see that "Audigy Analog/Digital Output Jack" is Off.

Forgive the newb question, but how do I turn it on?

---

### Post by ksudbury on 2005-05-01
If you are using alsamixergui (sudo apt-get install alsamixergui) you just click with your mouse on the un highlighted icon and it will go blue :D

---

