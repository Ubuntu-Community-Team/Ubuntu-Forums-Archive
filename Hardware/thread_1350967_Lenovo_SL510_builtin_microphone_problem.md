---
title: "Lenovo SL510 builtin microphone problem"
date: 2009-12-09
forum: Hardware
---

### Post by komesh11 on 2009-12-09
Hello,

I have recently acquired a Lenovo SL510 notebook. I have installed Ubuntu Karmic, everything seems to work fine except the builtin microphone. Any assistance would be appreciated.

thanks!

Here's some info about the laptop:

laptop:~$ uname -a
Linux laptop 2.6.31-16-generic #52-Ubuntu SMP Thu Dec 3 22:00:22 UTC 2009 i686 GNU/Linux

laptop:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

laptop:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Lenovo Device 20f2
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at f2a00000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-i

ALSA information:

!!Linux Distribution
!!------------------

Ubuntu 9.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.10"


!!DMI Information
!!---------------

Manufacturer:      LENOVO
Product Name:      2847CTO


!!Kernel Information
!!------------------

Kernel release:    2.6.31-16-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.20
Utilities version:  1.0.20


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf2a00000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

Complete output at:
[http://www.alsa-project.org/db/?f=34e9422de572d2e153cb773f58d4b252dbcee180](http://www.alsa-project.org/db/?f=34e9422de572d2e153cb773f58d4b252dbcee180)

---

### Post by vduck on 2010-01-09
Komesh, I also have a sl510 thinkpad running karmic, and this is a little off topic, but ... how did you get the laptop display working? This is driving me nuts!

---

### Post by kubik007 on 2010-01-26
MIC problem:
Did you tried to switch internal/external mic?

This was new to me as well, you need to select internal or external source, for example "alsamixer" in terminal, the hit tab to see input sources.


Display problem:
I have SL510 and I didnt have any problems, but I have seen reports, that during the installation, external display is used instead of notebooks LCD. Try to install with monitor or try different Live CD.

Regards, Petr

---

### Post by john_brown_jr on 2010-02-17
you need to switch to the development version of ALSA drivers:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/523522](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/523522)

---

### Post by henius on 2010-02-26
Yeah! Tell me dude I was trying to install ubuntu 9.10 64bit on my lenovo sl 510, but display didnt work...i have hd 4500 intel inside....I have conected big screen 22inch monitor so i could made all updates ....But the screen still doesnt work...Can please someone HELP me...Couse right now im on OPENSUSE becouse of this bug... :(

---

### Post by sabya24 on 2010-04-10
> **henius said:**
> Yeah! Tell me dude I was trying to install ubuntu 9.10 64bit on my lenovo sl 510, but display didnt work...i have hd 4500 intel inside....I have conected big screen 22inch monitor so i could made all updates ....But the screen still doesnt work...Can please someone HELP me...Couse right now im on OPENSUSE becouse of this bug... :(

I got a lenovo sl510 recently and was thinking which distro to install...i tried running 64 bit ubuntu 8.10 live CD but like you, i got no display...which version of openSUSE are you running and is it KDE or Gnome? which distro will run best out of the box without needing too many changes? thanks in advance.

---

### Post by lidex on 2010-04-11
You'll want to investigate alsamixer as stated previously. The terminal command:
```
alsamixer
```

But firstly, go here and follow directions to install alsa-backports:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

