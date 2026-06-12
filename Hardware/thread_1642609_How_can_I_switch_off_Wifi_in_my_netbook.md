---
title: "How can I switch off Wifi in my netbook?"
date: 2010-12-10
forum: Hardware
---

### Post by zhaotianwu on 2010-12-10
I'm using Ubuntu 10.10, just freshly installed. I am not using any Wifi so I want it switch off. In Windows I can simply switch it off by pressing Fn+F9, however in Ubuntu when I press those keys nothing happened. And I also look for options in System==> Preference and System==>Administration, but didn't find anything. How can I switch off Wifi once and for all? Thanks.

---

### Post by HankB on 2010-12-10
You can turn off wireless networking by right clicking the icon in the menu bar and clicking on "Enable Wireless." I think that will turn the radio off.

You might get more specific help if you identify brand and model of netbook.

HTH,
hank

---

### Post by Ibidem on 2010-12-10
Surest way:
Open a root terminal.
Run 
```
iwconfig|grep '802.11'
```
You should see something like this:
```
...
...
wlan0     802.11bg ESSID ...
```
If wlan0 is the proper interface, run:
```
ifconfig wlan0 down
```

---

### Post by zhaotianwu on 2010-12-10
> **HankB said:**
> You can turn off wireless networking by right clicking the icon in the menu bar and clicking on "Enable Wireless." I think that will turn the radio off.

You might get more specific help if you identify brand and model of netbook.

HTH,
hank

My netbook is Samsung NP-N310. Any particular advice on this model? Thanks.

---

### Post by zhaotianwu on 2010-12-10
> **Ibidem said:**
> Surest way:
Open a root terminal.
Run 
```
iwconfig|grep '802.11'
```You should see something like this:
```
...
...
wlan0     802.11bg ESSID ...
```If wlan0 is the proper interface, run:
```
ifconfig wlan0 down
```

Hi I've tried exactly what you said here, but the wifi light is still on for my netbook, I don't know why.:o

---

### Post by jschall1 on 2010-12-10
> **zhaotianwu said:**
> Hi I've tried exactly what you said here, but the wifi light is still on for my netbook, I don't know why.:o

You probably will need to install samsung-tools from the voria ppa.

---

