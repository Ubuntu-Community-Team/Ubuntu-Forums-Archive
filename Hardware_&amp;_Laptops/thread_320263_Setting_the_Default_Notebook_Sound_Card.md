---
title: "Setting the Default Notebook Sound Card?"
date: 2006-12-17
forum: Hardware &amp; Laptops
---

### Post by raid517 on 2006-12-17
Hi I have a Toshiba Satellite A100-225 laptop and am running Kubuntu 6.10.

Anyway the thing is that my laptop has onboard sound which is an Intel HD Audio Chip (which I believe is based on a Realtek design). The chip for this card is called snd_hda_intel. However I also have an Audigy 2 ZS PCMCIA notebook card.  The driver for this card is called snd_emu10k1.

Originally with both cards active my Intel HDA card was being loaded as the default card. This was relatively easy to resolve (though not as easy as it should be) by following these guides:

[http://ubuntuforums.org/showthread.php?t=282175](http://ubuntuforums.org/showthread.php?t=282175)

[http://www.debianhelp.co.uk/sound.htm](http://www.debianhelp.co.uk/sound.htm)

This essentially involved entering the following code:

options snd_emu10k1 index=0
options snd_hda_intel index=1

Into these files:

/etc/modutils/options

/etc/modprobe.d/sound

In order to cause my Audigy card to be loaded first. (Which is my preference)

The first of these guides didn't work - however the second did - and my Audigy card is now listed as the default card under Kmix in KDE.

However unfortunately the *majority* (and by majority I mean all of KDE, all of my Media Players, the event notification system and pretty much everything really, is still defaulting to trying to playback via the onboard Intel HDA chip.

There are a couple of applications I can configure (like LastFM player) and tell them to explicitly use my Audigy card - and if I can do this the sound does play back normally and as expected.

However there are only a very few applications that will allow me to select my audio device in this way - and in any case, it is far from ideal as the ideal scenario would clearly to be able to use the Audigy card as my default system wide audio playback device - rather than just having a few applications use it, while the rest of the system uses the Intel chip.

There are a couple of conditions that might be wort considering in my attempts to get my set up to work.

Firstly I cannot simply turn the Intel chip off in my bios - as my laptop will not allow this. (I guess it was never envisaged that I might use a different sound card). Nor is this quite a solution as it does not resolve the ordering and default device dilemma that I am facing now. Secondly I cannot simply remove the module from /etc/modules so that it does not get loaded when I reboot - since most hardware detection is now done by HAL. Nor can I compile my kernel to remove the driver - as this has the undesirable effect of meaning that I cannot use my Intel chip at all. Nor would I want to do any of this - as there are several scenarios - where for example I may wish to remove my Audigy PCMCIA card and insert a TV card, or insert a PCMCIA SATA card (so that I can load an alternative OS) and still have sound without having to hack through various configuration files.

So predominantly all I want is to set my Audigy card as the default system wide card that all my applications will default to and my Intel chip as the fall back card that my system will revert to if the Audigy card is removed.

Can anyone suggest how I might achieve this?

I originally presumed that the above methodology would have achieved this, but this does not seem to have been the case. (And yes I did reboot after making these changes).

---

### Post by encompass on 2006-12-17
Never finished your post... you where rather wordy..
But this may help... did it for me and my 3 cards.

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
btw... it is a sticky in the video and sound section.

---

### Post by raid517 on 2006-12-17
Yeah that is the guide I followed if you had read the post.

Sorry about the length - but it is all just necessary information if you wish to understand what I am trying to do.

I can't see any way to shorten it.

---

### Post by digbybare on 2007-04-10
I'm having a very similar problem with my Creative Audigy 2 ZS Notebook on a Dell Inspiron 600m. I'm running Xubuntu.

Here's what I got for "sudo lspci -v":
```

02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 1020
        Flags: bus master, medium devsel, latency 32, IRQ 5
        Memory at faffd000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

03:00.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Unknown device 2001
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at d000 [size=64]
        Capabilities: [dc] Power Management version 2

```

my /proc/asound/modules:
```

 0 snd_intel8x0
 1 snd_emu10k1

```

All my sound is being directed through the onboard Intel card instead of my Audigy. Also, I checked the [http://ubuntuforums.org/showthread.php?t=205449&highlight=audigy+2+notebook](http://ubuntuforums.org/showthread.php?t=205449&highlight=audigy+2+notebook) . I followed the instructions, purged alsa and reinstalled it, but there's no change. Also, when I try to run alsaconf it gives me the error:
```
bash: alsaconf: command not found
```

So, what should I do?

---

