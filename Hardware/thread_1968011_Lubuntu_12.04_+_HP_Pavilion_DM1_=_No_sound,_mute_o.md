---
title: "Lubuntu 12.04 + HP Pavilion DM1 = No sound, mute off."
date: 2012-04-28
forum: Hardware
---

### Post by aJacom on 2012-04-28
Hello everyone. I'm sorry if this is a double post, or if I posted it in a wrong section. 

I have looked a lot for the solution, and I asked around in IRC also, but no one could help me, because it seems its not a quick solution, and I couldn't see any solution in the forums either.

**The lubuntu installation has no sound. **

These solutions have not worked.
- [http://askubuntu.com/questions/106224/no-sound-after-lubuntu-installation](http://askubuntu.com/questions/106224/no-sound-after-lubuntu-installation)
- In IRC people told me that it was the mute settings from alsamixer. This was not it.

Lubuntu version is 12.04 32bits. 

Thanks :)

---

### Post by marinara on 2012-04-29
there's a troubleshooting guide on the wiki.  It's difficult but it always works

---

### Post by aJacom on 2012-04-29
Hi.

I followed the guide. 

- I have checked codec compatibility in [https://wiki.ubuntu.com/Audio/HDAGeneric](https://wiki.ubuntu.com/Audio/HDAGeneric). It is supported.
-  I have checked that everything is correct in the alsamixer, following these instructions: [https://wiki.ubuntu.com/Audio/Alsamixer](https://wiki.ubuntu.com/Audio/Alsamixer)
- linux-alsa-driver-modules does not show up in Synaptic after adding ppa:ubuntu-audio-dev/ppa. apt-get install linux-alsa-driver-modules-$(uname -r) also did not had results. This was according to [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Also, as posted [here]("http://forum.lxde.org/viewtopic.php?f=8&t=31254&p=38853#p38853"), someone suggested I uninstalled pulse. It wasn't installed. I uninstalled libpulse0 but it didn't work either.

Here's the output of lshw -c sound:

```

PCI (sysfs)  
  *-multimedia:0          
       description: Audio device
       product: Wrestler HDMI Audio [Radeon HD 6250/6310]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:42 memory:90244000-90247fff
  *-multimedia:1
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 40
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=snd_hda_intel latency=64
       resources: irq:16 memory:90240000-90243fff

```

And $ lspci | grep Audio :

```

00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310]
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)

```

---

### Post by marinara on 2012-04-29
did you follow this guide?  [https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_17](https://help.ubuntu.com/community/SoundTroubleshootingProcedure#Step_17)

usually when i get to step 17 everything works

---

### Post by ts3 on 2012-04-29
> **aJacom said:**
> Here's the output of lshw -c sound:

And $ lspci | grep Audio

Hi, I have an HP dm1 laptop and ran the same lshw and lspci to compare.  The outputs are the same apart from the resources line in multimedia0 and the configuration (same driver, different latency) and the resources lines in multimedia1.  

For what it's worth, on my laptop when I click on the little volume icon in the panel (I run Ubuntu, it might be different on lubuntu) I get no sound if the slider is more than one-third close to the left-hand end.  Sorry, I'm not describing it well: basically, even with the mute off, there is a sharp cut off rather than a gradual decrease in volume.  So basically, if the slider is anywhere between 0% and 30%, even if it is say 29% there is no sound at all even though it looks like there should be.  If the slider moves to say 31% the music starts playing loudly.  Might be worth trying moving the volume/sound slider (or whatever the lubuntu equivalent is) say to the half point and see what happens.

Given all the troubleshooting you've done this is not likely to be the cause but I thought I'd mention it just in case :) I have ubuntu and other distributions on different hardware and have never come across the same sound quirk except for the hp dm1 laptop.

---

### Post by aJacom on 2012-04-30
Hi.

Marinara, I believe I was checking at the wrong Troubleshooting Guide.

This was the solution: [http://forum.lxde.org/viewtopic.php?f=8&t=31254#p38854](http://forum.lxde.org/viewtopic.php?f=8&t=31254#p38854). (partly)

"Be sure that pavucontrol, pulseaudio, pulseaudio-utils and libgtk-3-0 are all installed. Then play with the different settings in pulseaudio volume control and the controls in your player until you get sound. http://douwil7.100webspace.net/linux/Tuning.html#17"

I had uninstalled pulse like someone suggested in that same forum, but that didn't work. Only installing pulse gave me my sound back.

**EDIT:**
That solved the issue, partly.

I have sound now ( :) ), but the sound is coming off really bad, with quirks and "dirty".

---

### Post by marinara on 2012-05-01
i just tried to add your helpful hint to the wiki, but it seems to be down.  glad you got sound to work.  really i'm a bit impressed

---

