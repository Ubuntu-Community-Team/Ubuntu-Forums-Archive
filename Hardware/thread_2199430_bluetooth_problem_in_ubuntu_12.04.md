---
title: "bluetooth problem in ubuntu 12.04"
date: 2014-01-13
forum: Hardware
---

### Post by adityashah30 on 2014-01-13
Hi guys,
I recently installed windows 8.1 along with ubuntu 12.04 lts on my dell xps l502x machine. Since, the installation of windows 8.1, the control switch for bluetooth which was same for wifi doesn't work. I mean that now with Fn+F2, I can only toggle wifi and bluetooth always remains on. Also, after waking from suspend, bluetooth always turns on. Please can anyone give me a solution to fix this?

Thanks

---

### Post by varunendra on 2014-01-14
We may try rfkill command to toggle it on/off.

Please try -
```
rfkill block bluetooth
```

If that doesn't help disabling it, please post back the output of -
```
rfkill list
```

**PS:**
Have you tried "blueman" yet? It gives better control over bluetooth adapter, and some controls that the default applet doesn't show.

---

### Post by zircon_34 on 2014-01-15
I have the same problem in Ubuntu 13.10 on Macbook air 5,1...

---

### Post by varunendra on 2014-01-15
> **zircon_34 said:**
> I have the same problem in Ubuntu 13.10 on Macbook air 5,1...

Does any of the suggestions I gave in my previous post works for you? If not, please post the same output as I asked for in that post. Much better - post the details along with the outputs in a separate thread of your own in "Apple Users" section of the forums and give us its link here.

---

### Post by zircon_34 on 2014-01-16
It didn't work. Thats the output:

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

I tried the same with the sudo command before the rfkill, then the bluetooth was disabled. But when I open the bluetooth properties (right click) the button is on. So I typed "rfkill list" to check, and again bluetooth is on (soft blocked: no). 

The only way for me to disable it was to click on the bluetooth icon (on top right corner) and select bluetooth, and the icon disappears with bluetooth disabled.

I found [another thread]("http://linuxg.net/how-to-disable-bluetooth-at-startup-5-practical-methods/") that explains that this command has to be saved in a text file to be remembered at boot up. I might try this and will post a thread if it works. there are other similar problems like the screen brightness is always full per default at startup...

---

### Post by adityashah30 on 2014-01-16
I tried blueman and it did give me much better control over bluetooth, but still not the exact thing i was looking for. My question is that why doesn't Fn+F2 control bluetooth anymore?

---

### Post by K3N8 on 2014-01-25
Hi,

I had the same problem. I blacklisted "acer_wmi" in /etc/modprobe.d/blacklist.conf. Next I added "ath3k" to /etc/modules. Now everything works again.

Gr. Alexander

---

