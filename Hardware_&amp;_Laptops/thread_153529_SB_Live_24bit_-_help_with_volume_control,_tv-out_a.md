---
title: "SB Live 24bit - help with volume control, tv-out and zapping"
date: 2006-04-01
forum: Hardware &amp; Laptops
---

### Post by korami on 2006-04-01
Hi there,

until now I didn't need to start a new thread to ask for help, as the answer was already in this forum somewhere (great forum!!! :-D ). However, for the following problems I didn't find any answer. So...

(EDIT: actually this is my second thread... I forgot about the first one...)

I brought these days a Soundblaster Live 24bit card (I used the built in AC97-type sound card before), which I also managed to configure in order to have sound (even surround, though I have no surround system yet) following this [wiki]("https://wiki.ubuntu.com/HowToConfigureSoundBlasterAudigySEinBreezy?action=show&redirect=HowToSetupSoundBlasterAudigyInBreezy"). 

However, now I have the following problems:
1. Changing the volume from the volume applet has no effect, as it moves only the slider for the "IEC958 Center/LFE" mixer element, whereas the volume in my speakers gets changed only when changing the slider for the "Analog Front" mixer element. Of course I can always open the volume control and change the right mixer, but I was wondering if there is a setting here to do this directly from the panel?

2. Before, when I used the built-in sound card, I put my speakers in the first line-out connector and my audio jack for TV-out in the second one, made a setting in the gnome volume-control to use 4-channel output, and that way I had sound for my TV-out without having to switch between the jacks for the speakers and for TV every time I wanted to watch a movie on my television. Now however this is not working anymore, as I get on my TV only the rear audio output from a movie (e.g.  encoded with A/52 audio codec using surround 5.1). So the question is: can I make a setting somewhere to get stereo 2.0 audio output for every sound? Even if it's a setting in the movie player (I use totem-xine and VLC)?

3. I have a WinFast 2000XP tv-tuner using Zapping as application for viewing TV on my box (I like to have Gnome-integrated apps). Since I installed the driver CA0106 for the new sound card however, Zapping crashes at startup. This is what I get when running "zapping" in a terminal:
```
mixer.c: Invalid recording line requested
```
Any idea of how this could be fixed?


Thanks!

(PS: I hope this is the right section for posting this)

---

### Post by korami on 2006-04-03
Ok, to 3. I thought of doing a complete removal of the zapping package from Synaptic, then removed the config file from the ~/.zapping directory, then installed the zapping package again. I could start the app but had no sound this time. 

So I went to Zapping's properties->Devices->Audio and saw that the checkbox "Control volume with soundcard mixer" was not ticked. I checked it, selected the  *device file* /dev/mixer (the only entry in the drop-down box), couldn't change the *Input* as it was grayed out, and saved the settings. On restarting zapping I got the initial error again.

Is this device file not the right one? Which one could be? (The setting for default sync and default source in Multimedia Systems Selector are both set to ALSA... after having followed some threads in this forum about how to set up duplex sound...).

Any help is appreciated.

---

### Post by korami on 2006-04-12
Noone with this type of soundcard having these issues???  :(

---

### Post by xxbartosxx on 2006-06-03
[QUOTE=korami]
1. Changing the volume from the volume applet has no effect, as it moves only the slider for the "IEC958 Center/LFE" mixer element, whereas the volume in my speakers gets changed only when changing the slider for the "Analog Front" mixer element. Of course I can always open the volume control and change the right mixer, but I was wondering if there is a setting here to do this directly from the panel?
[/QUOTE]
Got one of your problems, see quote. But my problem is the volume controls on my keyboard seem to change 'Analog Center/LFE' channel and  not 'Analog Front' where my sound is.
If you right click on the sound icon next to your clock -> prefferences you can choose your soundcard and the channel to control, close the window and reboot. Now if you left click one time on the sound icon, you can change there the volume. But I can't find how the right channel would react on my keyboard volume controls, I only see that if I push a buttn that the isd change something, for the 'Analog Center/LFE' channel but no volume change or muteing.
Grts Bart

---

### Post by korami on 2006-06-05
Thanks xxbartosxx, that solved my problem with the volume control. Sorry I can't give a solution to yours. Maybe a specific keyboard driver would help...

---

