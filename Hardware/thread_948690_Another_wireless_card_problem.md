---
title: "Another wireless card problem"
date: 2008-10-15
forum: Hardware
---

### Post by qjmoss on 2008-10-15
I'm a Ubuntu noob. I installed Ubuntu over my Vista partition for reasons that you can all probably understand. I have a new Sony Vaio laptop and i'm not even sure on what wireless card i have. I think it's an Atheros AR242x 802.11, But i'm not 100% sure. I've been working on getting this to work for a long time, about two weeks and still no luck. 

My laptop has an on/off switch but When i select both options no light turns on If anyone could walk me through this step by step because i'm sick of using my crappy Linksys USB. 

I've ran though a couple things. Such as downloading Madwifi and some otherthing, but i couldnt seem to get that to work. 
Thanks so much

:confused:

---

### Post by theirishfozz on 2008-10-16
If the light worked in vista that might be a problem. I can toggle the light (different laptop) in Ubuntu if acpi is working (yes by default). 

Find out your card by typing

lspci -v | grep ireless     (not wireless in case of different case)

If that returns nothing try just lspci -v and scan down the list.

Check the madwifi site to see if that card is supported. If not get hold of the windows drivers for that card and use ndiswrapper

---

### Post by qjmoss on 2008-10-16
lspci -v | grep  came up and said i have  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)



Anyone give me the steps to getting madwifi to work. My card is supported

---

### Post by qjmoss on 2008-10-16
quentin@quentin-laptop:~$ sudo ./madwifi.sh --reinstall
Found at least one Atheros device.
Checking build dependencies...
...build dependencies OK
Removing previous MadWifi installations...OK
Building MadWifi...OK
Installing MadWifi...OK
Loading kernel module...OK
It seems that the driver did not detect compatible hardware.

---

### Post by theirishfozz on 2008-10-19
hmm.. but your card is supported on the madwifi site?

According to madwifi you have the AR5007 EG wireless card, the EXACT same card as me. How strange!

I had a lot of trouble getting wireless to work. I'm not sure what steps you have taken so far but here's what I suggest.

Before you do anything, if you have a wireless button or switch on your keyboard (or as a function key) try and toggle wireless on and off. If it doesn't work then try and restart and see if it works then. If it still doesn't work maybe it needs drivers first. 

Follow the steps here: [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
Make sure you blacklist ndiswrapper.
> sudo gedit /etc/modprobe.d/blacklist
Add "blacklist ndiswrapper" to the list

If it doesnt work post what gets printed out when you try and load ath-pci. I have a problem outlined here: [http://ubuntuforums.org/showthread.php?t=884842](http://ubuntuforums.org/showthread.php?t=884842) where wireless works every second time you restart the computer. Apparently shutting down ubuntu correctly messes up the wireless card. Starting back up into ubuntu or windows after that means the wireless card doesnt work. The next restart is fine or if the computer is not shut down correctly also means it works ok. Only if the wireless card is currently working and ubuntu is shut down correctly. If you have the same card and OS you might have the same problem.

---

