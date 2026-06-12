---
title: "How to change MAC address of Dell Inspiron N4010 in ubuntu 10.04LTS?"
date: 2010-10-16
forum: Hardware
---

### Post by Shibbir on 2010-10-16
[LEFT]I have a Dell Inspiron N4010 notebook. I've installed ubuntu 10.04LTS  along with windows 7. The problem is that i can't find my ethernet  device on ubuntu. I need to change the MAC address. In windows 7 i can  see and change mac address of my nic card. But in ubuntu i just cannot.  I've tried **ifconfig **command, but that doesn't show my original nic card.  Can anyone have a idea please?:confused:[/LEFT]

---

### Post by spikoley on 2010-10-16
You need to install *macchanger*.

```
sudo apt-get install macchanger
```

Set a random mac address. Change eth0 to your nic.
```
sudo macchanger -A eth0
```


Set a random mac address using the same manufacturer as your nic.
```
sudo macchanger -a eth0
```


Set a custom mac address:
```
sudo macchanger -m XX:XX:XX:XX:XX:XX
```

Where XX:XX:XX:XX:XX:XX is the mac address you want to change it to.

---

