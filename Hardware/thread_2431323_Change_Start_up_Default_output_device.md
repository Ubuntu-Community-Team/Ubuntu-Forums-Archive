---
title: "Change Start up/ Default output device?"
date: 2019-11-14
forum: Hardware
---

### Post by castlefox on 2019-11-14
Hi, 

I am using a Logitech G610 and every single time I restart my machine the sound output device ALWAYS changes it back to HDMI and I have to change it to head headphones or line out for the speakers.
Almost every single day I get rather annoying after starting up my PC I change the volume with the big knob on the keyboard but it doesnt work since it went back to HDMI output. 

Anyone have solution for me?   This is drives me crazy almost every day.

I am using 19.04

---

### Post by CatKiller on 2019-11-14
The other desktop environments tend to have the ability to set the default device built into their volume control, but Gnome is rather limited in its configuration ability. There is a PulseAudio utility, whose name I can't currently recall, that will let you do that in Gnome.

---

### Post by SeijiSensei on 2019-11-15
I think CatKiler is referring to the pavucontrol program. 

```
sudo apt install pavucontrol
```

[https://www.addictivetips.com/ubuntu-linux-tips/manage-audio-devices-on-linux-pavucontrol/](https://www.addictivetips.com/ubuntu-linux-tips/manage-audio-devices-on-linux-pavucontrol/)

---

### Post by CatKiller on 2019-11-15
Yep, that name definitely rings a bell and the image looks familiar. It's been a long time since I had to use it on one of my own installs so I could remember that it definitely existed, but not what it was called.

---

### Post by castlefox on 2019-11-16
Thanks for the reply!!   I will look into this.

---

