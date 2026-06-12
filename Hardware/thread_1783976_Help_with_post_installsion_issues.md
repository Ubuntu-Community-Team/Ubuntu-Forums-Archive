---
title: "Help with post installsion issues"
date: 2011-06-16
forum: Hardware
---

### Post by Googleness on 2011-06-16
Hello Everyone,

I've just replaced windows 7 Ultimate with Ubuntu 11.04 64 bit on my Laptop (Lenovo U550).
With most of the issues I've managed to solve already but there are two problems left which I'll need your help with.

1) Bluetooth: after each time I reboot my laptop and logging in to Ubuntu with my user the Bluetooth applet is active but when I open it I get the message:

> Bluetooth is Disabledchecking with rfkill I can see it's not blocked, and I can only use Bluetooth (mostly with my Logitech V470 mouse) only after running this at the terminal:

```
sudo service bluetooth restart
```2) Mouse keys: AS I've metioned erlier I have Logitech V470 Bluetooth mouse. The middle mouse button is both a scroller and 3 keys (down, right, left). I want to set up the middle keys (right, left) to be used for browsing (forward, backward).
After some investigation I've stumbled across a tool called **btnx** which by it's documention support my mouse model.

The problem is that the auto test implemented in the tool is failing to recognize my mouse keys. It's stuck on the "move your mouse, click the keys" phase.


Any help will be appreciated,
Liron

---

