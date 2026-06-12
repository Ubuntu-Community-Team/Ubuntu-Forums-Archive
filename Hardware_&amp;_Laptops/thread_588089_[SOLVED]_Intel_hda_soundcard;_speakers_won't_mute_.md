---
title: "[SOLVED] Intel hda soundcard; speakers won't mute when headphones are plugged in"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by hazica on 2007-10-23
Problem description:

My Intel hda sound card works just fine under normal circumstances, but when I plug the headphones in, the speakers aren't automatically muted.

I remember reading somewhere that updating the alsa driver to version 1.0.15 would solve the problem. I did and it didn't.

Needless to say that  playing around with the volume sliders in various sound mixers didn't do the trick either.

I can definitely rule out any hardware problems since the system works perfectly under Vista - an OS which I passionately dislike.

I'm using Kubuntu Gutsy (I upgraded from Feisty).  

I'd really appreciate your help.

Thanks.


EDIT: this info  might be useful:

```

$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc400000 irq 22


```

---

### Post by brk3 on 2007-10-23
I also have a similar problem with this card since I upgraded to Gutsy in that the volume slider in the volume applet/alsamixer appears to have no effect on the volume.. very annoying :confused:

---

### Post by thegr8brian on 2007-10-23
I had the same problem try adjusting the surround volume, for some reason my laptop speakers are labelled  as surround and my headphone is labelled as front.

---

### Post by hazica on 2007-10-23
Thanks thegr8brian for the suggestion but i don't have any surround settings sliders. 

I only have 3 output setting sliders: Master, PCM, and Digital. I have no idea what "digital" stands for but it doesn't appear to have any effect on the sound output. Master and PCM, both adjust the sound volume.

Any other suggestions?

EDIT: here is another bit of info straight from the horse's mouth:
```

$ cat /proc/asound/*

cat: /proc/asound/card0: Is a directory
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc400000 irq 22
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 33:        : timer
00-00: HDA Codec 0
cat: /proc/asound/Intel: Is a directory
 0 snd_hda_intel
cat: /proc/asound/oss: Is a directory
00-01: Conexant Digital : Conexant Digital : playback 1
00-00: CONEXANT Analog : CONEXANT Analog : playback 1 : capture 1
cat: /proc/asound/seq: Is a directory
G0: system timer : 4000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
Advanced Linux Sound Architecture Driver Version 1.0.15.
Compiled on Oct 23 2007 for kernel 2.6.22-14-generic (SMP).

```

---

### Post by palintheus on 2007-10-23
This is marked solved, but I don't see a solution, unless I'm missing something

---

### Post by hazica on 2007-10-23
Ok. Finally managed to get the damn thing working! I can finally listen to music in the library!

Should anyone be interested in how I managed to do it, well... here is the [[COLOR="Red"]solution[/COLOR]]("http://https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28HdaIntelSoundHowto%29").

Assuming you already have alsa up and running, you can jump straight to the section called **Manually Specify Module Parameters**

Here's what I've done to fix my problem:

Basically you tell alsa which driver to use for your hda intel sound card. You do this by first looking at the output of ```
head -n 1 /proc/asound/card0/codec*
``` In my case it was ```
Codec: Conexant CX20549 (Venice)
```
Then you issue the command: ```
zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
``` Look for the subtitle "Module snd-hda-intel". In this subsection look for the name of codec (in my case the *Conexant CX20549* was renamed to *Conexant 5045*). Then go through the list of possible options for this codec and choose the one that suits you best. I had the choice between *laptop* and *test*.

The next thing to do is edit the **/etc/modprobe.d/alsa-base** file as root. ```
sudo kate /etc/modprobe.d/alsa-base
``` Replace kate with your preferred editor (gedit, vim).
Add the line *options snd-hda-intel model=OPTION_YOU_CHOSE* to the file.
 In my case, the line looked like this *options snd-hda-intel model=laptop*.
Save and reboot.

That should do the trick.

PS: The same howto in german: [[COLOR="Red"]link[/COLOR]]("http://wiki.ubuntuusers.de/Soundkarten_installieren/HDA")

---

### Post by brk3 on 2007-10-24
hmm, must try this when I get home

---

### Post by tanas on 2007-10-24
Thanks hazica!!! It worked!
I followed your instructions in German, and just had to try two different options.

For those who don't read German and have a ALC883 as I do, there's an extra step that hazica didn't wiote here (because the thread was related to another card). Add the same line 

snd-hda-intel model=OPTION_YOU_CHOSE
in the end of file /etc/modules without the "options".

:)

---

### Post by hazica on 2007-10-25
> **tanas said:**
> 
For those who don't read German and have a ALC883 as I do, there's an extra step that hazica didn't wiote here (because the thread was related to another card). Add the same line 

snd-hda-intel model=OPTION_YOU_CHOSE
in the end of file /etc/modules without the "options".
:)

Sorry about the omission. As you said, it wasn't relevant to me so i kind of overlooked it.

---

### Post by labord on 2007-10-28
I too have an ALC883 and I followed all the suggested steps but none of the options offered in alsa-config solved my problem. I tried "laptop-eapd" but then only headphones worked (after rebooting), speakers were mute. Then I tried "acer" with the same result, and "medion" did not work at all (my laptop is neither acer nor medion, its a cheap no-name from pc-world). Any suggestions?

---

### Post by ashlakim on 2008-02-02
Just what I had been looking for ages and none worked before! But now the problem is solved! Thanx! ^^!

---

### Post by Scarabomb on 2008-03-19
> **tanas said:**
> Thanks hazica!!! It worked!
I followed your instructions in German, and just had to try two different options.

For those who don't read German and have a ALC883 as I do, there's an extra step that hazica didn't wiote here (because the thread was related to another card). Add the same line 

snd-hda-intel model=OPTION_YOU_CHOSE
in the end of file /etc/modules without the "options".

:)

OMG THANK YOU SO MUCH!! I've broken my system about 10 times now trying to find different fixes but this and

> **hazica said:**
> Ok. Finally managed to get the damn thing working! I can finally listen to music in the library!

Should anyone be interested in how I managed to do it, well... here is the [[COLOR="Red"]solution[/COLOR]]("http://https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28HdaIntelSoundHowto%29").

Assuming you already have alsa up and running, you can jump straight to the section called **Manually Specify Module Parameters**

Here's what I've done to fix my problem:

Basically you tell alsa which driver to use for your hda intel sound card. You do this by first looking at the output of ```
head -n 1 /proc/asound/card0/codec*
``` In my case it was ```
Codec: Conexant CX20549 (Venice)
```
Then you issue the command: ```
zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
``` Look for the subtitle "Module snd-hda-intel". In this subsection look for the name of codec (in my case the *Conexant CX20549* was renamed to *Conexant 5045*). Then go through the list of possible options for this codec and choose the one that suits you best. I had the choice between *laptop* and *test*.

The next thing to do is edit the **/etc/modprobe.d/alsa-base** file as root. ```
sudo kate /etc/modprobe.d/alsa-base
``` Replace kate with your preferred editor (gedit, vim).
Add the line *options snd-hda-intel model=OPTION_YOU_CHOSE* to the file.
 In my case, the line looked like this *options snd-hda-intel model=laptop*.
Save and reboot.

That should do the trick.

PS: The same howto in german: [[COLOR="Red"]link[/COLOR]]("http://wiki.ubuntuusers.de/Soundkarten_installieren/HDA")

Worked for me.

It took me awhile to get my speakers back up after I messed them up.  Next task, transferring my iTunes playlists and getting WoW to play faster than 20 fps.

---

### Post by shamshe on 2008-04-29
hmmm it worked for me but now i have to go in and turn the headphone check mark on and off everytime to get it to work. i have a custom built ms-1719 

any resolution for this?

---

