---
title: "A perennial installation 'GOTCHA' - WiFi !!"
date: 2010-05-14
forum: Hardware
---

### Post by mango42 on 2010-05-14
Ever since I started using Ubuntu Linux (Gutsy Gibbon) my major installation issue has always been net access.

Despite Lucid Lynx being the very best and smoothest install I have ever attempted, this key issue is still with us. Could this be because the devs are used to being hardwired to the net?

So, I get to the install page that shows what hardware I have available for net access but this page *never* gives an option for USB connected WiFi dongles - hence any attempts to set up the net are doomed to failure because of that 1st page's limited options. Fine, it discovers that I have Ethernet ports and *built in* WiFi but doesn't seem to look any further to the *only* port with a working net connection - USB.

Perhaps none of the devs work out in the sticks in developing countries where the *only* option is often bicycle-powered Access Points? The only way I can get on the net is by running a WiFi dongle on the end of 15metres of (amplified/powered) USB cable.

I can always resolve this issue eventually (well, I could until 10.04, where the very options in the Network dialogue that enabled me to fix this problem without resorting to the commandline have now disappeared!!) but it would be great if more was done to ascertain exactly what resources are really available at the install stage, even it's only a field titled 'None of Those Listed'.

Hopefully this 'rantlet' will be taken in the manner intended - positive criticism of what is now proven to be the very best OS on the planet, IMO ;-)

---

### Post by jpl888 on 2010-05-14
Although wireless device support has come on in leaps and bounds, in Linux, over the last few years, it can still be patchy.

The first thing to find out is what support there is for your dongle.

If you post the output of ```
lsusb
``` I can tell you what your options are.

---

### Post by mango42 on 2010-05-14
It's a bog-standard dongle that's been working fine since 7.04 - *once I set it up manually* (as opposed to a 'modern' Netgear dongle that refuses to connect to Open Access Points at all - Big Brother at work? Looks like it!).

```
Bus 001 Device 004: ID 148f:2570 Ralink Technology, Corp. 802.11g WiFi
```

It's just that install page that's annoying - at the very least, there definitely needs to be an option to bypass the whole net issue if no live net access found, imo

---

### Post by jpl888 on 2010-05-14
Well I'm not sure about the rt2570 but I have used the rt73 quite successfully with Ubuntu i.e. it worked out of the box for me using the in kernel drivers.

Do you know which driver you are using?

Could you post output of ```
lsmod
```?

---

### Post by mango42 on 2010-05-14
Grateful thanks for your interest, **jpl888**

Relevant **lsmod** output:-

```
rt2500usb              21152  0 
rt2x00usb              11548  1 rt2500usb
rt2x00lib              29756  2 rt2500usb,rt2x00usb
input_polldev           3716  1 rt2x00lib
mac80211              181140  2 rt2x00usb,rt2x00lib
cfg80211               93052  2 rt2x00lib,mac80211

```

and following my comment about a useless netgear dongle:-
"Germany: Mandatory passwords for all wireless accounts"
[http://news.yahoo.com/s/ap/20100512/ap_on_hi_te/eu_germany_wireless_passwords](http://news.yahoo.com/s/ap/20100512/ap_on_hi_te/eu_germany_wireless_passwords)

---

### Post by jpl888 on 2010-05-14
Well that's the right driver anyway.

I'll tell you my own experiences, and you can take it with a pinch of salt if you like.

Network Manager is a bit of a steaming pile of borkage IMO. I have had a number of issues with it over the last couple of years and I find it is easier in the long run just to configure your network the good ole' /etc/network/interfaces way.

The specific problem I have with Network Manager (and or driver) at the moment is that it takes upto 30 seconds to register and get an IP address. At least using "interfaces" by the time I get to the desktop it has sorted itself out (and considering my laptop takes circa 15 seconds to boot it is definitely working better than network manager).

I suppose the reason Network Manager is used is that it is the best user friendly networking app available at the minute.

I also have issues with it deleting the WPA key when I am unable to get an IP for some reason, or something similar. I seem to remember having to repeatedly enter the key and for it to be lost after reboot, which I found intensely annoying.

Maybe we should be gently suggesting that Ubuntu get rid of Network Manager and start again?

---

### Post by jpl888 on 2010-05-14
I just read your original post again and I realise I am going off on tangents.

Perhaps wireless users should be told to boot the liveCD and install from the liveCD desktop.

At least then if the wireless card works out of the box there will be no issue with internet connection?

---

### Post by mango42 on 2010-05-14
> Perhaps wireless users should be told to boot the liveCD and install from the liveCD desktop.

Unfortunately this doesn't apply to UbuntuStudio, my main interest - alternate install only. FWIW, I make a point of creating a standard Ubuntu LiveCD install, then partition and install Studio - then spend 'some time' getting the WiFi dongle to work.

Tangents welcome but perhaps not by the mods ;-)

---

### Post by mango42 on 2010-05-15
Bump

Any developers interested in this issue or are WiFi dongles still too much of a political, let alone technological, football?

---

### Post by mango42 on 2010-05-28
I sometimes wonder whether there are gremlins at work amongst all the wonderful vocational coders here (who work their brains to a frazzle providing us with brilliant tools) that make matters difficult for us semi-computer-literate users? Would it be paranoid to inquire whether commercial or political factions have some high level 'lobbying' going on in the Linux world, to discourage the free flow of information?

Just to round this thread off on a happy note, installing **NetworkManager Applet 0.8** manually from the DVD (```
Ubuntu-Studio 10.04 LTS amd64/pool/main/n/network-manager-applet/network-manager-gnome_0.8-0ubuntu3_amd64.deb
```) has finally enabled me to get this machine on the net.

Yay!:P

---

