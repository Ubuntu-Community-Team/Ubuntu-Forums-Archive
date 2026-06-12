---
title: "why is sound such a problem"
date: 2005-11-15
forum: Hardware &amp; Laptops
---

### Post by jezjones on 2005-11-15
Hi everyone,

It seems to me that sound is a real issue for alot of people using breezy.

I have yet to get sound working, it seems that the card is detected and when alsa starts up there is slight pop sound (like speakers being turned on), but nothing comes out when i play sounds or cds or dvds.

I can use the fn sound controls and i get the same 'pop' type noise when i mute / unmute .

I have got alsamixer and muted / unmuted everything while sound is playing.

To be honest there seems to be quite a few contraditions in the fixes poeple have found, for some it is muting certain channels and for others it is unmuting them.... well none of it works for me.

I have been using linux since debian 3.0, and until ubuntu i would build a minimal system and then add to it.

I like ubuntu but one of the problems that all distros suffer from (and is the source of my confusion here), there are too many programs.

For sound there is OSS, ALSA, ESD and Arts in my multimedia selector.
When i go to my mixer or alsamixergui there is the conexant device and the alsa device.
There are too many combinations!!! and not enough info about which i need and which i can do without.

Previously i have only used alsa for sound and not had the others and i cant help thinking that things are getting confused with all this sound stuff.

Can anyone point me to a decent little app that will control my sound config for me... or failing that can anyone give me any more info on which sound do i need and which i should set to what in the multimedia selector.

I really dont want to spend my time installing from scratch and building up, cos i'll do it with debian not ubuntu and i am trying to show my friends that linux (esp ubuntu) is really accessible.


hardware:-

PB easynote A8 laptop (centrino et all), AC97 intelICH6 sound card, Ubuntu breezy plus automatix

---

### Post by Sewage on 2005-11-17
I am having ongoing issues with my sound as well~ I have yet to get the sound card even installed.

I just have a simple question though, not meaning to hijack your theard~ is there a command or an application used to install/setup/configure your sound card, other than "system/preferences/sound"?

---

### Post by jezjones on 2005-11-20
not a problem, i dont think there is really an answer as these forums are pretty helpful, so the lack of replies means that its all covered in other threads.

Anyway, i have had some progress and i am trying to use the latest alsa drivers,  as ubuntu came with 0.9 and apparently 0.9b works... i will post success as i have it, as the driver is up to 10.0 now... 

In the process i installed alsaconf which is the program that configures alsa cards. You should be able to apt it, and then try man alsaconf

Good luck

---

### Post by mistergq on 2005-11-28
Jez, did you have to recompile your Kernile for the upgrade to the new drivers?  I too am having sound problems (no sound) on my gateway laptop.

---

### Post by mengqing on 2005-11-28
try the 1.0.10 driver, it may work for you, well at least it worked for me.

---

### Post by mistergq on 2005-11-28
[QUOTE=mengqing]try the 1.0.10 driver, it may work for you, well at least it worked for me.[/QUOTE]
I would like to, but as a newbie, I am not sure how to install it and I have not found any howtos walking me through it.

---

### Post by mengqing on 2005-11-28
[QUOTE=mistergq]I would like to, but as a newbie, I am not sure how to install it and I have not found any howtos walking me through it.[/QUOTE]

First, goto [http://www.alsa-project.org/](http://www.alsa-project.org/) and download all the 1.0.10 stuff on the right side

then follow this howTO  [https://wiki.ubuntu.com//HdaIntelSoundHowto](https://wiki.ubuntu.com//HdaIntelSoundHowto)

---

### Post by mistergq on 2005-11-28
thansk, I tried those as well as this [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=.&chip=440MX%2C+i810%2C+i810%2C+i810E%2C+i820%2C+i820&module=intel8x0](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=.&chip=440MX%2C+i810%2C+i810%2C+i810E%2C+i820%2C+i820&module=intel8x0) and I still do not have 1.0.10 installed.  THis is getting very frustrating quickly.

Has anyone written a how to compile this into the kernile?

---

### Post by mflint on 2006-08-29
Jezjones>

Apologies to everyone for resurrecting an old thread, but I have the same laptop and same problem as Jezjones - and might have made some progress.

Original problem:
On my Packard Bell Easynote A8 machine, the sound card appears to be recognised, the modules are all installed, but nothing comes out of the speakers.

Current situation:
I can hear sound through headphones, but it's extremely quiet - almost inaudible.

Here's what I did:
Followed the instructions in [this post]("http://www.ubuntuforums.org/showpost.php?p=791304&postcount=164") for installing ALSA from CVS.

Then, in my terminal window, ran
```
watch -n 1 aplay /usr/share/sounds/question.wav
```
to get a sound constantly playing, and then messed around with the volume controls.

The volume control device is set to "Intel ICH6 (Alsa mixer)", and the following individual controls in the 'playback' section are all set to maximum volume, unmuted:

Master, PCM, Center, Mic (yes, really)

All other controls are mute or zero volume.

Can anyone else confirm these findings?

---

### Post by michellez on 2006-09-16
Sat here now with my Packard Bell A8 550 - same machine with just a bit faster processor basically. I'm having the exact same sound problems!

Maxed all the ones you said you have and muted the rest. Same still.

What have you got ticked on the "Switches" tab in the volume control?

Cheers :)

---

