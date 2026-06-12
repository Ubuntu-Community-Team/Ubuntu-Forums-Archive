---
title: "wireless drivers of 10.10 can be installed in 12.04?"
date: 2012-06-11
forum: Hardware
---

### Post by wagnermarques on 2012-06-11
Hi

My Dell vostro 3450 wireless card do not wants to work.

[COLOR=Navy][COLOR=Black]wagner@note:~$[/COLOR] lspci -v | grep Wireless
[COLOR=Red][COLOR=Green]01:00.0 Network controller:** Atheros** Communications Inc. **AR9285** Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Dell Wireless 1702 802.11bgn Half-size Mini PCIe Card [AR9002WB-1NGCD][/COLOR]
[COLOR=Black]wagner@note:~$ [/COLOR][/COLOR][/COLOR][COLOR=Red]
[/COLOR]

Looking for a fix, I hit the page: 
[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)


but that drivers is not for my xubuntu 12.04, but 10.10.

So, I'd like to ask:
Shoud I install that drivers anyway?
Shoud try some another test before?

best regards!

---

### Post by sanderj on 2012-06-11
Open a Terminal, then type:

```
wget http://www.appelboor.com/dump/check-my-network.py
python check-my-network.py

```

Post the full output here.

---

### Post by Yellow Pasque on 2012-06-11
Make sure rfkill isn't blocking it: [https://bugs.launchpad.net/ubuntu/+source/rfkill/+bug/900030](https://bugs.launchpad.net/ubuntu/+source/rfkill/+bug/900030)

See also: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773154](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773154)

---

### Post by wagnermarques on 2012-06-11
the commands

sudo modprobe -r ath9k
sudo rfkill unblock all
sudo modprobe ath9k
from ([https://bugs.launchpad.net/ubuntu/+source/rfkill/+bug/900030](https://bugs.launchpad.net/ubuntu/+source/rfkill/+bug/900030))

fixed the problem.

I'm unable to connect right now but I'm seeing the wireless networks avaible now!!! I'll test the connection at my school latter!

Many thanks to Temüjin and sanderj!
Best Regards!

---

### Post by wagnermarques on 2012-06-21
Ok, round two!

I've tested the wifi card behavior in two cases:

1) **without a ethernet cable connected** and with wireless network avaible
     **The wifi card not work**, just the bluetouth card icon appears

     Obs:  after doing... 
     sudo modprobe -r ath9k
     sudo rfkill unblock all
     sudo modprobe ath9k
     The wifi card behavior not change!
 

2)** with ethernet cable connected** (camming from my adls modem)
     The **wireless networks available is detected** by my wifi card. 
     I could not test a connection because  I have not permission to connect with any of these networks detected at my house and I have not a wireless router. 
      In the same enviroment, when I disconnect the ethernet cable, the wifi device stops to works too. The ethernet connection icon disapears and wifi card icon too.


 I can't figure out what is the relationship with ethernet and wifi card have with each other, but maybe, this fact can help to solve the problem!

---

