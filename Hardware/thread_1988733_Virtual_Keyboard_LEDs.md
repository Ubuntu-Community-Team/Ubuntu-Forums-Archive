---
title: "Virtual Keyboard LEDs"
date: 2012-05-28
forum: Hardware
---

### Post by datajack on 2012-05-28
I have just bought a new laptop and realised that there are no LEDs indicating the sate of Caps Lock, Num Lock etc.

Is there anything that will display the current state of the keyboard LEDs on the top bar of Unity?

---

### Post by typhoon_tip on 2012-05-28
Answer is yes, there is:

```
sudo add-apt-repository ppa:tsbarnes/indicator-keylock
sudo apt-get update
sudo apt-get install indicator-keylock

```

Logout and login again after install.

EDIT: just installed myself too, I like the fact that when the CAPS is tuned on, you get a nice message on the same style as other system messages.

---

### Post by datajack on 2012-05-28
Thanks!
There's a number of niggly issues with it that I will take to launchpad - but it's a lot better than what I had before :)

---

