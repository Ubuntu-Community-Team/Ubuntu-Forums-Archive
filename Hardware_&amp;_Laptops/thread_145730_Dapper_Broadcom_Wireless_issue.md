---
title: "Dapper Broadcom Wireless issue"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by mweston on 2006-03-16
I plugged my old Belkin F5D7010 into my new Dapper installatio - just to see what would happen. Much to my surprise, lspci identified it. However....

sudo lshw -C network

  *-network
       description: 802.11g CardBus
       vendor: Broadcom
       physical id: 0
       version: 4.5
       slot: Socket 1
       resources: irq:11
  *-network DISABLED
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth1
       version: 03
       serial: 00:11:50:07:5b:46
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.15-18-386 link=no multi cast=yes wireless=IEEE 802.11b/g
       resources: iomemory:16000000-16001fff irq:11


My question - why is my wireless network DISABLED? Can I enable it? How?

Help....please?:???:

---

### Post by eyebrowman92 on 2006-03-16
broadcom doesnt release any of their driver info, therefore the devs cant write drivers for the broadcom cards, which means you cant use it.  try a pcmcia wireless card

---

### Post by mweston on 2006-03-17
Understood - although I saw something claiming that Dapper could handle Broadcom chipsets.

My bigger problem, is that even using NDISWRAPPER, I can't get this card to work in Dapper - even though it performed beautifully in Breezy.

I picked up a cheap DWL-650 and tried it as well. No luck with the Linux-wlan drivers. NDISWRAPPER doesn't like the card either. No hardware detected.

It looks like I'm doomed to a wired network on my laptop.
Its an old Compaq Armada 7400 333MHZ

Any other suggestions are appreciated.

---

### Post by engla on 2006-03-17
No, dapper has introduced lots of things for Broadcom Wireless specifically. See it says driver=bcm43xx, that's the new driver they included.

I don't know what disabled in this context means, but I would not worry.. get Network Manager and try to configure this thing..

I can't help specifically since I don't use dapper daily..

---

### Post by mweston on 2006-03-18
Network manager does not help. It lets me set up WEP, but the card still shows as disabled in lshw. I like dapper, but it just doesn't seem to like my wireless choices. Perhaps I'll go back to Breezy - at least for now. 

If anybody has a last minute suggestion, please advise.

Compaq Armada 7400 333mhz - 128 MB RAM
trying to use a Belkin F5D7010(broadcom) or DLink DWL-650 rev.P(Prism2)

Thanks,

---

### Post by LinuxKid on 2006-03-19
> No, dapper has introduced lots of things for Broadcom Wireless specifically. See it says driver=bcm43xx, that's the new driver they included.

so you're telling me that dapper will be able to work with my acer that has a broadcom 802.11 b/g wireless adapter built in

OMG!!!!!!!!!!!!!

This would be the first linux distro to do that and then I can actually spend some time on Ubuntu doing better things than word processing

I can not stress this enough!!!!!!!!!!!!!!!

please tell me you're not lying!

---

### Post by dragomirov on 2006-03-19
Just a quick answer (ain't got much time to be more explicative)

Yes the broadcom wireless card works under linux, but the driver loaded along with the kernel isn't that good. It goes "DISBLED" all the time, so...

```
lmod |grep bcm
```

and you'll see something like 

```
bcm43xx               114444  0
ieee80211softmac       28544  1 bcm43xx
ieee80211              35144  2 bcm43xx,ieee80211softmac
```

"bcm43xx" is the kernel module that loads the driver for wifi card.

Remove it 

```
rmmod bcm43xx
```

and install ndiswrapper

h&k

---

### Post by LinuxKid on 2006-03-19
yes, but the ndiswrapper proccess is long and troublesome (well at least for me)

I'm still trying to get it to work, humph!

I guess it's better

(NOTE: too find out if I ever get it working just look at my signature ;))

---

### Post by dragomirov on 2006-03-20
Sorry for my late.

Well ndiswrapper isn't a big deal at all. You just have to have the windoze drivers (the .sys and .inf files). That's why ndiswrapper has been written for :D 

first you have to 
```
apt-get instalL ndiswrapper
```
then 
```
cd to/whatever/are/your/drivers
ndiswrapper -i yourdrivername.inf
sudo modprobe ndiswrapper

```
then type "iwconfig" and you'll have to notice a device called "wlan0" or something, that can be configured with "sudo network-admin" or by editing /etc/network/interfaces

You can find many tips [here]("https://wiki.ubuntu.com/WiFiHowto")

h&k

---

### Post by LinuxKid on 2006-03-20
no, I did that

It doesn't matter anymore (if you look at my sig), I had an actiontec pcmcia wireless lan card that didn't work in breezy, so I tried it in in dapper for the heck of it and now I'm typing from dapper :)

---

### Post by dragomirov on 2006-03-22
:KS 
so that' s fine! dapper rules

---

### Post by garethppls on 2006-04-04
[QUOTE=dragomirov]:KS 
so that' s fine! dapper rules[/QUOTE]
I did your tutorial it works well done, just one tiny issue... everytime I restart the system it reverts to bcm43xx  (the crap driver) can I just make it ndiswrapper at the start instead, or could you show me how

---

### Post by mweston on 2006-04-05
[QUOTE=garethppls]I did your tutorial it works well done, just one tiny issue... everytime I restart the system it reverts to bcm43xx  (the crap driver) can I just make it ndiswrapper at the start instead, or could you show me how[/QUOTE]
Try blacklisting the BCM43xx driver.

From terminal:
sudo gedit /etc/modprobe.d/blacklist

At the end of the file, just add the line "blacklist bcm43xx" and that should prevent the module from loading automatically.  


(thanks, elsewhere !! [http://www.ubuntuforums.org/showthread.php?t=155289]("http://www.ubuntuforums.org/showthread.php?t=155289")

Good luck!

---

