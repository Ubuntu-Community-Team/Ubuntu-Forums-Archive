---
title: "repeating audio &quot;popping&quot;/beeping sound"
date: 2011-03-16
forum: Hardware
---

### Post by jingo_man on 2011-03-16
i have always had this issue and it is enormously frustrating! a sample of the standard noise is attached (recorded from an [[COLOR=darkgreen]iphone[/COLOR]]("http://ubuntugeek.com/forum/index.php/topic,4086.0.html#")  infront of the speakers, so its probably quieter that what i actually  hear). also to note that if an audio stream ends, no matter the source,  it can end up repeating the last fraction of whatever noise is made.

the  system is primarily a HTPC box in my lounge, running XBMC. i'm afraid  my girlfriend might murder me if this cannot be sorted!

i am  running ubuntu 10.04, with the svn xbmc build (though dont think i have  upgraded beyond the official dharma release, as they stopped the svn for  a while), and i followed this guide to configure the audio, which  upgrades ALSA and applies some specific Intel HDA config for my ASUS  P5N7A-VM [[COLOR=darkgreen]Motherboard[/COLOR]]("http://ubuntugeek.com/forum/index.php/topic,4086.0.html#"):

[http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation,_an_unofficial_Step-by-Step_Guide#Upgrading_ALSA_.28sound_driver.29_to_the_latest_version](http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation,_an_unofficial_Step-by-Step_Guide#Upgrading_ALSA_.28sound_driver.29_to_the_latest_version)

the  system was originally built on an earlier version of ubuntu and an  earlier xbmc, which have both been upgraded since within the O/S. i have also upgraded to ALSA 1.0.24 today, with no effect. maybe  newer features are available or newer configs are available?

it  makes this sound both within the XBMC (which it auto-boots into as its  own desktop session, rather than the desktop) but if i return the GNOME  desktop session, it still occurs.

the whole ALSA/PulseAudio thing  gets confusing. i assume i am using ALSA. can i use PulseAudio? are  there benefits, etc, of either?

i have run a bunch of the  commands i see available, like "aplay -l", "lsmod", etc. everything  looks ok. i have tried adding more options to the  modprobe.d/alsa-base.conf and rebooting. everything i have tried totally  kills audio (though atleast the popping stops!)

---

