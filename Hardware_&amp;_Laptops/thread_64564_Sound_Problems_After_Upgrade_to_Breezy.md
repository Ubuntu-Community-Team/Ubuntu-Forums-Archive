---
title: "Sound Problems After Upgrade to Breezy"
date: 2005-09-11
forum: Hardware &amp; Laptops
---

### Post by gunderwood on 2005-09-11
I recently upgraded my Hoary installation to Breezy by using dist-upgrade. My sound worked fine in Hoary but I am unable to get it to work in Breezy. It appears that the onboard sound (Intel ICH6 AC 97 Audio) is correctly detected and that the necessary drivers have been loaded. I've searched through the forums, mailing lists and docs and am unable to find anything that helps. 

I attempted the sound fix detailed at [ubuntuguide.org/#configuresoundproperly](http://) 
so my configuration is the same as in the howto.

All of my sound levels are unmuted in alsaconfig. I've tried setting the sound daemon in System > Preferences > Multimedia System Selector to ALSA and ESD (currently set to ESD). This is the output from an audio debugging script from the ALSA website to discover pertinant data about my hardware and drivers.

```

ALSA Audio Debug v0.0.9 - Sun Sep 11 09:14:46 PDT 2005
http://alsa.opensrc.org/?page=aadebug

Kernel ----------------------------------------------------
Linux ubuntu 2.6.12-8-386 #1 Tue Aug 30 22:41:30 BST 2005 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_atiixp_modem       15396  0 
snd_via82xx_modem      14500  0 
snd_intel8x0m          16836  0 
snd_intel8x0           30016  5 
snd_ac97_codec         71804  4 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0
snd_pcm_oss            46368  0 
snd_mixer_oss          16128  3 snd_pcm_oss
snd_pcm                78344  7 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  17 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10120  5 snd_atiixp_modem,snd_via82xx_modem,snd_intel8x0m,snd_intel8x0,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.9 (Sun May 29 07:31:02 2005 UTC).
0 [ICH6           ]: ICH4 - Intel ICH6
                     Intel ICH6 with unknown codec at 0xb0040800, irq 11
 20: [0- 4]: digital audio playback
 27: [0- 3]: digital audio capture
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
00-00: Intel ICH : Intel ICH6 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel ICH6 - MIC ADC : capture 1
00-02: Intel ICH - MIC2 ADC : Intel ICH6 - MIC2 ADC : capture 1
00-03: Intel ICH - ADC2 : Intel ICH6 - ADC2 : capture 1
00-04: Intel ICH - IEC958 : Intel ICH6 - IEC958 : playback 1

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1c  pcmC0D2c  pcmC0D3c  pcmC0D4p  timer

CPU -------------------------------------------------------
model name	: Intel(R) Pentium(R) M processor 1.60GHz
cpu MHz		: 598.796

RAM -------------------------------------------------------
MemTotal:       507284 kB
SwapTotal:      996020 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)

```

When I run 
$aplay -l
I get the following output. 

```
 
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Any help with this issue would be greatly appreciated.

---

