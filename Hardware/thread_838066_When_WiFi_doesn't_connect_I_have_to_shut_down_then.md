---
title: "When WiFi doesn't connect I have to shut down then turn computer on again 2-3 times"
date: 2008-06-23
forum: Hardware
---

### Post by slayr007 on 2008-06-23
Does Anyone have any Idea how to fix this problem.
It'd be much appreciated.

---

### Post by chalewa on 2008-06-23
is it an atheros card?

---

### Post by ajopaul on 2008-06-23
If your card is identified and appropriate drivers laoded, then i assume its a problem with NetworkManager - the UI, whihc allows you to connect to a listed wireles.. 

Here's a old fashioned method. 

$sudo pkill NetworkManager
$sudo dhclient -r eth1 #Or wlan0 depending on your card
$sudo iwlist scan
 #This gives a list of wifi's available 
$sudo iwfconfig eth1 essid <essid-name> key <key if any>
$sudo dhclient eth1

eth1 can be replaced from the device name listed with sudo iwlist scan

Hope this helps!

---

### Post by slayr007 on 2008-06-23
It is an Atheros Card

---

### Post by slayr007 on 2008-06-23
are you sure that will work?:
$sudo pkill NetworkManager
$sudo dhclient -r eth1 #Or wlan0 depending on your card
$sudo iwlist scan
#This gives a list of wifi's available
$sudo iwfconfig eth1 essid <essid-name> key <key if any>
$sudo dhclient eth1

---

### Post by ajopaul on 2008-06-24
well, give it a try, u wont lose anything, restart will bring back NetworkManager anyways..

---

### Post by Flag on 2008-06-24
I have the same problem on an Acer 7520 with an Atheros card, instead of re boot, try : sudo rmmod ndiswrapper and sudo modprobe ndiswrapper.
It's not ideal, but it works for me, still am looking for a definite fix.

Good luck

---

### Post by Pha[N]toM on 2008-06-24
It's problem NOT only in Network Manager, or only in Ndiswrapper drivers...

My issue is: 
[LIST]
[*]turn off driver ( [COLOR="Green"][FONT="Courier New"]# sudo rmmod ndiswrapper[/FONT][/COLOR] )
[*]remove wireless network in [ RMButton menu at NM icon in tray > Edit Wireless Networks ]
[*]turn driver on ( [COLOR="Green"][FONT="Courier New"]# sudo modprobe ndiswrapper[/FONT][/COLOR] )
[/LIST]

Sometimes I've just need to on/off driver. 
It shakes me, I didn't like that, but this is Atheros... 

Sorry for my poor Eng ;)

---

### Post by slayr007 on 2008-06-25
yo man the code just destroyed the wifi connection i did have

---

### Post by Flag on 2008-06-25
Which code ? What did you do exactly ?

---

### Post by slayr007 on 2008-06-26
> **Flag said:**
> I have the same problem on an Acer 7520 with an Atheros card, instead of re boot, try : sudo rmmod ndiswrapper and sudo modprobe ndiswrapper.
It's not ideal, but it works for me, still am looking for a definite fix.

Good luck

This one

---

### Post by chalewa on 2008-06-26
ive got this problem too...

the only fix i have found for it is doing a hard shutdown/restart via the button. 

everytime i do it this way, the connection comes back on, but if i select shutdown or restart from the menu...doesn't work. 

i know its not ideal, but its the best thing i have come up with to date.



edit: and the purpose of that code is to turn off the driver, so if you lost connection, that is good...did you power the driver back on?

---

### Post by slayr007 on 2008-06-26
that's not my problem, it's only when I restart.  If I shut down from the menu, it takes 2-3 times but it eventually connects

---

### Post by krodiak on 2008-06-26
Use ndiswrapper

```
lspci | grep less
```

Then find ur windows driver.... then:
```

sudo apt-get install ndiswrapper-utils-1.9
cd to/your/inf/driver/
sudo ndiswrapper -i yourdriver.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
sudo reboot

```

Should do the trick

---

### Post by slayr007 on 2008-06-26
ndiswrapper doesn't show up:confused:

---

### Post by Pha[N]toM on 2008-07-08
Guys, and what in other distros?
Same problem?
Maybe Atheros must update her's proprietay, but linux-driver?
Maybe we must write open ...ah...mmm.. "letter(message)" to Atheros?

---

### Post by Pha[N]toM on 2008-07-23
Hey! there is successfull for me: [http://ubuntuforums.org/showpost.php?p=5103560&postcount=1](http://ubuntuforums.org/showpost.php?p=5103560&postcount=1)

YAHOO!!!

---

### Post by ajopaul on 2008-07-28
Just incase , 

Atheros Releases Free Linux Driver For Its 802.11n Devices

[http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for](http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for)

---

### Post by Pha[N]toM on 2008-08-05
Great news!
[sorry for flood]

---

