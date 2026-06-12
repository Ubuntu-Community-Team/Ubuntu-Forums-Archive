---
title: "ndiswrapper &amp; wireless card (F5D7050 v2)"
date: 2005-11-20
forum: General Help
---

### Post by joelhaasnoot on 2005-11-20
Hi,
I have a Belkin USB Wireless Adapter model F5D7050 v2. I am trying to use it with my Ubuntu 5.10. 

I did the following commands and these are the approximate responses:
```

# sudo ndiswrapper -i /home/joel/rt2500usb.sys
blah blah added driver
# sudo ndiswrapper -l
installed drivers:
rt2500usb              installed driver, hardware present
# sudo ndiswrapper -m
adding to blah blah (something about the modprobe)
# sudo modprobe ndiswrapper

```

The last step seems to do nothing, it takes a long time and never finishes. Anybody have any hints, tips or tricks...

---

### Post by jimmyp on 2005-11-20
[QUOTE=joelhaasnoot]Hi,
I have a Belkin USB Wireless Adapter model F5D7050 v2. I am trying to use it with my Ubuntu 5.10. 

I did the following commands and these are the approximate responses:
```

# sudo ndiswrapper -i /home/joel/rt2500usb.sys
blah blah added driver
# sudo ndiswrapper -l
installed drivers:
rt2500usb              installed driver, hardware present
# sudo ndiswrapper -m
adding to blah blah (something about the modprobe)
# sudo modprobe ndiswrapper

```

The last step seems to do nothing, it takes a long time and never finishes. Anybody have any hints, tips or tricks...[/QUOTE]

What does the command dmesg say about the wireless card?  It will be at the end.  What do /var/log/syslog and /var/log/messages have to say?

---

### Post by joelhaasnoot on 2005-11-20
I have attached the files...
syslog.zip = /var/log/syslog
dsmeg.txt = dmesg output (last lines)

looks like linux keeps resetting the device?

---

### Post by ecobuntu on 2005-11-20
BTW if modprobe actually works it's silent.

---

### Post by treadlove on 2005-12-31
Pulling the USB plug, and then reinserting it did the trick for me.  After that, I entered "iwconfig", and then changed my network connection under System, Administration, Networking.

The USB dongle was then functional.

The problem I am still having is that, if I leave the dongle plugged in, on rebooting ubuntu, it hangs when trying to initialize the hotplugsystem.  The same pulling and inserting trick works here too, but is too annoying to tolerate for the long term.

Anyone have any solutions to this second problem?

---

### Post by tfarinella on 2007-06-24
sorry if this is an old topic i found it on googles and it applies


I tried treadlove's steps but i got this

```



# ndiswrapper -m
Adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper
# modprobe ndiswrapper
FATAL: Module ndiswrapper not found.



```

any ideas?

---

