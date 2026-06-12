---
title: "missing alsa-driver package"
date: 2012-06-17
forum: Hardware
---

### Post by arcadetor on 2012-06-17
ok.. I have the typical headphone-front speakers sound problem.. (when you connect the headphones to the laptop, the sound from the laptop speakers is still there...)

I had been trying a lot of codes, sudo asdasdasd, etc... but I found that the solution to my problem was this package:

"linux-alsa-driver-modules-2.6.32-38-generic"

when I run "sudo apt-get install linux-alsa-driver-modules-$(uname -r)" it says that the package can't be found...

so, I tried with the synaptics program... but i found only up to 32.34... "maybe it will work" I thought xD.. so I installed the package and reboot...

the thing is that when I log in to 32.34... there is no sound problem :)! but... I don't have wifi :(..

and, when i log in to 32.38.... i have wifi, but the sound problem is still there...

SO....... where I can find this package (linux-alsa-driver-modules-2.6.32-38-generic)?????:confused: plz help!!

I have Ubuntu 10.04 LTS and a Toshiba Satellite c645d
kernel 2.6.32-38.........

---

