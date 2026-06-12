---
title: "Sound Problem Toshiba X200"
date: 2008-08-12
forum: Hardware
---

### Post by bastianbu on 2008-08-12
Hi there ...

I am new to linux and i have a little problem with it on my notebook 

Notebook:

Toshiba Satego X200 - 21U  (in hardware the same as a Toshiba Satelite x205-S9349 but the german version)

So i installed linux an well i got 95% of the problems solfed :guitar:

But there is 1 Problem left with the soundcard (the microfone)

At first the sound was not running at all (only 2 of the speakers in the 4.1 systems) .... so i followed the folowing steps:

[http://ubuntuforums.org/showthread.php?p=4473064](http://ubuntuforums.org/showthread.php?p=4473064)

(thx to LuisGMarine to get my spekers running ;) )

The only thing that does not work is the sound recording ... 

I can't record anything from the mic and outhers don't hear me in teamspeak2 or skye 

I tryed to configure it with alsamixer but this doesn't seem to work either. (perhaps the main problem is that i don't realy know what i have to configure in the kmix or alsamixer to get it work ... )

greetings from bavaria

Bastian



ps. sorry for my bad english but i am not a nativ speaker ...

---

### Post by balaknair on 2008-08-12
I think there is an unresolved bug with the internal mic in some laptop models, but I'm not sure if that is the trouble in your case. If you mention which version of Ubuntu you're using(Ubuntu/Kubuntu/Xubuntu 7.10/8.04  32-bit/64-bit) it would be helpful.
[I just installed Ubuntu 64-bit on a Lenovo laptop with hardware similar to your specs, and it worked out of the box(all the hardware worked flawlessly including wifi, suspend/resume and sound).]

If you're using Ubuntu 8.04, it comes with ALSA 1.0.15 which generally works fine with ICH8 audio(including the mic in my limited experience). 
Before trying anything else follow these steps and see if this fixes the issue:
1. right-click on the volume applet and select "Open Volume Control".

2. within the volume control application select "Edit > Preferences".

3. select "Capture", "Mix", and "Input Source" at the bottom of the list, and close.

4. select the "Recording" tab and set "Capture" to full volume and "Mix" at about 1/3 full volume.
5. make sure Capture and Mix are unmuted

6. select the "Options" tab and select "Mic" as the input source.


If you still experience problems, you can try recompiling ALSA with 1.0.16 or 1.0.17(the latest stable version) 
This is a last resort however.
There are many guides available on how to do that, I'd recommend this one
[https://help.ubuntu.com/community/SoundTroubleshooting#ALSA%20driver%20Compilation](https://help.ubuntu.com/community/SoundTroubleshooting#ALSA%20driver%20Compilation)
 


There might also be a pulseaudio issue with Skype, you could try this page
[http://www.kaobear.com/2008/08/09/pulseaudio-fixes-for-hardy-heron/](http://www.kaobear.com/2008/08/09/pulseaudio-fixes-for-hardy-heron/)

You'll find tips on how to make Skype recognize your mic hardware (Appendix A in the above guide).

Hope this is helpful.
If you still have issues, post a reply here and mention what version of Ubuntu you're using, and post the output of the following commands in a Terminal(Applications menu> Accessories> Terminal)
```
lspci -v
``` 
```
aplay -l
```

All the best.

---

### Post by bastianbu on 2008-08-13
It's not working :/

I am Using Kbuntu x64 with Alsa 1.0.17

lspci -v gave me (for the audio contorler ;) ):

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller
(rev 03)
Subsystem: Toshiba America Info Systems Device ff00
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at f7500000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0
Enable-
Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
Capabilities: [100] Virtual Channel <?>
Capabilities: [130] Root Complex Link <?>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

aplay -l says:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

the alsa config file:

options snd slots=snd-hda-intel
options snd-hda-intel model=toshiba
alias snd-card-0 snd-hda-intel

... hm ...

Am i right if I say that the alsa config file isn't working as intended becorse the settings there aren't used? :confused:

... best thing will be to reinstall Alsa i think ...

greetings

Bastian

---

### Post by balaknair on 2008-08-13
Is the installation updated?
The newest modules in *buntu 8.04(linux-ubuntu-modules-2.6.24-19 and above) have built in support for the ALC268 codec, at least with ALSA 1.0.15(haven't tried 1.0.17) the only thing needed would be to add to 
etc/modprobe.d/alsa-base the following line
*options snd-hda-intel model=toshiba*

Could you try replacing 'toshiba' with 'auto', add this line
*options snd-hda-intel probe_mask=1*

(or probe_mask=8 ) and reboot, and see if it works before reinstalling alsa?

If not, it's probably easiest to reinstall ALSA.

BTW, what makes you say the ALSA config settings aren't used? Actually they are probably being used, they basically tell the kernal module what the hardware and firmware are like and how to communicate with them.

I hope this works for you.
All the best.

---

