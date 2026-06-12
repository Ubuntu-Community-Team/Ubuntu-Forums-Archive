---
title: "Suddenly lost wireless... what went wrong?"
date: 2009-01-31
forum: Hardware
---

### Post by racyrefinedraj on 2009-01-31
All of a sudden my wireless hardware seems to have gone MIA. Here's the vital stats:

-Acer laptop, atheros chipset
-Hardy Heron
-I can see the hardware with lspci
-lsmod gives an entry for wlan pointing at that hardware (is that what I'm looking for?)
-I can't see the network device with iwconfig or ifconfig
-Obviously, network manager does nothing for me (the option for "enable wireless" went away)

What's the next step to diagnosing this?

---

### Post by Piro24 on 2009-01-31
You could 

> Sudo modprobe [name of driver] -r
Sudo modprobe [name of driver]

Though this is basic, usually when "enable wireless" dissapears, reloading the drivers fixs it.

---

### Post by racyrefinedraj on 2009-01-31
I just tried the following

```
sudo modprobe ath_pci -r
sudo modprobe ath_pci
```


and the driver is correctly loaded/unloaded, still no "enable wireless" option

---

### Post by racyrefinedraj on 2009-01-31
well what do you know, I tried modprobe a few more times and it worked. 

Crazy wireless gremlins. 

Anyway, thanks.

---

