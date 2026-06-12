---
title: "Networking problems with Dell Vostro 1510"
date: 2008-07-09
forum: Hardware
---

### Post by BoBWidget on 2008-07-09
Hello, hello. 

I have just bought a Dell Vostro 1510 laptop. It came pre-installed with Windows Vista, which I need to keep for ProTools audio work. I have also installed Ubuntu Hardy alongside as, quite frankly, it is awesome. 

My wireless/wired networking works fine under Windows but not under Ubuntu. 
When Ubuntu boots, with the wireless switch 'on', the indicator light stays off and network manager doesn't see a wireless card. The wired connection is listed in network manager but doesn't work. The icon indicates a valid connection whether a cable is present or not and firefox won't load any pages. 

I'm at a bit of a loss here. I've tried using the windows wireless driver with ndiswrapper, but the little indicator light stays off, even on restart, and I have had no luck with the wired connection at all either. 

The two cards are:
Wired: Realtek RTL8168C(P)/8111C(P) Gigabit PCI-E
Wireless: Dell Wireless 1395 WLAN Mini-Card

Thanks for any advice you may have!!

---

### Post by stats on 2008-07-10
the driver is in the repo now
if you dint install  ndiswrapper then skip steps 2,3,4 
1.Update & upgrade using update-manager/synaptic/adept etc
2.
```

sudo apt-get remove ndisgtk ndiswrapper-common ndiswrapper-utils-1.9

```
3. Remove the ndiswrapper line from /etc/modules
4. Disable wireless from the network manager applet and then

```
sudo modprobe -r ndiswrapper
```

If it cribs about module being in use, it means you have not disabled wireless
5. Restart, if there were any kernel upgrades
6. System->Administration->Hardware Drivers
I see a wl driver here. Make sure it says enabled and is in use.

worked for me with dell 1395 on inspiron 1525

---

### Post by BoBWidget on 2008-07-10
Cheers man, thanks a lot! Problem solved!
Wireless now working!

Thanks again!!

---

