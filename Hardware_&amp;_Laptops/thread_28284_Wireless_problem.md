---
title: "Wireless problem"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by redteto on 2005-04-19
I am totally beginner with linux..
I've got a Belkin wireless card (model F5D7010).
I am following this guide ([http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)) to install my hardware, but i got some problems...when i try to install the windows driver i type ndiswrapper -i, then when i type ndiswrapper -l the computer returns:
"Installed ndis drivers:
bcmwl5 invalid driver!"

What i have to do??

---

### Post by jbharrison on 2005-04-19
[http://www.linuxquestions.org/hcl/showproduct.php?product=1898&sort=8&cat=128&page=1](http://www.linuxquestions.org/hcl/showproduct.php?product=1898&sort=8&cat=128&page=1)

---

### Post by redteto on 2005-04-19
[QUOTE=jbharrison][http://www.linuxquestions.org/hcl/showproduct.php?product=1898&sort=8&cat=128&page=1](http://www.linuxquestions.org/hcl/showproduct.php?product=1898&sort=8&cat=128&page=1)[/QUOTE]

Great! Now i got my driver working!

But i have some trouble with the configuration..I've actived my wlan0 (from system->administration->network), i configured it with DHCP, i entered my SSID's name...but i'm still not connected.....

Suggestions? 
(i'm following this guide [http://www.ubuntulinux.org/wiki/WiFiHowto](http://www.ubuntulinux.org/wiki/WiFiHowto))

---

### Post by Toddy on 2005-04-19
Check to see if your router is not set to "shared" authentication.  I believe that you have to use "open".

---

### Post by redteto on 2005-04-20
[QUOTE=Toddy]Check to see if your router is not set to "shared" authentication.  I believe that you have to use "open".[/QUOTE]

It's already set to "open"..

---

### Post by redteto on 2005-04-20
I don't know what to do..please help!

Maybe i do something wrong with the router configuration...the wireless settings of my router are:
Enable AP->YES
SSID->alice
Channel->6 (i tried also 1, and 11...random)
Security-> (I used "none" and i tried also WEP, but nothing changed)
There are lot of others settings but i haven't changed nothing

My wlan0 insted is configured like this:
ppp0->not configured
wlan0->configured and activated
eth0 not configured

The properties of wlan0 are:
This dispositive is configurated->YES
ESSID->alice
Configuration->DHCP


What i could do??

I also tried wifi-radar to scan for wireless signals, but i can't install and run it..

---

### Post by spd106 on 2005-04-21
Check out

[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

and follow the links for all makes with the same chipset/driver.

A common problem is the /etc/ndiswrapper/<driver>/*.conf file, the radiostate should be set to 0 not 1.

This usually manifests as the light not coming on when you boot up.

If you do a quick search in the networking or laptop subforums you will see lot's of similar threads about this or other cards with a similar (broadcom?) chipset. 

Often the rev number makes a big difference so double check.

Hope this helps.

---

### Post by redteto on 2005-04-21
Nothing changed..my driver i think it's running well, the led of the card is on.
If i type "ifconfig" i'v got "lo" and "wlan0" running...

It seems that all is running...but i can't connect...if i enter "ping google.com" i obtain unknown host name or something....

I'm very sad.. ](*,)

---

### Post by spd106 on 2005-04-22
Hi,

Does ```
iwlist wlan0 scan
``` show your router?


I have the belkin f5d7010uk card, during boot (despite a brief stall) it seems to be started but when i log in the card won't find my router.
However by removing the ndiswrapper module,```
sudo modprobe -r ndiswrapper
``` then reloading it, ```
sudo modprobe ndiswrapper
``` the router can now be seen.
 
This is strange, but it works for me.

---

### Post by redteto on 2005-04-22
No way.. 
With "iwlist wlan0 scan" i get this message:
"wlan0     No scan results"

even if i try "your method" :? 

 :(  :(

---

