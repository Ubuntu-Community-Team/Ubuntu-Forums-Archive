---
title: "PulseAudio will not work with Bluetooth speakers"
date: 2014-03-01
forum: Hardware
---

### Post by ben_jetson2 on 2014-03-01
I just bought a new set of Bluetooth speakers to replace my old ones. The old ones used the regular green audio jack on the rear panel of the tower to connect, and always worked. The bluetooth speakers work sometimes, but other times, they do not. When they are not working, even if I pulg in a regular pair of speakers (regular green audio jack), they do not work either, and no devices show up in the sound settings page (screenshot below). There is no pattern as to when this occurs, and the only way to fix it is to completely uninstall and purge pulseaudio, reinstall it, and then reboot. If I run "pacmd list-cards" it outputs "Daemon not responding."

Below are screenshots of audio settings and the tray icon while the speakers are not working.
Tray icon: [IMG]http://i.imgur.com/UTu1d3o.png[/IMG]

Sound Settings:
[IMG]http://i.imgur.com/cF0pyuk.png[/IMG]

Any ideas on how to get the bluetooth speakers to work? Any help is greatly appreciated. :) -Ben

---

### Post by ben_jetson2 on 2014-03-01
I forgot to post my system specs/hardware info:

Compaq SR2170NX
Ubuntu 12.10 Desktop (System originally had Vista Home Basic on it)
1.7GB RAM, 2.9 GB Swap
Processor: Intel® Pentium(R) 4 CPU 3.00GHz × 2 
Bluetooth Adapter: Iogear USB Micro Adapter (Model # GBU521W6)
Bluetooth Speakers: Cyber Acoustics CA-3092BT

---

### Post by qunungnauraq on 2014-03-02
I would try a different usb bluetooth adapter and see what happens.

---

### Post by ben_jetson2 on 2014-03-02
Thanks for the reply. Unfortunately, I do not have another USB bluetooth adapter lying around, but I have tested the speakers with my Nexus 7 and Moto X, and they work fine with both. The bluetooth adapter works fine with my other devices, sending/recieving files, etc. For some reason, whenever the speakers connect, pulseaudio just freezes. I do have "pulseaudio-module-bluetooth" installed, so the speakers should work. Do you have any other ideas? :)

---

### Post by ben_jetson2 on 2014-03-03
I'm still having trouble with the Bluetooth speakers. Anyone have any ideas? :)

---

