---
title: "nVidia HDMI audio device not showing up"
date: 2010-12-09
forum: Hardware
---

### Post by akameswaran on 2010-12-09
OK - basic information
Dell m6400 Dual Boot Win7/Ubuntu 10.04 (upgrading to 10.10)
Graphix = nVidia quadra 2700M - with latest drivers from nVidia, Dell only provides rhel drivers, and the ones in the Ubuntu repo were wicked old.
Intel Integrated Audio - analog

So HDMI Video Output works, and Intel audio analog works.

In windows 7, hdmi (ok really DisplayPort to HDMI) audio works just fine.  There are two audio devices registered in windows.

On Ubuntu, no such luck.  aplay -l and -L only show the intel audio device.  I've checked the nVidia readme and found no options regarding the audio device.  I know it's there since it works in windows.  

Does anyone know the module I should expect for nVidia audio over HDMI?  or the also module?  

Ubuntu wants to use pulseaudio - any thoughts on ripping it out and see if plain alsa will at least recognize the device?

---

### Post by akameswaran on 2010-12-10
OK - so ripped out pulse audio - nothing.

Discovered that I apparently need to have the snd-hda-codec-nvhdmi for this to work.  However, I can't modprobe it, I get an Invalid Argument error.  I can insert snd-hda-codec-hdmi - but it doesn't help.

SO I still have no device in lspci or aplay (yes one does sort of demand the other) except the onboard intel.  From my searching, I should have both the intel and nvidia sound device.  I'm about to try and rip everything out and reinstall the sound.

Oh I also went and got the latest Alsa driver modules, then just for S&G I recompiled the NVIDIA graphix driver using it's own script.  I'm about to rip everything relating to sound and reinstall.  I may even rip out the NVIDIA driver, and slowly work my way up through versions.  

This is truthfully retarded.  This machine is a year old.  The quadro seems a relatively common mobile chipset.  Obviously Dell is only going to help on RHEL (which they provide drivers for) I'm almost tempted to P2V my current ubuntu, and see if I can use HDMI audio through VMWARE on the Windows 7 side of things.  If that works, then I may just try RHEL 5.1 with the provided Dell drivers, just to try and figure out what alsa/driver versions work.  Not sure if that will have carryover.

I also really hope maybe...maybe somebody else has done this, or at least may have some clue how to get the right modules to actually load.

---

### Post by atlasx on 2010-12-21
I have the same issue.  I have a GeForce 8400 GS and aplay -l shows absolutely no HDMI audio for the NVidia.  No sound works.  Just wish it would have worked out of box.  I may also go to Fedora for this one and hope for better luck since I absolutely despise trying to troubleshoot and tinker with Linux audio.  If there's one thing Linux doesn't have right and have totally f*cked the dog on it's an audio system that makes sense and "just works".

-Atlas

---

### Post by pefdus on 2011-06-08
Hi akameswaran,

Did you find the solution in the end ? 

Back 2 years ago I had it working with a 8000 series GeForce. But for the life of me I think I just fluked it.

---

