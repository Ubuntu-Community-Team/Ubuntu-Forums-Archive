---
title: "Atheros 5006EG on Edgy"
date: 2007-02-18
forum: Hardware &amp; Laptops
---

### Post by Tauhshi on 2007-02-18
[SIZE="6"][COLOR="Red"]SOLVED![/COLOR][/SIZE]
Thank you everyone for all your help! You've helped my cousin come over to Ubuntu!

Ok, I'm clueless here. How do I go about installing the wireless driver for my Atheros 5006EG? lspci returns an atheros pci card, but doesn't give the model number, only an unknown. The card doesnt show up in the network manager. Also, I have no ethernet cable to hook the computer up with, but I do have my other Ubuntu laptop hooked up to wireless, so any thing I have to download must be downloaded to a USB drive . . .

---

### Post by Turmoyl on 2007-02-18
Try this:

sudo modprobe -r ath_pci
sudo modprobe ath_pci
sudo iwpriv ath0 mode 2

---

### Post by Tauhshi on 2007-02-18
Output:
```
neko@nekos-laptop:~$ sudo modprobe -r ath_pci
Password:
neko@nekos-laptop:~$ sudo modprobe ath_pci
neko@nekos-laptop:~$ sudo iwpriv ath0 mode 2
ath0      no private ioctls.

neko@nekos-laptop:~$ 
```

---

### Post by Turmoyl on 2007-02-19
Hmmm... that's odd, Tauhshi, but try ignoring that error and then gaining an IP assignment via DHCP, etc.

---

### Post by Tauhshi on 2007-02-19
Hmm, yeah, how would I do that?

Also, my network card doen't show up in the Network Manager . . .

---

### Post by Turmoyl on 2007-02-19
sudo dhclient ath0

---

### Post by Tauhshi on 2007-02-19
Ok, tried out SuSE, it didn't work either! Curse this wireless card!

I found out the model of the card, an Atheros 5006EG, cursed in every Google search result!

Oh, and on SuSE, it says dhclient isn't a valid command . . .

---

### Post by Turmoyl on 2007-02-19
This just keeps getting more odd.  The Atheros in my ThinkPad X60s is an AR5212 and it worked - other than the need to unload and reload the driver before each ESSID change - out of the box.

On a different note, who cares what SuSE does and doesn't do?  That flavor has been off on its own, violating standards of all kinds since its inception.  Now its owned by a company that refuses to innovate and forges agreements with M$.  Let it rot.

---

### Post by thomyorke38 on 2007-02-19
oh man, i had the same problem with my laptop wireless for the longest time! here's how i got it working

use automatix to install ndiswrapper, and then install it... go find the file net5211.inf on your windows partition (if you have one, otherwise google the drivers and get it from there) add that file into the windows wireless driver utility and reboot, and voila...

the problem is that this card is too new to be part of madwifi or be present in the restricted drivers package that comes with windows... but ndiswrapper seems to work for me, give it a try

---

### Post by zetaz7680 on 2007-02-19
Have you tried downloading (manually to a removable flash drive, etc) the Madwifi drivers from sourceforge? I use an Atheros wifi card 5005GS and the only way I was able to fix that problem was to install latest MadWifi.

---

### Post by Tauhshi on 2007-02-19
I thank you all for the help! (And sorry for the SuSE thing, I just thought maybe it'd work . . .)

Anyway, The Atheros 5006EG driver is in net5211.inf? So, the matching .sys file would be net5211.inf? Ok, is it possible to download ndiswrapper to a flash drive? I don't currently have access to an extra Ethernet cable . . .
[B]
EDIT:[/B] I've managed to get it to work! I used the Device manager in Windows to find the Wireless driver for my card. I then simply loaded it up using Ndiswrapper, and viola! It worked! Now, should I post the .inf and the .sys file somewhere so that other people can get it?

---

### Post by adam206 on 2007-11-05
Hey all, new to Ubuntu as of last night.  I have a Toshiba Satellite U300 with an Atheros 5006EG wlan card.  I was having the same problem: the device manager does recognize the wireless card, but wireless connection does not show up on network options.  I installed ndiswrapper and ndisgtk, and got the net5211.inf driver.  But when I add it to the wireless network drivers it says "invalid Driver", and upon restarting has no effect.  I have disabled the restricted driver (Atheros Hardware Access Layer (HAL)), but in restricted drivers it still lists it as 'in use'.

Any suggestions on where I can go from here to get the wireless working?  Im very limited in the command prompt but im learning, and desparate.  Thanks All!

---

