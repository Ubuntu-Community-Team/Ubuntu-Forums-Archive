---
title: "Need help with 3 Intrepid Problems"
date: 2008-11-15
forum: General Help
---

### Post by ragflan on 2008-11-15
Hi all. I just upgraded to Intrepid from Hardy 2 days back. I actually did a fresh install instead of upgrading. Everything's great in Intrepid, but I have 3 problems. 

1.) BTNX no longer works but I already read why on Ubuntu Forums. I read something about 'evdev'. Does anyone know another way?

2.) I can connect to any Network without any problems. But when I turn my wireless switch off on my laptop and turn it back on, Network Manager won't detect any networks at all. Everything is grayed out. Only a restart fixes this. Something I never encountered on Hardy.

3.) Compiz effects are really laggy. I've not enabled anything more than what I had on my Hardy install - and in fact, I removed most of the effects. XORG seems to take a lot of CPU. I've pretty much disabled everything on Compiz except Desktop Wall and Wobbly Windows and a couple of other plugins. Not more than 7 are checked. The memory usage is around the same. 30-40% on CPU1, and 45-50% on CPU2. 

Here are the applications that I know are running. Firestarter, Easy Stroke, Fusion Icon, Drapes, Gnome-Do and Conky. With all these running, CPU usage is at 5% or less. Once I open any window - be it Firefox, Gedit, Thunderbird, Prism or anything in general - CPU usage goes up to around 30% and doesn't go down till I minimize the window. Applications are snappy, and even more responsive than on Hardy, but the effects are really laggy. 

I would greatly appreciate any help.

---

### Post by blackened on 2008-11-15
For #2, you need to restart your wireless adapter (which is essentially what happens when you reboot) using the following command (replace wlan0 with your appropriate adapter, you can usually find this using iwconfig in the terminal):
```
sudo ifconfig **wlan0** up
```

---

### Post by Peter09 on 2008-11-15
For your laggy display

Check your video driver by
```
lshw -C display
```

There appear to be problems with the drivers set ups for quite a few systems at the moment.

---

### Post by ragflan on 2008-11-15
When I type the command (lshw -C display), I get the following: 


```
WARNING: you should run this program as super-user.
  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

```


I don't know what the above means. Anyone?

---

### Post by Peter09 on 2008-11-15
As a First Pass at configuring your Video Driver:
1. Check that there is no driver waiting to be enabled in System->Administration->Hardware Drivers
2. Boot into recovery mode and select 'xfix' from the menu, this may resolve it. (Check 1. after doing this as well)

---

### Post by ragflan on 2008-11-15
> **blackened said:**
> For #2, you need to restart your wireless adapter (which is essentially what happens when you reboot) using the following command (replace wlan0 with your appropriate adapter, you can usually find this using iwconfig in the terminal):
```
sudo ifconfig **wlan0** up
```


Problem 2 is fixed! THank you! 

There are no display drivers to install under System -> Administration -> Hardware Drivers. I'm gonna try xfix now. Be right back.

---

### Post by ragflan on 2008-11-15
I'm back. No change. I tried to boot into Recovery mode and choose the xfix option. I got a message saying any changes I made to Xorg will be replaced and that a backup will be placed in /etc/X11.

I logged back in the normal way, there's nothing under Hardware Drivers but the problem still persists. The CPU usage is still around less than 5% with no window open. But with a window open, it's like 20-40% even though I'm not doing much. Like right now, I only have Ubuntu Forums open in a Prism window, and usage is around 20%

---

