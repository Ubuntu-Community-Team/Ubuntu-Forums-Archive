---
title: "Activating external LCD port on Lenovo X60 Laptop"
date: 2007-06-03
forum: Hardware &amp; Laptops
---

### Post by dlwofford on 2007-06-03
The main purpose of this guide is to show how I was able to enable/disable the LCD port on my Lenovo X60 for presentations using Ubuntu 7.04.  Before we start make sure you have the following packages installed from Synaptic.

[B]libc6 (>= 2.3.6-6)
pciutils (>= 1:2.1.11-6)
build essentials[/B]

```
sudo aptitude install build-essential libc6 pciutils
```

Once the packages are installed go to [[COLOR="green"]"http://www16.plala.or.jp/mano-a-mano/i810switch.html"[/COLOR] ]("http://www16.plala.or.jp/mano-a-mano/i810switch.html")
and download the i810switch program developed by Ken Mano. I used build i810switch-0.6.5.tar.gz.
Once downloaded extracted edit the &#8220;**i810switch.c**&#8221; file. We want the i810 program to treats the I945 chip set as I855. Within the &#8220;**i810switch.c**&#8221; file find the entry
```
 i = (p = strstr(*buff_ptr, I855STR)) != NULL;
```
and replace it with
```

               i = (p = strstr(*buff_ptr, I855STR)) != NULL ||
                  (p = strstr(*buff_ptr, I945STR)) != NULL;
                if (i)
                {
                        *chiptype = I855;
```

close and save &#8220;**i810switch.c**&#8221;. 

From a terminal session go to the i810switch directory and do your
```
sudo make
sudo install

``` 

The last step is to edit your /etc/X11/xorg.conf and add the following info at the &#8220;Device&#8221; section [/SIZE]
```

Section "Device"
Identifier "Intel Corporation Mobile Integrated Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
Option "MonitorLayout" "CRT,LFP"
Option "Clone" "true"
Option "DevicePresence" "true"
EndSection
```

Reboot and the external LCD will turn on via start-up. 

From a terminal session or shell script you can issue the following commands.
```
gksudo i810switch crt off
```
or
```
gksudo i810switch crt on
```
or 
```
gksudo i810rotate 
```
Which toggles between LCD only, LCD+CRT, CRT only.

Now someone just figure out a way to map the toggle to the FN-F7 keys. :D
I hope this guide helps someone!

This guide was prepared using the following info from these site.
[[COLOR="green"]http://www.thinkwiki.org/wiki/Installing_openSUSE_10.2_on_a_ThinkPad_X60]("http://www.thinkwiki.org/wiki/Installing_openSUSE_10.2_on_a_ThinkPad_X60")[/COLOR]
[[COLOR="green"]http://packages.debian.org/testing/utils/i810switch.html]("http://packages.debian.org/testing/utils/i810switch.html")[/COLOR]
[[COLOR="green"]http://www.williambrownstreet.net/Linux/Dapper/]("http://www.williambrownstreet.net/Linux/Dapper/")[/COLOR]

---

