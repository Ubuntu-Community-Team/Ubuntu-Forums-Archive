---
title: "HDMI to VGA cable - force hotplug?"
date: 2015-04-17
forum: Hardware
---

### Post by djole94hns2 on 2015-04-17
Hi there,

I'm wondering, can I force my ATI graphics card to recognize HDMI as plugged in, so I can force the signal trough this adapter:

[img]http://s10.postimg.org/5g3flqwwp/IMG_20150416_171456.jpg [/img] 

This adapter worked very well on my Raspberry Pi, with help of forcing HDMI to recognize the cable as plugged in, or in short, with this parameter:

```
hdmi_force_hotplug
```

Is there anything similar I can do with the ATI Radeon graphics card?

The main reason I want to "trick" my card to recognize HDMI as plugged in is because I want to run audio trough it with this adapter (it splits the signal into VGA and 3.5mm audio connectors).

Thanks in advance!

---

### Post by trag on 2015-05-04
I use the same style of splitter to fix an over scan problem using just HDMI on my big screen. connected the VGA and the 3.5 to the TV( switched TV to read VGA from HDMI) and it fired right up

---

