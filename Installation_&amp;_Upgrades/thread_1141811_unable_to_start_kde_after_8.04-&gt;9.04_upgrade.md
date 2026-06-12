---
title: "unable to start kde after 8.04-&gt;9.04 upgrade"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by stakh on 2009-04-28
Today I run the distribution upgrade scrpit on my kubuntu 8.04 to get jaunty 9.04.

There were two bugs reported by the script, ls /var/crash/:
- mumble-server.0.crash
- usr_lib_kde4_bin_krunner_lock.1000.crash

Afer rebooting as instructed, KDE fails to launch (I get a gaphical wallpaper, but no login menu), and I'm dropped to a terminal. Trying startx also fails.

Any ideas on how to recover kde?

---

### Post by kannedheat on 2009-06-04
I have also upgraded to 9.04 and added the ATI control panel.  When I rebooted I can no longer use my mouse or logon screen.

---

### Post by kannedheat on 2009-06-04
Problem solved

Boot up to a terminal session and type:
```
apt-get remove --purge xorg-driver-fglrx
```
Since I used the ATI console
```
/urs/share/ati/fglrx -uninstall.sh
```
```
reboot
```
I was good to go. You might want to try
```
apt-get install xserver-xorg-video-radeon
```
If you need to get online through the terminal session 
```
iwconfig
```
```
ifconfig *$device_name* up
```
```
iwlist scan
``````
iwconfig *$device* essid "*connections name*"
```
```
dhclient *$device*
```

---

