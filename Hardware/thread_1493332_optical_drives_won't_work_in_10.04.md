---
title: "optical drives won't work in 10.04"
date: 2010-05-25
forum: Hardware
---

### Post by Tryer(ForLife) on 2010-05-25
hello

i have 2 optical drives, they are both combo DVD/cd recorders, and both of them, every since i did a clean install of lucid lynx wont work. I put a DVD inside and nothing happens, it's not loaded at all. It's the same with both burners. Sometimes it works, and even then i get errors when i try to open something.

Please note that they both work ok in windows, and before they worked ok in ubuntu 9.04 jaunty.
When i upgraded to 10.04 i did a format and install, so this shouldn't be an upgrade problem.

is there any help, i really don't wanna boot windows to read dvds....

---

### Post by Tryer(ForLife) on 2010-05-26
well after some more googling i found a solution, at least to my problem
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

You have to run this

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

in Terminal

and then install libdvdcss2 from Synaptic

and that's it, it worked....

---

