---
title: "Maverick upgrade partially broke sound"
date: 2010-12-21
forum: Hardware
---

### Post by Lateralis on 2010-12-21
Season's greetings to one and all!

I have a curious problem with my Fujitsu Siemens Amilo laptop after upgrading from Lucid to Maverick.  Everything was fine in Lucid, did the upgrade and everything is largely fine except my sound. 

The problem: sound works if I have something plugged into the headphone/speaker jack but no sound comes from the front laptop integrated speakers.  At first glance, the microphone seems to be working OK.

Here is some (potentially) useful information:


Ubuntu Maverick 64-bit

```

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

dmesg relating to the sound card:


[    0.410030] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.410034] pci 0000:00:1b.0: PME# disabled
[   23.719271] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   23.719529] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   23.719558] HDA Intel 0000:00:1b.0: setting latency timer to 64

```

I can see the correct kernel module, snd_hda_intel, is loaded into the kernel.  

I have checked gstreamer-properties and the Ubuntu sound preferences and everything seems OK and in order.  

I don't have OSS installed and the system is using ALSA.  (Could that be it?  What is the default now in Ubuntu?)


Does anyone have any suggestions or tips for getting the front speakers working? 

Thanks!

---

### Post by mastablasta on 2010-12-21
10.04 has alsa 1.0.22, 10.10 has ver 1.0.23.
 
have you checked alsamixer? Have you tried to configure the sound card via alsa?
 
sudo alsaconf

---

### Post by DasEi on 2010-12-21
As mentioned above install alsamixergui and check if channels are unmuted. Also you see in the upper right corner of that gui if soundchip was detected correctly (then it's name is printed there. PCM as volume has to be higher then 0.

If that won't do it, recompile Alsa, preferably latest version.
Howto and latest package are on alsaprojekt homepage.

DasEi

---

### Post by Lateralis on 2010-12-21
I meant to mention that I have the version 1.0.23 of Alsa

```

cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.23

```

I have alsamixer installed but had forgotten about that.  I have just checked and nothing's muted.  Every channel has a value greater than 0 except mic and mic gain.  

alsamixer also appears to have detected my sound card OK.  In the top left of the alsamixer menu it says

```

Card: HDA Intel                                                                                                                
Chip: Realtek ALC888

```

which is correct.  I tried ```
sudo alsaconf
``` but that command doesn't exist and doesn't appear to be in the main repos.

---

### Post by mastablasta on 2010-12-22
hmm it seems something is wrong here as alsaconf is supposed to configure your soundcard that ALSA will use. 
 
here is a good description of what it does:
[http://linuxmanpages.com/man8/alsaconf.8.php](http://linuxmanpages.com/man8/alsaconf.8.php)
 
> DESCRIPTION
This manual page documents briefly the alsaconf command. This manual page was written for the Debian distribution because the original program does not have a manual page. 
 
Alsaconf is a simple shell script which tries to detect the sound cards on your system and writes a suitable configuration file for ALSA. It will try to guess what GNU/Linux distribution you're running, and will act accordingly to the standards of that distribution, if specific support is available. Alsaconf will write a modutils snippet which can be then used by modutils to load the correct parameters for your sound card.
 
EDIT:
 
you could try and recompile alsa by following this guide (made for ubuntu 10.04):
[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

---

### Post by Lateralis on 2010-12-31
The plot thickens!  

I haven't done anything like recompile ALSA yet, but I tried to install something using Wine.  As it happens, the install didn't work, but the installer has some music which plays in the background - that played out of the front speakers!  I did try to suppress the sound by using the laptop's mute hotkey but the music still played.  

When I get back home after New Year I will have a go at recompiling ALSA, but I will also investigate Wine in case there is some weirdo conflict. 

Thanks to everyone for your replies so far too. =)  

And a happy New Year to you all!

---

