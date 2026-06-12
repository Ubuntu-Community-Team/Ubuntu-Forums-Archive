---
title: "issue with Acer 5520 wireless after jaunty update"
date: 2009-04-28
forum: Hardware
---

### Post by hombrebeastia on 2009-04-28
i have a acer 5520 series laptop with an atheros wireless card. it worked fine while i ran 8.10. i then updated to the new release and at first the wireless seemed to work but now my wireless isnt working properly. the drivers arnt loading properly it seems. here is what ive tried!

*iwconfig shows no wireless card

*lsmod shows both wlan and ath_hal loaded

*ive tried using the hardware drivers applet to select the unselected driver but it always says it has disable the driver: its not in use!

*have tried uninstalling and reinstalling the madwifi packet but that didnt work either.. 

is this a issue with the kernel?

it seem others are having issues with the bcm (intel) based cards also.

any help would be appreciated, thank you in advance

---

### Post by cabez0n on 2009-05-12
I have the same laptop and the wireless is working allright. I did a clean install though. 
You might want to get the madwifi-hal drivers, they certainly work. 
Just make, make install and reboot. 

Also, you might want to check dmesg if you say ath_hal and ath_pci are loaded. By the way, is ath_pci module loaded as well ?

Cheers

---

### Post by hombrebeastia on 2009-05-27
I have already downloaded part of the package through terminal, but when I try to sudo apt-get install cairo-dock cairo-dock-plugins- i get couldnt find package cairo dock plugins. I got rid  of my bottom desktop toolbar, and now all of my windows disapear when i minimize them. thankyou for the help before hand.:(

---

### Post by hombrebeastia on 2010-03-18
I have an Acer 5520, and I Have used the madwifi driver for my atheros card; with ubuntu 9.04. My internet connection is 16gb; and I can get maybe 1 to 9 mps when connected wirelessly. The madwifi driver turns my wifi card off if I enable it; Are there any other drivers? has any one had this problem with thier same Acer. Please help.

---

### Post by Goveynetcom on 2010-03-18
What can I say?
Clean installs perform much better.
Make back ups of your important files, then do a fresh and clean install.
I have updated a desktop from 9.04 to 9.10, but now it is very slow, and I had 9.10 working under a weaker system better.
If you can't seem to fix it, just do a fresh install.

It stinks, but sometimes you gotta do stuff you hate.

Update on any progress you have ;) .

---

### Post by norseman-has-a-laptop on 2010-03-18
> **Goveynetcom said:**
> What can I say?
Clean installs perform much better.
Make back ups of your important files, then do a fresh and clean install.
I have updated a desktop from 9.04 to 9.10, but now it is very slow, and I had 9.10 working under a weaker system better.
If you can't seem to fix it, just do a fresh install.

It stinks, but sometimes you gotta do stuff you hate.

Update on any progress you have ;) .

also if your going to reinstall reformate as well when you do that it runs way more smoothly

---

### Post by hombrebeastia on 2010-03-18
I fully agree a clean disc install runs smoothly; It did before. I recently got my enclosure; backed up everything and went to 9.10, and had terrible video problems; I believe it was a screen format issue. Anyway, I went back to 9.04 and just had the Ethernet plugged right in. I got my wireless and set it up. My girl's hp 15 gets 54 mbps and my itouch has no issues, so I believe it to be this driver. Idk what driver I am using, I attempted to enable madwifi for the Atheros, and it wouldn't allow the wifi card to come on. It simply wasn't there. I disabled, and reset, and had the same slow wirless connection. I can deal with it, but if anyone knows of a better driver for an Atheros card for an Acer 5520. Thanks for the advice, it was reassuring to know I did something right in clean installing.

---

