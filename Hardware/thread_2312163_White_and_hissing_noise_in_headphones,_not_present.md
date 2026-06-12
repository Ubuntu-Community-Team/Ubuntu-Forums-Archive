---
title: "White and hissing noise in headphones, not present in Windows"
date: 2016-02-02
forum: Hardware
---

### Post by dijsss on 2016-02-02
[COLOR=#333333][FONT=Ubuntu]Hello everyone,[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]I've recently installed Ubuntu 15.10 on my HP Pavilion p042nd. Everything works fine except for the headphones, there is a loud white noise and the left headphone makes a "hissing" noise. The speakers do not do this. I've tried turning off the Intel power saving mode but that does not work. The noise only goes away when I mute the headphones. Does anyone know how to fix this?[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Thanks, Dijs[/FONT][/COLOR]

---

### Post by petarivanov1985 on 2016-02-03
I have the same problem on my Asus n551 and Ubuntu 15.10 still can`t find a solution

---

### Post by Bjornen on 2016-02-23
I have the same problem on my Asus UX501VW except that mutting the sound does not help on my machine. I am currently running ubuntu gnome 16.04, using kernel 4.4.0-6-generic, but the white noise in the headphone jack was also present on 15.10 kernel 4.2.
It would be great if someone have an idea on this topic :).

---

### Post by Zakatell_Kanda on 2016-03-15
Same here with my Asus UX501VW, can anyone guide us on how we can debug it?

---

### Post by aleksandr9 on 2016-03-21
> **Zakatell_Kanda said:**
> Same here with my Asus UX501VW, can anyone guide us on how we can debug it?
+1

---

### Post by jeremy31 on 2016-03-21
Try muting the microphone input

---

### Post by aleksandr9 on 2016-03-21
> **jeremy31 said:**
> Try muting the microphone input
I tried to do this. No luck.
Volume of noise not changed after changing volume on any channel. Even if i mute all channels.

---

### Post by jeremy31 on 2016-03-21
Might have easier time searching if you post ```
lspci -nnk | grep -iA2 audio
```

---

### Post by aleksandr9 on 2016-03-21
```
[FONT=monospace][COLOR=#000000]user@zenbook:~$ lspci -nnk | grep -iA2 audio[/COLOR]
00:1f.3 [COLOR=#FF5454]**Audio**[/COLOR][COLOR=#000000] device [0403]: Intel Corporation Sunrise Point-H HD [/COLOR][COLOR=#FF5454]**Audio**[/COLOR][COLOR=#000000] [8086:a170] (rev 31)[/COLOR]
        Subsystem: ASUSTeK Computer Inc. Sunrise Point-H HD [COLOR=#FF5454]**Audio**[/COLOR][COLOR=#000000] [1043:1080][/COLOR]
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
[/FONT]
```

---

### Post by aleksandr9 on 2016-03-22
Finally i figured out how to fix this. Just need to set correct driver in /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=dell-headset-multi
```
Now headphones and microphone works fine

---

### Post by Bjornen on 2016-04-07
I tried the dell driver, and it seams to lower the noise, but is stil there unfortunately :(. My laptop is the UX501VW running the latest Ubuntu gnome 16.04.

---

### Post by Bjornen on 2016-04-07
GOOD news.
aleksandr9 you are right. After choosing a driver for the alc668 that works, the whistle disapears. My problem was that i now had a low white noise instead. The solution to this is opening "Alsamixer" and disable "Loopback Mi" :D. Now I can finally enjoy music from the headphone jack again!

---

### Post by aleksandr9 on 2016-05-25
Unfortunately, problem is not completely gone: after system wake up white noise strikes back.
Reloading alsa did not help.

---

### Post by fcastillo on 2016-12-02
> **Bjornen said:**
> GOOD news.
aleksandr9 you are right. After choosing a driver for the alc668 that works, the whistle disapears. My problem was that i now had a low white noise instead. The solution to this is opening "Alsamixer" and disable "Loopback Mi" :D. Now I can finally enjoy music from the headphone jack again!

Your post just saved my sanity. That white noise was driving me crazy. I didn't change any drivers or anything similar, but I did disable the "Loopback Mixer" from alsamixer and now everything is solved. I did make sure to run ```
sudo alsactl store
``` so the modified alsamixer settings will be saved across reboots.

I really was going crazy and about to break my headphones and computer. You truly saved me... Thanks!!!

---

