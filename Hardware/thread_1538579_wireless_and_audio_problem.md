---
title: "wireless and audio problem"
date: 2010-07-25
forum: Hardware
---

### Post by nate_nightroad on 2010-07-25
hi all, i have this netbook from hp and the model is 110-3004TU. the problem here lies with the audio and wireless card driver. now the problem is that no audio coming out from the netbook and ubuntu is able to detect the wireless card but it shows no wireless network available.

for your information,the audio manufacturer is IDT while the wireless card manufacturer is Ralink.

please advice as it is quite annoying to be using ubuntu without audio and having to use LAN for internet connectivity.

thank you and have a nice day~!

---

### Post by lidex on 2010-07-25
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

