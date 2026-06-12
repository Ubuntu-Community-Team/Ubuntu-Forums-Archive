---
title: "no sound with alsa"
date: 2011-07-12
forum: Hardware
---

### Post by mrmc on 2011-07-12
hi 
i have problem. I have ubuntu 11.04 , i can listen sounds when i don't build alsa. I need to build this for pjsip. i built it then there is no sound and driver. I built alsa-driver, alsa-lib then alsa util.

---

### Post by lidex on 2011-07-15
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by jsgoodall on 2011-07-19
Same problem here, apparently with ALSA.

Sound icon appears in icon tray but no sound bars on it, sound control greyed out when I click on it. No sound either with speakers or headphones.

Thanks for any help you can give.

Here I post my output
[http://www.alsa-project.org/db/?f=3d495f489acc819d7e542befec0b9c43af010514](http://www.alsa-project.org/db/?f=3d495f489acc819d7e542befec0b9c43af010514)

---

### Post by loaba on 2011-07-19
I was having the same problem. I googled "ubuntu 11.04 no sound" and found this [**[COLOR="Navy"]thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1748258).

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

These command lines fixed my issue, sound is up and running.

---

### Post by jsgoodall on 2011-07-19
To this I had to add 

sudo apt-get --purge remove pulseaudio

and 

sudo apt-get install pulseaudio

Thank you all, now it works!

---

### Post by mrmc on 2011-07-20
actually i found my problem , ALSA does not support my sound device may be yours. i m searching to add my device. Can you help me about this

---

