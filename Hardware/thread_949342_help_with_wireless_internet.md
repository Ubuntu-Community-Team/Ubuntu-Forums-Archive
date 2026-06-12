---
title: "help with wireless internet"
date: 2008-10-16
forum: Hardware
---

### Post by capeman on 2008-10-16
HEY GUYS!:) i am use in Ubuntu  inside my windows vista laptop,my laptop has wireless internet and it works fine with vista YET when i go on ubuntu i have no idea on how to get it going with my ubuntu it works if i stick it in the Ethernet plug but not wireless one of my friends said download easy wifi radar or something but that doesn't work :(  so i seriously need some help! i love ubuntu more then vista right now just i hate the it how i cant connect to wireless i sure it can i just dunno how so some help would be nice  thanks in advance LACHLAN!

---

### Post by theirishfozz on 2008-10-16
Hi

First check and see if your card is supported. Type 
> sudo ifconfig
and have a look at what interfaces have been created. You should have lo, eth0 and any wireless interfaces created from valid device. If one exists (ath0, wifi0 etc) then you can just type 
> sudo ifconfig ath0 up
replacing ath0 with the name of your wireless interface.

If you didnt see any wireles interfaces your card probably isnt supported but that doesnt mean we cant get it working. You'll either need to use ndiswrapper to use your windows drivers on linux, or use madwifi. Check the madwifi site to see if madwifi is supported 
> [http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)
and if it is follow the instructions here:
> [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

Otherwise use ndiswrapper:
> [http://linuxfornewbies.org/forum/index.php/topic,3.0.html](http://linuxfornewbies.org/forum/index.php/topic,3.0.html)

A good start is generally removing any ndiswrapper installed with ubuntu and installing the svn version. I've never had success with the synaptic version.

Before you start working on ndiswrapper you need to get hold of your windows wireless drivers from your windows partition or from the internet.

---

### Post by Ayuthia on 2008-10-16
Fisrt, we need to figure out your wireless card.  Can you open up the Terminal and post the results of lspci -nn?

---

