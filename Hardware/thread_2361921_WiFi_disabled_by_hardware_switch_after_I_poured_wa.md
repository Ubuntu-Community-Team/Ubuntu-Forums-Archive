---
title: "WiFi disabled by hardware switch after I poured water on my laptop keyboard"
date: 2017-05-22
forum: Hardware
---

### Post by user3822769 on 2017-05-22
I poured water on my laptop computer. I switched off power and waited for two days. Everything seemed OK except WiFi. It says WiFi is disabled by hardware switch. I tried Fn + Fx, and rfkill unblock all. But nothing works. And also eth0 interface works, but there is no light blinking. Is part of network hardware broken by water. How can I check my network hardware throughly.

```
zw@zw-Inspiron-3442:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```

---

### Post by chrisonbuntu on 2017-05-22
Are you sure its completely dry?  Turn off the machine and put in a sealed bag containing silica or dried rice.  Leave for a few more days.

The wifi chip might have been short-circuited by the water.  You might have to get a USB wifi dongle...

---

### Post by Autodave on 2017-05-22
You might also want to try and remove the battery and leave it out for 10 minutes with the power cord disconnected. After 10 minutes, put it back together and see what happens.

---

