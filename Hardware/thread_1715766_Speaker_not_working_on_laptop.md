---
title: "Speaker not working on laptop"
date: 2011-03-27
forum: Hardware
---

### Post by SerenitySS on 2011-03-27
I have installed Ubuntu v10.10
Installed on a Toshiba Protege which is not listed as a supported platform. :(
The laptop is has a Realtek audio card in it.
From some research in the forum, I dicovered that I needed the Realtek ALC262 Codec.
I downloaded the Realtek Linux Audiopack version 5.16 from their web site.
It installed the ALSA 1.0.24 version. I then added the libraries and utilities.
Then compiled the whole thing and ran make.
added the line "options snd-hda-intel model=toshiba-s06" to the end of the file "/etc/modprobe.d/alsa-base.conf"

If the volume level is at it's highest, I get sound from the headphone jack playing external speakers.
Otherwise the internal speakers just do not work.

I ran the command: sudo lshw -c sound
  *-multimedia            
       description: Audio device
       product: N10/ICH 7 Family High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:ffc3c000-ffc3ffff

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

Link to my ALSA report for my machine:
[http://www.alsa-project.org/db/?f=d70f07c534f8a39bbd31387388f1e57bb5013886](http://www.alsa-project.org/db/?f=d70f07c534f8a39bbd31387388f1e57bb5013886)

[COLOR=#000000][FONT=Times New Roman]!!ALSA Version
!!------------
Driver version:     1.0.23
Library version:    1.0.24.1
Utilities version:  1.0.23[/FONT][/COLOR]There is discrepancy between versions but..... 

At this point, I am scratching my head. I am relatively new to Ubuntu but really liking what I see.
Any information someone could provide to assist in fixing this issue?
I fear if I tinker with it any more, then I will simply mess it up without guidance.

Thank You,
Paul ( SerenitySS )

---

### Post by SerenitySS on 2011-04-02
After some additional testing I have a bad sound card.
Installed another OS and found the same issue.
Back to Ubuntu on the laptop and using an external speaker system.

Thank you for all details from the forum.

---

### Post by lidex on 2011-04-02
You have some wild and wacky configuration missteps. Possibly not a hardware issue??

---

