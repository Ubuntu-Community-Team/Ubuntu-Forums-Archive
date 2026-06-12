---
title: "No sound... what's missing???"
date: 2009-03-02
forum: Hardware
---

### Post by MoscowModder on 2009-03-02
I have Ubuntu 8.10 Intrepid Ibex installed on Win XP Pro with WUBI.  I have never heard a single sound from Ubuntu, save the occasional beep.  The main sound has remained silent.  I have ALSA, I have a mixer, everything works like it's supposed to, except that it makes no sound.

Does anyone know what's missing?

---

### Post by ddrichardson on 2009-03-03
ALSA is muted by default, have you unmuted it with alsamixer?

---

### Post by MoscowModder on 2009-03-04
I went through every single volume controller and everything acts like it's working.  Is it possible that the sound card driver could be missing?

---

### Post by theresonant on 2009-03-04
Try and go to System -> Preferences -> Sound, and see whether you're actually using ALSA for sound output. And click the "Test" buttons, though if you're saying there's no sound for anything, I don't know if they'll make it.

---

### Post by MoscowModder on 2009-03-04
I _did_ check the sound preferences and set everything to ALSA, not muted, turned up, etc.  Not one solitary beep.

---

### Post by MoscowModder on 2009-03-04
Places I've checked and enabled everything:

System -> Preferences -> Sound
Applications -> Sound&Video -> Gnome Alsa Mixer
Volume control applet -> Open volume control
The volume control on the computer itself

What's up?

---

### Post by vgrisham on 2009-03-04
Try [this (post 6)]("http://ubuntuforums.org/showthread.php?t=1012179").

Double click your volume icon in the system tray. Choose the switches tab and enable external amplifier. It worked for me.

---

### Post by jonasback on 2009-03-04
Maybe your useraccount isn't in the audio group. Try this in the terminal:

sudo adduser <username> audio

---

### Post by ddrichardson on 2009-03-04
What kind of soundcard is it?

---

### Post by MoscowModder on 2009-03-05
> **vgrisham said:**
> Try [this (post 6)]("http://ubuntuforums.org/showthread.php?t=1012179").

Double click your volume icon in the system tray. Choose the switches tab and enable external amplifier. It worked for me.

I tried switching external amplifier on and off and on again.  Do I have to restart or something?

By the way, it was on when I found it.

---

### Post by MoscowModder on 2009-03-05
> **ddrichardson said:**
> What kind of soundcard is it?

I have no idea what kind of soundcard it is.  How do I find out?

---

### Post by ddrichardson on 2009-03-05
Open a terminal and type:
```
lshw -C sound
```

---

### Post by MoscowModder on 2009-03-07
Here is the output of the command *lshw -C sound*:
```
  *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

```

---

### Post by vgrisham on 2009-03-07
> **MoscowModder said:**
> Here is the output of the command *lshw -C sound*:
```
  *-multimedia            
       description: Multimedia audio controller
       product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0

```

Try [this]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0m") or [this]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0"). After making the changes, make sure your sound settings under volume control are all set to ALSA.

---

### Post by MoscowModder on 2009-03-07
Wait...I already have ALSA!

What do your instructions do besides install ALSA?

---

### Post by vgrisham on 2009-03-07
> **MoscowModder said:**
> Wait...I already have ALSA!

What do your instructions do besides install ALSA?

The instructions alter how ALSA handles your card. 

By the way, what model is your notebook?

---

### Post by acho on 2009-03-07
I have the same problem too. My Speaker laptop is no sound. But sound is out and can be hear with speakerphone output.
I can't understand to patch it step by step.
Anyone can explain the step?
my laptop is MSI VR420x
...
...
:KS :KS :KS :KS

---

### Post by vgrisham on 2009-03-07
First, open a terminal and code:
> lshw -C sound

This will tell you exactly what card you've got.

Then, head over to the ALSA matrix. There you'll find notes on how to get your card working with ALSA. [Here's]("http://www.alsa-project.org/main/index.php/Matrix:Main") the main matrix page. It's sorted by card manufacturer. Good luck.

---

### Post by ddrichardson on 2009-03-07
Why would he need to use lshw a second time :-)

Follow the guide [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto"), when it goes wrong let us know where.

---

### Post by vgrisham on 2009-03-07
> **ddrichardson said:**
> Why would he need to use lshw a second time :-)

Follow the guide [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto"), when it goes wrong let us know where.

What do you mean a second time? ACHO is a new poster.

---

### Post by ddrichardson on 2009-03-07
> **vgrisham said:**
> What do you mean a second time? ACHO is a new poster.
What and he can't read the rest of the post? ;-)

---

### Post by vgrisham on 2009-03-07
You know, Ubuntu? Humanity towards others. I'm just trying to help.

---

### Post by ddrichardson on 2009-03-07
Yes I know the Ubuntu philosophy but you need to learn the meaning of smilies.

I marked both posts with them indicating I was joking with you - don't get so bent out of shape, if I offended you it was unintentional but you have no need to remind me of the code of conduct or the meaning of Ubuntu.

---

### Post by MoscowModder on 2009-03-11
I've been sent to three guides, but I don't quite get it.  The instructions on [the guide at alsa-project.org]("http://www.alsa-project.org/main/index.php/Matrix:Module-intel8x0m") don't work.  For example: >  NB:  	

If you are using Hg (Mercurial) then you need to type:

        ./hgcompile "or" make build

instead of:

        ./configure


and 
> Now unzip and install the alsa-driver package:

       bunzip2 alsa-driver-xxx
       tar -xf alsa-driver-xxx
       cd alsa-driver-xxx
       ./configure --with-cards=intel8x0m --with-sequencer=yes ; make ; make install


I don't have anything to unzip!  This makes no sense!

Help, please?!

---

### Post by ddrichardson on 2009-03-11
I wouldn't build from source until you've followed the [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") because you will lose automatic updates for ALSA and in my experience it breaks more than it fixes because of how many packages depend on ALSA (ymmv).

That said, the guide means download the latest alsa-driver, alsa-lib and alsa-utils tarballs from [here]("http://www.alsa-project.org/main/index.php/Main_Page"). Then extract them, open a terminal and run the ./configure script in the folder. If it fails, install what it asks for if it passes then run make.

But like I say - try the howto first.

---

### Post by MoscowModder on 2009-03-14
The howto says the following...

> Update: The build instructions in this paragraph are outdated. For Ubuntu 8.04 and 8.10 (at least) following the these instructions won't work. Please see [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695) for a convenient script that will build the latest ALSA release. Also, it is recommended that you see the more generic SoundTroubleshooting page for information on how to update audio drivers.

Didn't you say it was better _not_ to build/compile the package myself?

---

### Post by MoscowModder on 2009-03-14
While waiting for an answer, I decided to try getting those tarballs and installing it that way.  I rebooted, and still have no sound.

---

### Post by ddrichardson on 2009-03-14
Have you gone any further than the part talking about compiling a new driver? Have you tried specifying the model and so on?

---

### Post by MoscowModder on 2009-03-15
The command ```
cat /proc/asound/card0/codec#* | grep Codec
``` does nothing.  I changed it to ```
cat /proc/asound/card0/codec97#0 | grep Codec
``` and it returned ```
... Is a directory
```  How do I make it show me my card model?

Also, /usr/src/linux-headers-2.6.27-11-generic/Documentation/sound does not exist.  Is that the problem?

---

### Post by ddrichardson on 2009-03-15
What happens now if you type ```
alsactl -v
```And```
ls /proc/asound/card0
```

---

### Post by MoscowModder on 2009-03-15
I got:
```
alsactl version 1.0.16
```
and
```
codec97#0  id  intel8x0  oss_mixer  pcm0c  pcm0p  pcm1c  pcm2c  pcm3c  pcm4p
```

---

### Post by ddrichardson on 2009-03-15
OK, now```
modprobe | grep intel
```

---

### Post by MoscowModder on 2009-03-15
> **ddrichardson said:**
> OK, now```
modprobe | grep intel
```

```
Usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-Q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
```

Something tells me that's not what we want.

---

### Post by ddrichardson on 2009-03-15
Sorry, I meant```
lsmod | grep intel
```

---

### Post by MoscowModder on 2009-03-16
```
snd_intel8x0           37532  3 
snd_ac97_codec        111652  1 snd_intel8x0
snd_pcm                83204  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    63268  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         16136  2 snd_intel8x0,snd_pcm
intel_agp              33724  1 
agpgart                42184  3 drm,intel_agp

```

---

### Post by ddrichardson on 2009-03-17
Is the pc speaker module loaded?
```
sudo lsmod | grep snd-pcsp
```

---

### Post by MoscowModder on 2009-03-18
It didn't give me any feedback after asking for my password.  I rebooted and the condition is still the same.

Is that last command *sudo lsmod | grep snd-pcsp* supposed to tell me the status of something or change something?

---

### Post by ddrichardson on 2009-03-18
No, on some systems - notably Acer, the snd-pcsp module can inhibit the intel module. There's really nothing else I can offer you in the way of help here - you might have more luck [here]("http://www.alsa-project.org/main/index.php/Main_Page").

---

### Post by MoscowModder on 2009-03-18
Well, thanks for your help.  Thanks for all the time you spent thinking of solutions.  I'll keep looking on that Alsa wiki, then.

---

### Post by ddrichardson on 2009-03-18
> **MoscowModder said:**
> Well, thanks for your help.  Thanks for all the time you spent thinking of solutions.  I'll keep looking on that Alsa wiki, then.
Sorry I know its frustrating, I had a Realtek chipset in a laptop a few years ago that had a weird pinout configuration to the modem which meant that it woul not work in Linux. If it had been a desktop I'd have picked up a set of cheap USB speakers instead.

---

