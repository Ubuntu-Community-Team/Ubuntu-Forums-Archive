---
title: "Not Picking up Wireless Card"
date: 2010-02-03
forum: Hardware
---

### Post by jhonnyboy on 2010-02-03
Hello everyone, I was trying to install ndiswrapper and the drivers needed to get my laptop working with wireless properly. I never got around to finish installing the drivers although I did install ndiswrapper. I lost my wifi completely and my system doesn't even pick up my card.

My wifi was working with the default wifi software that comes with ubuntu. It was just lagging a lot. In any case...
 
I don't know many bash commands. Need a starting point. Anything would help. Thanks guys!

---

### Post by jhonnyboy on 2010-02-03
I have an Atheros Communications Wirelesscard AR2413 802.11bg

---

### Post by Cabs21 on 2010-02-03
did you try hardwiring into your wifi and updating drivers once you have another stable internet connection?

---

### Post by jhonnyboy on 2010-02-03
It was originally hardwired. I never finished to install ndiswrapper. It's suppose to be working with the hardwired connection, but the computer doesn't even detect my wifi anymore. Don't know what's going on. Any other way to test this?

---

### Post by jhonnyboy on 2010-02-03
When I try a iwlist scan bash command my computer displays:

lo Interface doesn't support scanning

eth0 Interface doesn't support scanning

From what I can see...the system isn't using my wireless card to scan for any available networks.

---

### Post by jhonnyboy on 2010-02-04
bump. Does anyone know why my wireless wouldn't be working?

---

### Post by Cabs21 on 2010-02-04
try using ```
ifconfig
``` or ```
iwconfig
``` and display the results so we can help you

---

### Post by Yellow Pasque on 2010-02-04
^ Yeah, that. Also, this should give information on whether any driver is loaded:
```
sudo lshw -C network
```

---

### Post by jhonnyboy on 2010-02-05
sudo lshw -C network results in only showing me the Ethernet connections.

iwconfig shows:

lo no wireless extensions.
eth0 no wireless extensions.

I loaded up a driver for ndiswrapper yesterday and it was working fine, to troubleshoot i uninstalled ndis and it all fell apart again. My idea no driver is loaded for the wifi. How can i install a driver to use with the default ubuntu network program?

---

### Post by Yellow Pasque on 2010-02-06
Post the output of:
```
sudo lshw -C network
```

---

### Post by bkratz on 2010-02-06
You might want to check out this thread and follow the link in post 2.
[http://ubuntuforums.org/showthread.php?t=1379627&highlight=AR2413](http://ubuntuforums.org/showthread.php?t=1379627&highlight=AR2413)

---

