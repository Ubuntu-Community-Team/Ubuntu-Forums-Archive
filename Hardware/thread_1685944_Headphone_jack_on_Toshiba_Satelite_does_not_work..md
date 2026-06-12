---
title: "Headphone jack on Toshiba Satelite does not work."
date: 2011-02-11
forum: Hardware
---

### Post by king james II on 2011-02-11
I have a Toshiba satellite T135D-S1324 RT and I have been running ubuntu 10.4 lucid since September of last year and needless to say I love everything about this OS. However I have hit a brick wall on one front, my headphone jack and built-in microphone do not work. I know this is a common problem with laptops and I have tried many different methods to get it working but failed each time. I've been struggling with this for months now and it's been driving me nuts. Can anyone out there please please give me a hand? :confused:

---

### Post by jerrrys on 2011-02-11
at first glance this seems promising; have you been here

 [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Toshiba+satellite+headphone+jack&as_qdr=all&sa=Google+Search&lang=en#941](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Toshiba+satellite+headphone+jack&as_qdr=all&sa=Google+Search&lang=en#941)

---

### Post by king james II on 2011-02-11
thanks dude but I found some code that totally solved it.

> sudo add-apt-repository ppa:ubuntu-audio-dev/ppa; sudo apt-get update; sudo apt-get install linux-alsa-driver-modules-$(uname -r)

PROPS TO MARIOST!

---

### Post by jerrrys on 2011-02-11
nice

---

### Post by mookie60 on 2012-01-29
adding the repository ppa and modules, as mentioned above, got my mic working.   only 6 months to find the right answer.   thank you thank you thank you

toshiba satellite m645-s4070 running Ubuntu 10.04

\\:D/

---

