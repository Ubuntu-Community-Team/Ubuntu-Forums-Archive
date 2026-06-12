---
title: "[SOLVED] Compiz wont change anything"
date: 2008-08-07
forum: General Help
---

### Post by yarn on 2008-08-07
ok so i installed compiz fusion onto my ubuntu 8.04 using this website 

[http://thegabfather.wordpress.com/2008/05/19/here-is-how-you-can-install-ubuntu-with-a-terminal/](http://thegabfather.wordpress.com/2008/05/19/here-is-how-you-can-install-ubuntu-with-a-terminal/)  

I did both through synaptic and through the terminal and neither will work. It wont even let me change the number of desktops i have. It says I only have one but really I have two. see screenshots.... THE DESKTOP SCREENSHOT SHOWS MY 2 DESKTOPS IN LOWER RIGHT CORNER BUT IN THE CCSM THE AREA WHERE YOU CAN CHANGE THE NUMBER OF DESKTOPS IS GRAYED OUT AND NO PLUGINS WORK AT ALL...any help would be much appreciated and I an very new to linux.

---

### Post by tuxxy on 2008-08-07
Compiz is included with the default Hardy install, to enable compiz you have to install your video driver from [B]system > admin > hardware drivers
[/B]
Then enable compiz at **system > prefs > appearance, **to install the compiz settings manager open terminal and type

```
sudo apt-get install ccsm
```

---

### Post by yarn on 2008-08-08
so how do i uninstall everything I have on here now?

---

### Post by yarn on 2008-08-08
oh...i got it working...u were right i just didnt understand...thanks a bunch

---

