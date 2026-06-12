---
title: "ubuntu 9.10 LG r405 wireless Howto Atheros AR5001 AR5007EG AR242x"
date: 2010-03-20
forum: Hardware
---

### Post by txtiger on 2010-03-20
Wow, this one feels like a rite of passage for my linux skills.  It took lots of time, but I got it.

Many thanks to all who contributed info over the years on these odd chipsets.

The core of the solution is here:

[http://ubuntuforums.org/showthread.php?t=921589]("http://ubuntuforums.org/showthread.php?t=921589")

The problem with most of the solutions that put in the madwifi driver is that this laptop uses the Fn+F6 key combo to turn on or off the card -- and apparently that does not work with any of the linux driver sets.

The key to the problem was finding that when you issue an ifup command you will get an Error 132.  This means the card is switched off.  The info is here:
[http://ubuntuforums.org/showthread.php?t=1312627]("http://ubuntuforums.org/showthread.php?t=1312627")

In my case (since the laptop came with the evil Vista installed) I had no XP drivers.

You can get the driver versions at:

[http://www.atheros.cz]("http://www.atheros.cz")

Another problem I had was with selecting the correct driver.  None of the XP drivers worked with my laptop.  However, the one that finally worked was in the set 
Atheros_ar5xxx_7.7.0.466-xp([www.station-drivers.com).exe](www.station-drivers.com).exe)

and was the athw.sys driver in the win2k folder.  You use the ndisgtk program to install it from the netathw.inf file.

Following the steps on the first link will get you set to properly run the drivers.

Then installing the drivers with ndiswrapper will get the wifi card hardware working.

The last step to get a connection is to go into the make /etc/NetworkManager/nm-system-settings.conf to look like:

Code:
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true
```

After a reboot then everything should be working.

The following commands are your friend and should be memorized [with the correct device numbers wlan0, wlan1, eth0, etc.]:

sudo lshw -C network
sudo ifconfig wlan0 up
lspci -vv
sudo rfkill list
sudo /etc/init.d/networking restart
dmesg | grep -e ndis -e wlan
sudo gedit /etc/modprobe.d/blacklist.conf
ndiswrapper -l
ndiswrapper -v
ifconfig
iwconfig

I hope this helps someone else in their troubleshooting as well.

---

### Post by 2hot6ft2 on 2010-04-25
Fix to that driver link
[http://www.station-drivers.com/telechargement/atheros/wifi/Atheros_ar5xxx_7.7.0.466-xp(www.station-drivers.com).exe]("http://www.station-drivers.com/telechargement/atheros/wifi/Atheros_ar5xxx_7.7.0.466-xp(www.station-drivers.com).exe")

this link below is broken> **txtiger said:**
> 
Atheros_ar5xxx_7.7.0.466-xp([www.station-drivers.com).exe](www.station-drivers.com).exe)


---

