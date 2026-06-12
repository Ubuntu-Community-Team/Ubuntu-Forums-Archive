---
title: "Ubuntu 11.10 - no sound on Panasonic Toughbook CF52"
date: 2011-11-22
forum: Hardware
---

### Post by smiggy on 2011-11-22
Hi all,

Just downloaded and installed on Panasonic Toughbook CF-52, no sound.
Have same problem on Mint 12RC, Fedora 16 and OpenSuse 12.1 too.

Card is an HDA Intel (AD1884).
I can get sound from headphones but speakers are no go.
In sound settings I only have 1 output connector 'headphones'?!

I've amended the alsa-base.conf file and added "options snd-hda-intel index=0 model=auto/panasonic/laptop/mobile" each in turn to test, all to no avail!
Alsamixer shows no mutes in force either so I'm of the opinion that this just isn't supported across these 3 distro's.
Pity as Mint is my preferred choice and had high hopes that it would install and work but never mind.

Just wondered if anyone else out there knows the 'fix', has a CF-52 with same problem and resolved or can shed any light on what's going on?

----------------------

#aplay -l reports:-

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 0: AD198x Digital [AD198x Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

Up to now I have tried the following from the hardware list: 

options snd-hda-intel model=xxxxxxx

desktop
laptop
mobile
thinkpad
touchsmart	
basic	
hp
toshiba
dell_desktop
6stack
3stack
laptop-eapd
laptop-automute
ultra
samsung
samsung-p50	
6stack-dig	
3stack-dig	
auto

----------------------

All models relating to AD198x tested:

options snd-hda-intel model=xxxxxxx

desktop
laptop
mobile
thinkpad
touchsmart	
basic	
hp
toshiba
dell_desktop
6stack
3stack
laptop-eapd
laptop-automute
ultra
samsung
samsung-p50	
6stack-dig	
3stack-dig	
auto	

All work via single analogue connector (headphone) output.
No output via speakers at all.
Not sure if adding index=0, into the "options snd-hda-intel index=0 model=xxxxxx" will help, bit loathed to spend another hour/half gedit alsa-base.conf and sudo reboot'ing to be honest!!

So, hardware is supported, but for some reason the speaker output cannot be generated.
Anyone, anyone, Bueller, Bueller.......................

:confused:

---

### Post by smiggy on 2011-11-26
<bump>!!

---

### Post by smiggy on 2011-11-30
Well have to say that Ubuntu forum support is excellent!
Not a single response to this post, guess I've uncovered something that highlights a serious flaw in Ubuntu's 'it just works' philosophy!

However much I detest Windows at least the ability to install drivers to specific bit of hardware works compared to this Pulseaudio rubbish.

Even better when you find that your specific AD1884 has N/A against it in the Alsa list.
There are postings all over then net relating to this, numerous bug reports filed in Ubuntu by other people in older Distro's and guess what, NO ANSWER!!
In one case they waited until the version became obsolete, then responded by advising that the Distro was no longer supported and closed the bug report. PURE GENUIS!

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/526201](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/526201)
[http://ubuntuforums.org/archive/index.php/t-1449314.html](http://ubuntuforums.org/archive/index.php/t-1449314.html)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/855830](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/855830)

My love affair with Ubuntu ends here.

---

