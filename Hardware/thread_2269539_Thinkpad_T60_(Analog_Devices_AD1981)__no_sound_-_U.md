---
title: "Thinkpad T60 (Analog Devices AD1981)  no sound - Ubuntu 14.04"
date: 2015-03-16
forum: Hardware
---

### Post by Trinh_Le on 2015-03-16
Hi, i'm a newbie in Ubuntu. Sorry if my English incorrect. My laptop is Thinkpad T60 and i use external speaker. one month ago, I install Ubuntu 14.10, after software update, everything is ok and sound work fine. 7 days ago I install windows 7 and then i reinstall ubuntu 14.10 but sound don't work. I try install some times again (about 10 times include ubuntu 13.10, 14.04) but sound don't work. Please help, thanks.
Some info: 
```

 **** List of PLAYBACK Hardware Devices ****card 0: Intel [HDA Intel], device 0: AD1981 Analog [AD1981 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD1981 Digital [AD1981 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

---

### Post by tgalati4 on 2015-03-16
Welcome to the forums.

It could be that the output amplifier has burned out.  That's an older laptop and it happens.  Were you playing it loud for long periods of time?  I have a T43p and the [sound chip]("http://www.thinkwiki.org/wiki/AD1981HD") is pretty standard Intel, with no issues in Linux.

Can you hear sound using headphones?  Do you get very faint sound in one speaker?  It could be a loose cable inside.  It might be time to take it apart and clean it out and reseat the cables.  Sometimes the output jack gets loose and might need to be resoldered.  Is the audio jack loose when you plug in headphones?

When you hit the volume keys on the laptop, do they display a volume bar that goes up and down with volume change?

---

### Post by Yellow Pasque on 2015-03-16
Give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Maybe you'll get lucky and just have to toggle a setting in alsamixer.

---

