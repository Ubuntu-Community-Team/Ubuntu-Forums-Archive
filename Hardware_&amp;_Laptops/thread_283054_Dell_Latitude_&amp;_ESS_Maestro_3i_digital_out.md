---
title: "Dell Latitude &amp; ESS Maestro 3i digital out"
date: 2006-10-23
forum: Hardware &amp; Laptops
---

### Post by jankowskid on 2006-10-23
I have 2 older Dell Latitudes (C800 & CPx).  Both machines contain a proprietary ESS Maestro 3i from Dell, and have a tv/audio dongle of sorts that supply 3 connections (S-video out, Composite video out, Digital Audio Out - coaxial).  I have tried both machines, and the digital audio port is never detected by the os.  Also it doesn't even show up as a separate device from a "aplay -l" command.  I have gotten the TV functions of the dongle working fine.  

How do i force it, or is the 2nd subdevice my digital out and i don't know it?

Is it even possible since it is proprietary Dell stuff?

I am trying to use this with my 7.1 home theatre setup, so I would be greatful of any information posted, thanks....

Here is some info.  


lsmod | grep snd
snd_maestro3           27780  2 $ sudo nano /var/log/syslog
snd_ac97_codec        102820  1 snd_maestro3
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47232  0
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84996  3 snd_maestro3,snd_ac97_codec,snd_pcm_oss
snd_timer              24964  1 snd_pcm
snd_page_alloc         11656  1 snd_pcm
snd                    60548  10 snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd


sudo cat /proc/asound/devices
  2:        : timer
  3: [ 0- 0]: digital audio playback
  4: [ 0- 0]: digital audio capture
  5: [ 0]   : control


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCI [ESS Maestro3 PCI], device 0: Maestro3 [Maestro3]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

---

### Post by mpc823_99 on 2006-12-06
While I can't help you with your digital audio problem, perhaps you can help me. I have an old Dell Latitude CPx with the funky dongle. I'm trying to get the composite and S-Video out to work. How did you do it?

Thanks,
Daniel

---

### Post by jankowskid on 2006-12-06
[http://www.thinkwiki.org/wiki/Atitvout]("http://www.thinkwiki.org/wiki/Atitvout")

you might have to poke around to find the actual download, but it works...Good Luck!

---

### Post by Navdeep on 2007-09-11
how did you get the audio to work, i have no sound from ubuntu in my dell 8000 which is running ubuntu, it also has the ess maestro 3 pci?  I have not been able to get any audio at all.

---

