---
title: "Help with wireless internet"
date: 2008-10-13
forum: General Help
---

### Post by Cloudd on 2008-10-13
I just got Kubuntu with KDE4 installed. I was trying to find how to set up the wireless internet, but i couldn't figure it out. I am trying to connect with my computers built in wireless. Can anyone help?

---

### Post by ubunny on 2008-10-13
open a terminal window

sudo ifconfig ath0 down
sudo iwconfig ath0 essid someap key ifyouneedit
sudo ifconfig ath0 up
sudo dhclient ath0

kinda depends on your wireless card config.  check dmesg or lspci -v

---

### Post by Cloudd on 2008-10-13
So what do these do?

---

### Post by Yellow Pasque on 2008-10-13
First, identify what wireless card you have and see if there's a driver loaded:
```
sudo lshw -C network
```

---

### Post by Cloudd on 2008-10-13
I think it has a driver installed because it gave me a driver version. what do I do next? Btw it says "product: DP83815 (MacPhyter) Ethernet controller

---

### Post by Yellow Pasque on 2008-10-13
I believe that's the Ethernet controller, not the wireless. Please post output from the lshw command.

---

