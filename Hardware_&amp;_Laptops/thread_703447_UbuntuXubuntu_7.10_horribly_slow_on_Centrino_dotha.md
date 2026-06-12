---
title: "Ubuntu/Xubuntu 7.10 horribly slow on Centrino dothan 1.4GHz..."
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by denizenx on 2008-02-21
Hi there!
Second time trying Ubuntu after 6 briefly (no wireless)...

Installed on an Alienware Sentia 244, basically a Centrino 1.4GHz, 2GB RAM with an Atheros 108 WLAN card, standard 855 gfx with a 1400x1050LCD...

Setup was slow on Xubuntu, crashes unless  in Safe Mode on Ubuntu.
Takes about 30+ minutes to start in the LiveCD mode.

After install, takes about 30+ minutes to boot.
Everything lags quite badly and CPU is always fanning itself.

The question is: is it supposed to be so slow? XP is quite fast on this system, on dual boot.
Do I need to do anything else afer the install?

On the side:
- the ath0 is mounted but not showing networks, and there's no Device Manager to be found (as mention in Help)....
- suspend is a black screen with backlighton and mouse cursor?


Hi I really want to try out this, but it seems the speed is not even bearable playing Freecell... :(


Thanks for listening!

---

### Post by Yellow Pasque on 2008-02-21
- Try going to Applications -> System Tools -> System Monitor and see if anything is hogging your CPU.
- Perhaps you should also add the CPU frequency monitor to your bar on the top (right-click, add to panel, CPU Frequency Scaling Monitor) and make sure your CPU is scaling to full speed under load. You can sudo apt-get install cpufrequtils and use the cpufreq-info command for more detailed info on CPU scaling.
- Run some commands for us to diagnose your wireless:
```
sudo lshw -C network
cat /etc/network/interfaces
sudo iwconfig
```

---

### Post by denizenx on 2008-02-23
Tried the System Monitor, which itself takes up to 79% CPU! lol
the bar graph is almost always at 100% while the Monitor windows' processes do not add up to that.
Response is really bad, right click menus can take a minute to respond.
The CPU scaling is almost always at full speed.
Firefox works quite ok though.
Realised that wifi does not work because it tends to time out trying to connect. If I leave the laptop alone for a while and try to connect it connects ok.
WinXP runs smoothly without problems, but strangely xubuntu is also slow.

Tried same install on a new D630 (T7700, 2GB, intel GMA) and this runs at normal speeds at a slacking 800MHz (full is 2.4GHz)...
--> discovered that there is something like windowsupdate running in background, is it killing the older laptop?

Thanks Temujin for offering help!

---

