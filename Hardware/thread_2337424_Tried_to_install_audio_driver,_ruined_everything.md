---
title: "Tried to install audio driver, ruined everything"
date: 2016-09-18
forum: Hardware
---

### Post by Spae on 2016-09-18
SO my USB headphones were working fine. I wanted my desktop speakers to work also. They are connect to the audio jack. My soundcard is [COLOR=#333333][FONT=&quot]ALC892.

I downloaded the driver from realtek and followed the install instructions. Gave me errors and didn't work. So I forgot about it. Now after turning on my pc my headphones no longer work, all that's listed in sound settings now is dummy output. I have no sound at all, not even by usb.

My audio was working fine on ubuntu 14, I fresh installed 16 due to errors while trying to upgrade so I lost all of my installed drivers.

Any ideas?[/FONT][/COLOR]

---

### Post by Yellow Pasque on 2016-09-18
Uninstall the realtek driver and reinstall the linux-image package. That should get you back to stock audio module.

Then reboot and get more info:
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by ian-weisser on 2016-09-18
> **Spae said:**
> [COLOR=#333333][FONT=&amp]I fresh installed 16 due to errors while trying to upgrade so I lost all of my installed drivers.[/FONT][/COLOR]

Most release-upgrade errors are due to non-Ubuntu software. Uninstall that software and return your system to as close to stock as you can, and you can prevent most of those errors.

It's easy and, thanks to apt, takes only an extra minute or two. Saves hours over a reinstall.

---

### Post by Spae on 2016-09-18
> **Temüjin said:**
> [COLOR=#000000]Uninstall the realtek driver and reinstall the linux-image package. That should get you back to stock audio module.[/COLOR]
 Well I tried really hard to find information on how to do that but I couldn't. So I will be grateful if you explain that or link me to some documentation.

> **ian-weisser said:**
> Most release-upgrade errors are due to non-Ubuntu software. Uninstall that software and return your system to as close to stock as you can, and you can prevent most of those errors.

It's easy and, thanks to apt, takes only an extra minute or two. Saves hours over a reinstall.
 I'll definitely try to do that next time. Although I usually don't install very much software, I wonder what it was.


edit:
Also I did check the realtek folder for uninstall information but there isn't any

---

### Post by Yellow Pasque on 2016-09-18
How did you install the realtek driver? If you ran make install, then go into the directory you did that from and this will probably do it:
```
sudo make uninstall
```
Then:
```
sudo apt-get install linux-image-`uname -r`
```
The previous command uses backticks, so copy/paste if you don't know what those are..

---

### Post by Spae on 2016-09-18
Ok thanks, I did make uninstall.
As for the linux image, It said I was already at the latest version, and that there was nothing to install, update etc.

Edit forgot to mention that my usb sound still isn't working and it only has dummy output listed.

---

### Post by Yellow Pasque on 2016-09-19
My fault. I forgot  --reinstall switch:
```
sudo apt-get install --reinstall linux-image-`uname -r`
```

---

### Post by Spae on 2016-09-19
Done. It still only lists dummy output unfortunately.

---

### Post by Yellow Pasque on 2016-09-19
I assume you rebooted?
Time to get more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

