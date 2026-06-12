---
title: "ubuntu install problens"
date: 2017-01-10
forum: Hardware
---

### Post by nick-linux on 2017-01-10
I am trying to install ubuntu(16.01) and cant seem to get any flavor of debian to install. Whenever i try to install it it only sends a signal to one of my monitors and spits out these errors: 

[https://goo.gl/photos/PzaZGxXnKKKYfigT6](https://goo.gl/photos/PzaZGxXnKKKYfigT6)

This is clearly a graphics issue, and im not surprised.
here are the specs of my pc:
intel core i5 6600k
geforce gtx 970
Gigabyte z170x-ud5
and im running four monitors off my gpu. 
plz help

---

### Post by Bucky Ball on 2017-01-10
Welcome. Tried 16.04 LTS? Has five years support until 2021. 16.10 has nine months from last October. Reason I suggest is because I have the exact same GPU and it is running faultlessly on 16.04 and I had no issue installing with nouveau, then swapping to the proprietary NVidia driver which you will find in 'Additional Drivers' when you eventually get to a desktop.

Yea, it looks like a graphics issue, but have you tried with one monitor for the moment? Nouveau may not be coping with four monitors. Once installed you can start experimenting. Get the NVidia driver installed and you may have better luck with four monitors. 

Not sure what the configuration is on your version of the GTX 970, but what outputs are you using? HDMI, DVI, a combination of a few? Please be specific. ;)

---

