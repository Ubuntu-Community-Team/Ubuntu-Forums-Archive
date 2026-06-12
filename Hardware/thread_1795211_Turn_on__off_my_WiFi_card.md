---
title: "Turn on / off my WiFi card"
date: 2011-07-02
forum: Hardware
---

### Post by Denco1 on 2011-07-02
Hello all (new here :P )
I have notebook Toshiba Satellite L650-1K6 and Ubuntu 10.10 (dualboot with Windows 7).
I have a problem with my WiFi card (BCM4313). I would like to have a chance to turn it on and off everytime I need it. But there is a problem. Till is the WiFi turned on on Windows 7, I can connect to WiFi networks on Ubuntu too. When I disable WiFi on Ubuntu and then enable it again, I can't see the WiFi networks. I have to restart notebook to see the networks again. 
When I turn off WiFi on Windows 7, I can't connect to WiFi networks on Ubuntu at all (I can't see them).
I downloaded "Jupiter", but didn't help. It even doesn't know about WiFi card.
Is there any chance, that I will be to enable/disable my WiFi everytime I need without any problems?
Thanks for all replies (hope you understand me :D )

---

### Post by grahammechanical on 2011-07-02
It may be possible to turn the WiFi adapter on and off by pressing a combination of keys. Is this possible? If the WiFi is turned off at the keyboard (by hardware) then Ubuntu will not be able to activate it because it is switched off.

As you have found, Windows has the ability to switch off the WiFi adapter. It makes it impossible for Ubuntu to turn it back on. You need to turn WiFi on in Windows before you shutdown. You need to have Wifi switched on at the keyboard before you load Ubuntu.

When Ubuntu loads it searches for a working WiFi connection. If the WiFi  adapter is switched off it will not find a wireless network to connect  to. It is like trying to tune a radio to a certain radio station when  the radio is switched off. The wireless adapter is not receiving  wireless transmissions from the modem/router and so it does not work  under Ubuntu.

As for this

> When I disable WiFi on Ubuntu and then enable it again, I can't see the WiFi networks.How are you disabling WiFi? Are you clicking Enable Wireless? Then try also clicking Enable Networking. This might stimulate network manager to listen for the transmissions from the router.

Regards.

---

### Post by Denco1 on 2011-07-02
Ok, let's say, that WiFi is turned on from Windows, I can connect to WiFi networks on Ubuntu and I need to turn off the WiFi to save some power, because I'm going to be off the battery and I don't need to be connected to the Internet. After I'm back on AC, I must restart my notebook to be able to connect to WiFi networks again.

I disable WiFi by right clicking on the icon of internet connections in the tray and tick/untick *Enable wireless connections*.

---

### Post by grahammechanical on 2011-07-02
I am not very familiar with terminal commands. For that reason I try to offer advice using the menu system. Here are some terminal commands that I have learned through using this forum.

```
rfkill list
```

This will tell you if the wireless adapter is blocked either by software or hardware.

```
rfkill unblock all
```

```
rfkill unblock wifi
```

These command do as their name suggests - unblock the blocked adapter.

```
sudo ifconfig wlan0 down
```

switches off wifi

```
 sudo ifconfig wlan0 up
```

switches wifi back on.

I do not know if these commands will help. Regards.

---

### Post by Denco1 on 2011-07-02
I have already tried all these commands before.
WiFi is not listed in *rfkill list*

My WiFi card's name is eth1 (sounds little bit weird, hope it doesn't have anything to do with my problem)
```
sudo ifconfig eth1 up
sudo ifconfig eth1 down
```
Doesn't do anything as well.

Oh and I forgot to say, that my hardware switch for WiFi si Fn+F8, but doesn't work too.

---

