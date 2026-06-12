---
title: "SB Audigy drivers for Ubuntu?"
date: 2009-10-18
forum: Hardware
---

### Post by CardPlay3r on 2009-10-18
Hi everyone, I have an Audigy 24 bit sound card and 5+1 Logitech X-530 speakers. They work well under Vista, but in Ubuntu only the front speakers emit sound. I suspect Ubuntu doesn't see the card's 5.1 capability.


In the sound settings, there are 4 options for Audigy SE [SB0570] CA0106 (ALSA) and I selected one of them. The weird thing is when I click the Test button only the **middle** speaker is heard, although with any settings when I play a song only the front speakers are heard.



Are there any drivers for Ubuntu, or maybe someone can help me with the settings - I couldn't get it to work? Or maybe there will be a fix in Ubuntu 9.10? Thanks!

---

### Post by PorkyPie on 2009-10-18
You might want to check this out: [http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx](http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx)

---

### Post by CardPlay3r on 2009-10-18
> **PorkyPie said:**
> You might want to check this out: [http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx](http://connect.creativelabs.com/opensource/Wiki/SoundCard%20Support.aspx)

Thanks, but I don't have X-Fi I have Audigy :-(

They say AUdigy is supported, and it does appear as the driver enabled in sounds, but I still can only hear the front speakers...

---

### Post by dummy910 on 2009-10-18
> **CardPlay3r said:**
> Thanks, but I don't have X-Fi I have Audigy :-(

They say AUdigy is supported, and it does appear as the driver enabled in sounds, but I still can only hear the front speakers...

Wait, you missed the **Alsa Matrix Link** on this page that has [color=red]info-how-to's for most soundblaster cards[/color].

Matrix:**Vendor-Creative Labs**
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

---

### Post by CardPlay3r on 2009-10-25
> **dummy910 said:**
> Wait, you missed the **Alsa Matrix Link** on this page that has [COLOR=red]info-how-to's for most soundblaster cards[/COLOR].

Matrix:**Vendor-Creative Labs**
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)

Thanks dummy. In that list I don't see SB0507, which a sysinfo tool in windows detected my card to be. Does that mean I'm screwed? :(

Really hoping 9.10 will fix this...

---

### Post by IcarusR on 2009-10-25
Check out this thread, yes it is old but for diagnostic purposes still applies....

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by Paul D on 2009-11-05
None of these how to help links are doing it for me. I have audigy2 sound card, new install of 9.10 ubuntu studio. No audio. Not muted, and the volume slider is up.

aplay -l shows me;
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0........blah blah

What is the [Unknown] in there?
It continues to list a bunch of subdevices past that, each time showing the [unknown] deal. As you can see I got the emu10k1 deal in there, I assume it is correct for this card. Am I supposed to do something with the SB0570 or CA0106 things as well? I have seen other names like that too for soundblaster on these "Help" websites.

If I do the modinfo soundcore, I get;
filename:       /lib/modules/2.6.31-9-rt/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     3A50BBE947364A4D9DB6A97
depends:        
vermagic:       2.6.31-9-rt SMP preempt mod_unload modversions 586

I guess that looks good?

If I do a grep 'audio' /etc/group
I get;
audio:x:29:timidity,pulse,paul1

I guess that looks good too? Though I don't know what timidity is.

My sound preferences from the speaker deal on the top of the desktop shows me no hardware, it just shows "Internal audio 1 output/1input analog stereo duplex". The output tab shows the same.

The Jack patchbay program thing shows the SB AUDIGY 2 in the left window along with other midi thing, then the emu10k1 along with other stuff in the right window. I have tried making connections between the columns of items listed there, but I don't know what I am doing.

Not to threaten anyone here, but I am loosing my energy to mess around with this. I will give it another week, then I will have to go back to XP. I have already been goofing with this for 1 week. I want it to work.

---

### Post by CardPlay3r on 2010-01-18
Sorry for bumping this, but I haven't posted and just wanted to say that 9.10 solved it for me...

---

