---
title: "Soundcard does not show in sound settinngs"
date: 2015-01-30
forum: Hardware
---

### Post by bdoubek on 2015-01-30
Hey, I have Siberia Elite headphones, which uses their own soundcard system connected with USB. They worked before just fine, but now when i plug them in and open sound settings, they are not even registered as option. I tried to use **alsamixer**, which registers the sound card, but while trying to change with F6 to steelseries sound card, it closes alsamixer to terminal with: ```
cannot load mixer controls: Invalid argument
``` , tried to use ```
sudo aplay -l 
``` and here is the answer:```
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC269VB Digital [ALC269VB Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [SteelSeries SC2 USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```



Sorry, if the post is written badly. Well thx for future advices.

---

### Post by jan56 on 2015-08-08
Hey!

I have almost the exact same problem. 

When i select output in soundsettings i was able to see the steelseries sc2 soundcard. I selected a different modus by mistake and suddenly the usb soundcard was vanished. 

A google search also pointed auto to open a terminal, use the command alsamixer and hit f6 to select the proper soundcard. I was surprised the soundcard came up. Problem is that after selecting it there is still no sound in my usb headset.

---

### Post by jan56 on 2015-08-08
[https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices](https://help.ubuntu.com/community/UbuntuStudio/UsbAudioDevices)

Maybe this one is working for you? I tried it but it is a bit to difficult for me.

---

