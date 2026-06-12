---
title: "[SOLVED] Compaq V2000 Wireless not working --- BCM4318"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by borimrr on 2007-06-21
I have a Compaq v2000 with feisty recently installed on it.I tried ndiswrapper and now I can turn on and off the wireless button and can get internet only with a static IP Everytime i turn on the computer i have to run modprobe ndiswrapper and modprobe bcm43xx. Also when I do ndiswrapper -l it says the hardware is present with the drivers but that the inffile driver is invalid. I don't know if that's the problem. Any ideas?

---

### Post by oiper on 2007-06-22
I own a V2000 also. There was a time that I went through 3 drivers for that card before finding one that worked properly. You may have a working driver, but if not these drivers have worked for me. [http://bryan.bearscanfly.org/files/bcm43xx.tar.gz]("http://bryan.bearscanfly.org/files/bcm43xx.tar.gz")

You do NOT want to modprobe bcm43xx. The bcm43xx module is the opensource version and by my understanding, only works on unencrypted networks. You need to run 

```
gksudo gedit /etc/modprobe.d/blacklist
```

and add this line to the bottom of the file:

```
 blacklist bcm43xx
```

Then run ```
gksudo gedit /etc/modules
``` and add this line to the bottom of the file:

     ```
ndiswrapper
```

Now we can setup ndiswrapper again.

```

rmmod ndiswrapper
rmmod bcm43xx
ndiswrapper -r NameOfDriver

```

Then extract the drivers above, "cd" to where ever you extracted them, and run

```

ndiswrapper -i bcmwl5.inf
ndiswrapper -m
modprobe ndiswrapper

```

Hope that helps.

---

### Post by borimrr on 2007-06-22
The link for the drivers is not working.

---

### Post by borimrr on 2007-06-22
I got the drivers from another website but still the same problem. I can only connect with a static IP. DHCP and roaming mode say there connected but no internet. Also when I do ndiswrapper -l everything is good except it says bcm43xx for the alternate driver, I don't know if that's an issue.

---

### Post by oiper on 2007-06-25
Sorry to hear you aren't having any luck. I fixed the above link.

My ndiswrapper -l output is:
```
bcmwl5 : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
```

That is normal. 

Have you followed the instructions from the wiki? [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

---

### Post by borimrr on 2007-06-25
I found out how to fix my problem. I have to run "dhclient eth1" after I choose DHCP on my settings. Eth1 is my wireless interface some people might need to use dhclient wlan0. Thx for the help.

---

