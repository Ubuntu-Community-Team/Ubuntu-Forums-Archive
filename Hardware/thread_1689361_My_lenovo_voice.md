---
title: "My lenovo voice"
date: 2011-02-16
forum: Hardware
---

### Post by Dimesh on 2011-02-16
Al Slamo Aleekom

and HI everyone,
-------------------

the problem not with ubuntu only,
without using my head-phone, any voice comes out from my laptop  but when using head-phone, in fedora the voice comes out from laptop and head-phone at the same time,and ubuntu does not respond to headphone,


note:
the headphone works on windows.

---

### Post by Dimesh on 2011-02-16
?

---

### Post by lidex on 2011-02-16
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Dimesh on 2011-02-17
```
Automatically upload ALSA information to [www.alsa-project.org?](www.alsa-project.org?) [y/N] : y
Uploading information to [www.alsa-project.org](www.alsa-project.org) ...  Done!

Your ALSA information is located at [http://www.alsa-project.org/db/?f=6873ca8fb851c004ba8bdc9caa9e9587dd8390cf](http://www.alsa-project.org/db/?f=6873ca8fb851c004ba8bdc9caa9e9587dd8390cf)
                                                                                                                                      
Please inform the person helping you.
```

---

### Post by Dimesh on 2011-02-17
?

---

### Post by Dimesh on 2011-02-17
Can any one help i can not work with this problem please.

---

### Post by lidex on 2011-02-18
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
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by Dimesh on 2011-02-18
Realy, my Tongue can't say anything for you Mr.lidex , just thanks and hope to God guides you.

I just did those lines:
> sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)


**[COLOR="DarkRed"]It works[/COLOR]**

---

### Post by lidex on 2011-02-18
Good stuff. Please mark the thread solved using 'Thread Tools' up top.

---

