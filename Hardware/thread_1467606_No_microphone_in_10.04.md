---
title: "No microphone in 10.04"
date: 2010-04-30
forum: Hardware
---

### Post by Espionage724 on 2010-04-30
(maybe the same in 9.04+ even)

on windows, my card is a Realtek HDA ALC883
on Mac, its just Intel HDA ALC883 (probably same on *nix)

On a complete install of ubunutu, I have audio that outputs fine to analog front speakers and the digital optical port. I have no input devices though :/

My idea was to compile or somehow install realtek's drivers from their site. Assistance?

---

### Post by Manyette on 2010-04-30
Simple one, but just in case, have you checked System -> Preferences -> Sound to see if the Mic is muted.  It was on my install.  Would also recommend you download Gnome-Alsamixer. Hope this helps.

---

### Post by kuric on 2010-05-01
Thanks.
Had the same problem and Gnome-Alsamixer did the trick.

---

### Post by Espionage724 on 2010-05-01
Idk what I checked but whatever it was (maybe Prefernces > Sound) it had no input devices shown, whereas it had Output devices shown.

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Espionage724 on 2010-05-02
Acer TravelMate 2480 with Intel HDA ALC883
(ill to terminal stuff in like 30mins to an hr)

---

### Post by lidex on 2010-05-02
Hmm. That's it?? Guess you'll have a problem with this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=acer  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default.

---

### Post by Espionage724 on 2010-05-02
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

```
Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

```
Advanced Linux Sound Architecture Driver Version 1.0.21.
```

```
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC883

==> /proc/asound/card0/codec#1 <==
Codec: LSI Si3054
```

---

### Post by lidex on 2010-05-02
Great. Please mark the thread as solved using 'Thread Tools' up top.

---

### Post by Espionage724 on 2010-05-02
My issue wasn't solved though, I still don't have a microphone :/

---

### Post by lidex on 2010-05-02
Sorry, was reading your sig. :rolleyes:
Did you **reboot** and go into alsamixer and select capture devices?
You may want to try gnome-alsamixer as well and enable all the options in 'Edit>Sound Card Properties'

How many analog audio jacks do you have? Digital (spdif)?

---

### Post by Espionage724 on 2010-05-02
Headphones/SPDIF (in 1 port), Internal speakers and thats it as far as I know.

Theres 2 other jacks on the front of my laptop, one is microphone, and the other one is unknown lol. It looks sort of like ((*)) (the port picture, the * is a circle)

---

### Post by lidex on 2010-05-02
So, if the acer option didn't work, remove it and try these instead, ***one at a time only***:

```
options snd-hda-intel model=3stack-dig 
options snd-hda-intel model=3stack-2ch-dig 
options snd-hda-intel model=3stack-6ch-dig 

```
Remember to reboot each time and check alsamixer.

---

### Post by Espionage724 on 2010-05-02
Ok maybe I didn't do enough testing.

When I put it in analog mode, I get microphone, and I must select Microphone 1 to use the external mic, Microphone 2 for internal, and Line for.. line lol.

I had it in just Digital mode, which didn't have any inputs. But then I noticed the Digital + Analog Input mode (which I'm surprised I didn't notice before). I selected that and I have my sound going through my optical port, and input via whatever microphone I want.

Btw the acer thing made things maybe worse, because I lost the digital option (it only had Analog choices). I think I got mic back with that too, I didnt see though.

Thanks for the help though :D

---

### Post by jeSah8ci on 2010-08-22
I had the same issue here, but I discovered that what was wrong in my case was the 'profile' in the Sound Preferences > Hardware tab.

I don't know why, but the Analog Stereo Output profile was selected, instead of the Analog Stereo Duplex (in my case).

Selecting Analog Stereo Duplex displayed the connectors in the Input devices.

---

