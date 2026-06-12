---
title: "Dell latitude E6500 &amp; Intel 5100 wifi"
date: 2008-11-06
forum: General Help
---

### Post by b4rt on 2008-11-06
Hi,

I bought myself a Dell Inspiron E6500 today, and installed Intrepid.

The laptop has the Intel 5100 AGN network card, but it is not recognised by Ubuntu. Ndiswrapper does not work.

(Only the bluetooth light of my laptop seems to be lit. I have not yet seen the wifi light go on...)

Any help getting my card to work would be greatly appreciated!

Thanks in advance,

Bart

P.S: I posted this in General Questions since I cannot get an answer in the network section

---

### Post by khermans on 2008-11-11
I have the same laptop.  Interestingly, my wireless has worked at least once without ndiswrapper!  I have no idea how, but the only variable that changed was that I plugged in an SD card in the left-hand slot and restarted GDM/Gnome.  I was then able to connect to an encrypted network.  Weird?!?!  So I am very confused that I cannot make it work again even while rmmod/modprobing :-(

---

### Post by abdusamed on 2009-10-11
i CAN'T GET MY QOSMIO 5100 AGN WIRELESS WORKIN.. IT DOESN'T DETECT IT... i want ad hoc and connect to my pc's REMOTELY! helpz plz!

---

### Post by delcypher on 2009-10-11
You need to see if ubuntu has detected your wireless interface and loaded kernel modules for it.

In the terminal run
```
lspci -k
```

Look for your wireless card and see if any kernel modules are loaded, for example mine looks like this...
```

05:03.0 Network controller: RaLink RT2561/RT61 802.11g PCI
	Kernel driver in use: rt61pci
	Kernel modules: rt61pci

```

If it has a kernel module in use then good news, let's see if the interface is present, run

```
iwconfig
```

What output do yo get when you run these commands?

A little note on ndiswrapper: Ndiswrapper will not work if you have the kernel module for your card already loaded, even if it's not in use. You have to unload it first (where rt61pci is the kernel module for your wlan card) ```
sudo modprobe -r rt61pci 
```
Then you have to unload and then reload ndiswrapper
```
sudo modprobe -r ndiswrapper && sudo modprobe ndiswrapper
```

Let us know how you get on.

---

