---
title: "Gamepad support on Ubuntu?"
date: 2008-06-30
forum: Hardware
---

### Post by Starlight on 2008-06-30
Hi! I'm thinking about getting a gamepad. I've never used one on Linux, so I don't know how well they are supported... do they generally work well, or are there only some specific brands that work? I'm thinking about getting a Logitech one, but I'm not sure yet. If I get one with features like two analog controls and vibration feedback, will all of it work in Ubuntu? If yes, would it also work when playing games on Wine? :)

---

### Post by Starlight on 2008-07-01
Bumping this... and I also found this thread about a Logitech gamepad: [http://ubuntuforums.org/showthread.php?t=428469](http://ubuntuforums.org/showthread.php?t=428469)

Are there any gamepads which work in Ubuntu and I don't need to compile drivers for? :)

---

### Post by jualin on 2008-07-01
I have a Logitech Dual Action and it works well on Ubuntu. Also, if a program wants to know where the device is, it's usually /dev/input/js0 or /dev/js0.

---

### Post by Starlight on 2008-07-01
Thanks :) So maybe only the Chillstream one has problems and other Logitech gamepads work well...

---

### Post by achase79 on 2009-02-23
In 8.10 you don't have to compile drivers for it.  You just have to download and install an .fdi file that is already created from
[https://help.ubuntu.com/community/Joystick_lshal_outputs_done]("https://help.ubuntu.com/community/Joystick_lshal_outputs_done")

---

