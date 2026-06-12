---
title: "Touchpad not working"
date: 2010-08-07
forum: Hardware
---

### Post by michael00xc on 2010-08-07
Hi, total newbie to linux here.

i installed ubuntu 10.04 2 days ago. The only problem i encountered is about the touchpad.
i tried a lot of method but none i have completed so far.

- the device name is virtual core pointer.
- i have installed gsynaptics but i cant open it. this error comes out, "you have to set 'SHMConfig' 'true' in xorg.conf" but when i open xorg.conf, it is empty.

any enlightenment would be appreciated.

thanks

---

### Post by roger_1960 on 2010-08-07
Hi

Not sure, but try installing gpointing-device-settings in terminal > apt-get install gpointing-device-settings(or from synaptic package manager)  This works with my alps trackpad and is meant to replace gsynaptics I believe.

---

### Post by bprins on 2010-08-07
xorg.conf is empty? i bet ur opening the wrong 1. how the hell can X run without an xorg.conf.

do a locate xorg.conf, it might pop up on more then 1 location i guess.

---

### Post by lidex on 2010-08-07
> **bprins said:**
> xorg.conf is empty? i bet ur opening the wrong 1. how the hell can X run without an xorg.conf.

do a locate xorg.conf, it might pop up on more then 1 location i guess.

Nope, it's deprecated in ubuntu. You can create one if needed and it's location would be:
```
/etc/X11/xorg.conf
```

---

### Post by lidex on 2010-08-07
> **michael00xc said:**
> Hi, total newbie to linux here.

i installed ubuntu 10.04 2 days ago. The only problem i encountered is about the touchpad.
i tried a lot of method but none i have completed so far.

- the device name is virtual core pointer.
- i have installed gsynaptics but i cant open it. this error comes out, "you have to set 'SHMConfig' 'true' in xorg.conf" but when i open xorg.conf, it is empty.

any enlightenment would be appreciated.

thanks

It would help to know your laptop make/model number:
[http://www.linlap.com/](http://www.linlap.com/)

---

### Post by michael00xc on 2010-08-08
> **lidex said:**
> It would help to know your laptop make/model number:
[http://www.linlap.com/](http://www.linlap.com/)


I guess mine is not on your list. My laptop is named blue, model = M626.
idea:
1. I could also opt to try other method that you would recommend to other brand of laptop.
2. Maybe there is something i can do for the specific model of my touchpad that is similar to other brand of laptop. ex. if HP uses the same touchpad as my Blue does, then i could try the method you would recommend for the HP.

---

### Post by michael00xc on 2010-08-08
> **roger_1960 said:**
> Hi

Not sure, but try installing gpointing-device-settings in terminal (or from synaptic package manager)  This works with my alps trackpad and is meant to replace gsynaptics I believe.

Error, this is what i get:

E: could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory ( /var/lib/dpkg/), are you root?

I totally have no clue bout this one.

---

### Post by lidex on 2010-08-09
You need to use sudo to install in terminal using apt-get.
```
sudo apt-get install gpointing-device-settings
```
Enter your user password when prompted.

---

### Post by michael00xc on 2010-08-09
> **lidex said:**
> You need to use sudo to install in terminal using apt-get.
```
sudo apt-get install gpointing-device-settings
```Enter your user password when prompted.

I did what you said, it installed pointing devices on my system->preferences. Still, my touchpad is not working.

How would i know if my TP device is being recognized by ubuntu? any command i can type?

---

