---
title: "Logitech Formula EX Steering Wheel Install on Ubuntu 11.10"
date: 2012-01-19
forum: Hardware
---

### Post by ruqui05 on 2012-01-19
[B]Hi I'm new at this and I'm starting to switch to Ubuntu I hope that as in a few days leave Windows or leave it in the background, I'm testing in my beloved ubuntu, but the poblem mallor what I have to use my Logitech Formula EX wheel I want to know how to operate the pedals Feed Back and correctly that is what fails. With this being 100% ready to use ubuntu and leave windows. So thanks for your help and hope to install the wheel. :P
[/B]

---

### Post by doctorzeus on 2012-01-19
Generally speaking gaming Hardware is almost never supported by manufacturers on the Linux OS and they only usually create drivers for the Windows platform..

I assume that you can see the device under /dev/js0 or whatever and the reason you are trying to get this working is because you want to game on Linux (maybe using Wine)?

However you could try this command to ensure that all the configuration software is installed:

```
sudo apt-get install joystick
```

Also you may want to look at [URL="http://askubuntu.com/questions/32031/how-do-i-configure-a-joystick-or-gamepad"]this link..
[/URL]
Then report back to see if it recognizes your driving wheel :) ..

Hope this Helps!

---

