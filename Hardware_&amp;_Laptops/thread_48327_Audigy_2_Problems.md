---
title: "Audigy 2 Problems"
date: 2005-07-12
forum: Hardware &amp; Laptops
---

### Post by Haegin on 2005-07-12
I have just brought a Creative Audigy 2 Value and a 5.1 speaker setup to replace my old desktop speakers running from my onboard sound. The soundcard is picked up under Device Manager as an unknown device and the sound doesn't work.
Can anybody give me clear insturctions on how to get this soundcard working? I have had a look around the internet and have not been able to find anything that helped. I haven't a clue how to recompile my kernel with extra modules or anything so most of the tutorials have made no sense,

EDIT: I also have a logitec usb headset which is plugged in. This is picked up in alsamixer but nothing else is. When it wasnt plugged in then other options were available.

Please help

Human Prototype

---

### Post by scoon on 2005-07-12
Hey there, 

[http://www.alsa-project.org/](http://www.alsa-project.org/)

Find your card in the supported card matrix and you will get docs on how to set it up.  It should not be difficult as I run a audigy 2zs that works flawlessly.  The creative stuff works very very well with linux. 

regards, 

scoon

---

### Post by Haegin on 2005-07-12
I followed the link and found my card at the following location: [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=CA0108&module=emu10k1](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Audigy2+ZS+Value.&chip=CA0108&module=emu10k1)

The instructions tell me i need the soundcore compiled as a module. I checked using modinfo soundcore and I do have it installed. Does this mean that I can skip the quick install section or do I still have to do all or part of it?

Please can someone tell me the next step. I'm new to linux and idiot proof instructions are great. Even to the level of "Type in this command and tell me the output".

Thanks for the help so far

---

### Post by scoon on 2005-07-12
Hey there, 

Let the man pages be your guide.  start with man modinfo.  The checkout lsmod and you will end up installing the module with modprobe -v soundcore.  

regards, 

scoon

---

### Post by jrobcet on 2005-07-12
Before doing all that, you might want to have a look at this thread: [http://ubuntuforums.org/showthread.php?t=46619&highlight=audigy](http://ubuntuforums.org/showthread.php?t=46619&highlight=audigy)

---

### Post by kleeman on 2005-07-12
Do a lsmod and if you get a line like this (I have an Audigy 2 as well which works perfectly):

snd                    56580  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep

the alsa drivers are installed and you don't need to muck around with kernel module compiles or whatever.
Often the problem is simply that the mixer is muted. If this is the case execute
alsamixer
you will see sliders for master and pcm. Make sure these are unmuted and at a reasonable level (unmuting can be done with "m" on the keyboard). 

You might want to also search these fora (espeically the howto section) for basic sound checks....

---

