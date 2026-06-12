---
title: "Compaq CQ60 inbuilt Webcam help"
date: 2011-04-17
forum: Hardware
---

### Post by Palx on 2011-04-17
Hi, I am running Ubuntu 10.10 on a Compaq CQ60 laptop and cant get my inbuilt webcam to work. I have tried using Skype, Cheese, Ekiga, Camorama etc but it isn't detected at all.  I have also tried starting skype with 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```which doesnt help.


lsusb gives:

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```and it doesn't look like the webcam is on that list. After googling for a bit it would suggest that my laptop would have no problems using the in built webcam with linux, but for some reason it is not detected. Does anyone have any other solutions I can try? thanks

---

### Post by carega on 2011-04-17
I'm having the exact same problem with my compaq CQ40! At least I'm glad I'm not the only one

---

### Post by KrazyKarl910 on 2011-04-27
I am having the same issue... would love a response

---

