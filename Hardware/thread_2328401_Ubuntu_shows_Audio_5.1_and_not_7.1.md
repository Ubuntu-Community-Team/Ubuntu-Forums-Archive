---
title: "Ubuntu shows Audio 5.1 and not 7.1"
date: 2016-06-20
forum: Hardware
---

### Post by isidoro4 on 2016-06-20
Hi,I have installed Ubuntu 16.04 on my Pc. The Motherboard is Asus X99M-WS/SE and the Audio onboard uses Realtek ALC1150-8 channels featuring Crystal Sound 2. I don't understand because Ubuntu shows only 6 channel and not 8 channels. I can't test it because I haven't speakers 7.1

---

### Post by tareq.mhd on 2016-06-21
You can update the system first, then do install restricted extras.

> sudo apt update
> sudo apt dist-upgrade
> sudo apt install ubuntu-restricted-extras

Before doing these do not forget to update software sources. Please put tick on the ubuntu partner repositories. Now check again.

---

### Post by isidoro4 on 2016-06-21
Nothing Ubuntu shows the analogic audio till to 5.1. it isn't present the 7.1 mode.

---

### Post by isidoro4 on 2016-06-22
Nobody helps me?

---

### Post by tareq.mhd on 2016-06-22
Go to the dash and type sound, a window will open same as the picture.

[img]http://i.imgur.com/0cvnDOG.png[/img]

Now try to change mode, look at the options there.

Let me know the result.

---

### Post by isidoro4 on 2016-06-22
line-out appears only when I plug the jack of speakers. And "Mode" shows "Analog Surround 5.1 output". Where is 7.1 mode?. The voice isn't present in the Combo Box

---

### Post by tareq.mhd on 2016-06-23
> **isidoro4 said:**
> line-out appears only when I plug the jack of speakers. And "Mode" shows "Analog Surround 5.1 output". Where is 7.1 mode?. The voice isn't present in the Combo Box

This is good news, now click on the Analog Surround 5.1 Output; there is a menu under it.

---

### Post by isidoro4 on 2016-06-23
I know, but options are till to 5.1 mode. No 7.1 in menu. Maybe I need Pulseaudio?

---

### Post by tareq.mhd on 2016-06-23
Let's try another one, do execute following codes.

> sudo alsa force-reload
> reboot

---

