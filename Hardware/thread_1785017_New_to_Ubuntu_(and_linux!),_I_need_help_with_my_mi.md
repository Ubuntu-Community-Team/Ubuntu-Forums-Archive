---
title: "New to Ubuntu (and linux!), I need help with my microphone"
date: 2011-06-17
forum: Hardware
---

### Post by sarahmichele on 2011-06-17
So I am completely new to linux, (installed 2 days ago on a new PC, I am an old mac user, but my beautiful new macbook pro had some mystery water damage that fried just about everything, thanks sister's boyfriend). This all happened at a very convenient time, as I am trying to study for my C++ final.. Good time to learn some new computer stuff and distract me, right???

Anyhow, I seem to be having issues with my internal microphone. It doesn't work. I have tried all of the google-fu I could, have tried about 8 different suggestions, and nothing is fixing this issue. I don't know what info to provide in order to make this easier to help me, I'm on a Compaq Presario CQ62, running well, whatever version of ubuntu was available to me 2 days ago.

Please help!

---

### Post by sakishrist on 2011-06-17
Hello there,

One thing you could try is clicking on the volume icon and then selecting "Sound Preferences". Then you have to go to input and make sure the correct microphone is selected. Also make sure it's level is not too low.

Another thing would be to open a terminal (ctrl + alt + T) and type "alsamixer". Then press F4 for the input devices and play around with the settings a bit (I am not telling you what settings to make because every PC has different options).

You could also try the "gnome-alsamixer" (again you can open a terminal and type it, if you do not have it installed it will help you by showing you what to type to install it). It is basically the same thing as alsamixer but with a more user-friendly UI. It might be a bit more clear which microphone is selected.

Good luck!

---

### Post by sarahmichele on 2011-06-17
I have tried all of those things. alsamixer (and gnome alsa mixer) show my mic boost at the highest level, nothing is muted.

In sound preferences, I have "internal microphone" selected, and it does not show any level of input at all from my mic.

---

### Post by lidex on 2011-06-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by sarahmichele on 2011-06-18
[http://www.alsa-project.org/db/?f=d596c35e43c0a62ff160d6e5dcf19ee7302f0b95](http://www.alsa-project.org/db/?f=d596c35e43c0a62ff160d6e5dcf19ee7302f0b95)

---

### Post by lidex on 2011-06-18
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Check your levels in alsamixer.

---

### Post by sarahmichele on 2011-06-18
AH finally! It's definitely fixed now. Thank you so much!!!

---

