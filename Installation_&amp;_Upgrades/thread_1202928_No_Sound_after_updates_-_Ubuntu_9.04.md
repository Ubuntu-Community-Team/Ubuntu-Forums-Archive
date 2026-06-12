---
title: "No Sound after updates - Ubuntu 9.04"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by edantes on 2009-07-02
After installing a few updates, my sound system stopped working.  Not sure of exact cause or chain of events, but the result is that all I get are clicking noises when System->Preferences->Sound selects "Autodetect" or "ALSA".  I still get the correct test tone when I select the "OSS Analog" interface.

Question for our kind hearted readers:  How can I restore the default sound infrastructure I was using before?  Everything still works if I boot from the Ubuntu 9.04 CD.  I tried reinstalling packages from ALSA and PulseAudio without success.

Thanks in advance for your suggestions.

A bit of extra information:

lspci  | grep -i audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by wcorey on 2009-08-02
I have experienced precisely the same problem with 9.04, except I would describe the sound more as a static noise rather than clicking. I am running the 64 bit version of 9.04 on a Dell XPS 720.

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by mkultra42 on 2009-10-03
Add me to the list of people this has happened to. Installed some updates and lost all sound output capabilities.

---

### Post by MisterBill on 2009-10-03
Add me to the list -- this "things stop working when you do a kernel update" nonsense has GOT to stop -- come ON Canonical, if you guys are pretending to run a serious competitor to Window$ you simply cannot allow these kinds of poor quality control problems to persist. :confused:

My output :

lspci | grep -i audio

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

This is Ubuntu 9.04 (Jaunty) on a HP Pavillion DV 6000 laptop, by the way.

I cannot get the "Test Sound" to play no matter what I do. I am going to try booting into the last kernel and see what happens then, but I am very disappointed with the non-existent quality control being exercised by Canonical.

-------------------------------------------------------

Edit : Re-installed PulseAudio via Synaptic and now it works again... but I never should have had to go through this in the first place.

Incidentally, I also discovered that my instance of Jaunty is NOT keeping a revision history of previous kernels that I can boot into via GRUB -- this is unlike that I had encountered under Intrepid and it is disconcerting, I am aware that these old kernels do take up some disk space but it is a comforting safety factor to have. Does anybody know how to tell Ubuntu to retain the old kernels / configs, when it updates to a new version?

---

### Post by mkultra42 on 2009-10-03
I have found the solution. I posted [[COLOR="Magenta"][COLOR="Blue"]a new thread[/COLOR][/COLOR]]("http://ubuntuforums.org/showthread.php?t=1281248") regarding the issue and was told that after any kind of update I would need to re-install any drivers that I installed manually.

In my case I installed the drivers for my Soundblaster x-fi Gamer.

[[COLOR="Blue"]Here's a guide for those with a Soundblaster X-ficard.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=870001&highlight=Howto+xfi")

Reinstalling my drivers fixed the issue. If you are using manually installed drivers hopefully this will solve the issue for you also.

---

