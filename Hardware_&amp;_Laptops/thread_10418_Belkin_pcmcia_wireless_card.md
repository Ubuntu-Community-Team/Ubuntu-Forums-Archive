---
title: "Belkin pcmcia wireless card"
date: 2005-01-07
forum: Hardware &amp; Laptops
---

### Post by hack_benjamin on 2005-01-07
Have just installed ubuntu on my laptop and it picks up the pcmcia wifi card in the device manager but i can't see anything to do with it in /dev and i don't know if it autoloads the right modules etc.. starting from scratch (ie base system) how do you get it working??

cheers

---

### Post by tiiim on 2005-01-07
[QUOTE=hack_benjamin]Have just installed ubuntu on my laptop and it picks up the pcmcia wifi card in the device manager but i can't see anything to do with it in /dev and i don't know if it autoloads the right modules etc.. starting from scratch (ie base system) how do you get it working??

cheers[/QUOTE]
 can you run the network wizard and make a wireless connection?

Computer -> system config -> networking and create a new wirless network. Could be a chance your card may not be supported. If not go to the manafacture see if they done a driver if not google for a driver and see if exists.

---

### Post by el toro on 2005-01-21
What version card is it?  If it uses the Atmel chipset you need to apt-get the package "atmel-firmware" and restart PCMCIA services before it will work.  I've got a F5D6020 ver. 2 and it works great.

---

### Post by txcountymounty on 2005-10-11
[QUOTE=el toro]What version card is it?  If it uses the Atmel chipset you need to apt-get the package "atmel-firmware" and restart PCMCIA services before it will work.  I've got a F5D6020 ver. 2 and it works great.[/QUOTE]

Ok youre the 1st person ive seen actually get this card to work properly, i tried looking for the atmel-firmware package and apt-get didnt have it, I tried synaptic and no go there as well. can you tell me if it goes under another name. I just installed ubuntu leaving my old fc4 behind in an attempt to get this f5d6020 v2 to work

---

### Post by el toro on 2005-10-16
Actually, the more recent kernels (2.6.11/12?) have the driver for this card built in, so the atmel-firmware package is no longer necessary, at least in Breezy, afaik.

---

