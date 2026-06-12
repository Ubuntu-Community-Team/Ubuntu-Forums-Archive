---
title: "Logitech Headphones"
date: 2007-12-22
forum: Hardware &amp; Laptops
---

### Post by ThomasWii on 2007-12-22
Hi, when i go to System > Preferences > Sound and i click the test button (this is with no headphones)  a  long beep comes out of the speaker, when i plug my headphones in to the headphones slot (not usb) and press the test button no sound comes out of the headphones.

Any ideas

Thanks in advance,

Thomas

---

### Post by eggdeng on 2007-12-22
Check your sound card chip using
```
aplay -l
```
You will probably find it is an Intel HDA. If so, check out [http://http://ubuntuforums.org/showthread.php?t=314383]("http://http://ubuntuforums.org/showthread.php?t=314383&highlight=eggdeng")
or do a forum search. If not, do a forum search for your chip.

---

### Post by ThomasWii on 2007-12-23
I don't understand what you mean, all i know is that when i put in aplay -l this came up ```
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: modem [VIA 82XX modem], device 0: VIA 82XX modem [VIA 82XX modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by eggdeng on 2007-12-23
Alsa identifies your soundcard as a VIA  8237.
From what I can see on the forums and on Google, support for this particular card appears to have gone from bad to worse. See, for example [http://ubuntuforums.org/showthread.php?t=566718&highlight=VIA+8237]("http://ubuntuforums.org/showthread.php?t=566718&highlight=VIA+8237")
or [https://answers.launchpad.net/ubuntu/+question/898]("https://answers.launchpad.net/ubuntu/+question/898")
You could try opening a new thread with the name of the card in the title but I wouldn't get my hopes up. An alternative would be to look around for a set of usb speakers. 
Sorry not to be of more help.

---

