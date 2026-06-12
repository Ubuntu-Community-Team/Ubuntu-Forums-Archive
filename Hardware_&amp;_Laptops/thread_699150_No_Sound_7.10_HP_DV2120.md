---
title: "No Sound 7.10 HP DV2120"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by Nauj on 2008-02-17
Looking for some help with a fresh install of gutsy. I have an HP DV2120 with everything working except the sound.

MCP51 HD Audio

aplay -l shows:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

devices are there.. no configuration will work.

---

### Post by Yellow Pasque on 2008-02-17
First, try this:
```
sudo aptitude install linux-backports-modules-generic
```

If that doesn't work, try the attached scripts. They'll grab the latest version of ALSA. Just save it to your desktop and go into a terminal. Then run:
```
cd ~/Desktop
sudo chmod 777 alsa_1.sh
sudo chmod 777 alsa_2.sh
sudo sh alsa_1.sh
```
That will do the bulk of the work. Then you'll have to reboot and run the second one:
```
cd ~/Desktop
sudo sh alsa_2.sh
```
Make sure you run alsamixer and unmute everything (except the inputs if you're not using them)

---

### Post by Nauj on 2008-02-17
That whole process seemed to have gone through without a hitch. The only problem now is that aplay -l shows:
 aplay: device_list:207: no soundcards found...

I do get an error beep however when i hold down the backspace in terminal which is more sound than i have had so far. Any further help would be greatly appreciated.

---

### Post by Nauj on 2008-02-17
been working on this issue for over 16 hours straight. i'm about to install a different distro and try my luck w/ that. knoppix had sound working fine earlier.

---

### Post by chavanak on 2008-02-17
Your sound card is not detected i guess

---

