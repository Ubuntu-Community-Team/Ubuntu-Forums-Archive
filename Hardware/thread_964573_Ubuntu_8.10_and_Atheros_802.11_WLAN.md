---
title: "Ubuntu 8.10 and Atheros 802.11 WLAN"
date: 2008-10-31
forum: Hardware
---

### Post by squalleitor on 2008-10-31
Finally i downloaded the latest ubuntu i had my hopes up for my laptop Acer Aspire 4720Z and its wireless Atheros card.

But my wlan wont work... i go to system -> administration -> hardware drivers, there appears "support for Atheros 802.11 wireless LAN cards" enabled and being used at the moment, also says that it has been tested by ubuntu developers.

But it just wont work, the driver only appears here, when i go to network configuration the wlan wont appear, i can only connect by cable.

Please... help... why it wont work? whenever i read says that "it should work" "that it has been tested", but not on my laptop...

---

### Post by farhill on 2008-10-31
> **squalleitor said:**
> Finally i downloaded the latest ubuntu i had my hopes up for my laptop Acer Aspire 4720Z and its wireless Atheros card.

But my wlan wont work... i go to system -> administration -> hardware drivers, there appears "support for Atheros 802.11 wireless LAN cards" enabled and being used at the moment, also says that it has been tested by ubuntu developers.

You need to find out which Atheros chip your laptop uses. Many of the newer ones are not supported by drivers included with ubuntu.

If it's a AR242x (aka AR5007) I've successfully got that working with 8.04 and 8.10 x86_64 on a Toshiba L305D using the steps described at [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192). Note that this requires compiling and installing the driver yourself.

AFAIK, you can also use ndiswrappers, but I haven't tried. Once you know what card you have, searching for the specific chip will probably give you more useful results.

lspci -nn 
or 
lshw -numeric -C network
may help you figure out what you've got.

You might also find this thread useful
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=739998](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=739998)


edit:.
The method described here [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default) is probably better than what I linked before.

---

