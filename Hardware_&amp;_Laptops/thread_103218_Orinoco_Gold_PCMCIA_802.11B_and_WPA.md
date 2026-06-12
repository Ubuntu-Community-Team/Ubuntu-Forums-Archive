---
title: "Orinoco Gold PCMCIA 802.11B and WPA"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by Liver on 2005-12-13
Gents,

I have a ThinkPad T23, and an Orinoco Gold PCMCIA B card.

I have been struggling to get WPA working with this setup.  I have followed the directions several times.

The computer / Ubuntu recognizes the card, installation of wpasupplicant and configuration goes well.

On restart the communication always fails, can not get connected.

My WinXP machine finds the router so it all ok on that end, and I have triple checked the router name and password.

[COLOR="DarkOrange"]What I am thinking is the PCMCIA card so old that it will not do WPA?  Could that be an issue?[/COLOR]

If you had to suggest a linux-foolproof mini-pci or PCMCIA wireless card what would it be?  I would rather go with the PCMCIA card, because this laptop is not internally wired with antennas.

I appreciate any and all help.

Liver

---

### Post by pgf on 2005-12-14
> 

[COLOR="DarkOrange"]What I am thinking is the PCMCIA card so old that it will not do WPA?  Could that be an issue?[/COLOR]


yes.

> 
If you had to suggest a linux-foolproof mini-pci or PCMCIA wireless card what would it be?  I would rather go with the PCMCIA card, because this laptop is not internally wired with antennas.



the Engenius or Senao (same thing) NL2511-CD is a fine choice.  it needs recent firmware (see [http://linux.junsun.net/intersil-prism](http://linux.junsun.net/intersil-prism) ) but then it will run WPA just fine.  (using hostap drivers and wpa_supplicant)

if someone else knows that WPA will run on the original poster's orinoco
gold card, i would love to hear it.

---

### Post by jml on 2005-12-14
pgf, you are correct.  The Orinoco Gold card does not support WPA.  In fact, virtually no 802.11b card will support WPA.  In addition to the cards you listed, generally any card that uses the Atheros chipset will work with Ubuntu and WPA.  The one chip set I would avoid if WPA is important are cards based on the Ralink rt2500 chipset.  That chip set is not supported by WPA_Supplicant.  That is the application needed to configure WPA encryption in Linux.

---

### Post by Liver on 2005-12-18
Thanks guys.  I figured that may be the issue and I appreciate the confirmation.

I snagged a AirLink 101 108 PCMCIA card at Fry's for $15, going to try it out.

Liver

---

### Post by Liver on 2005-12-21
Yup, the PCMCIA card was the culprit.  Now that I have roaming internet access I can start reading and learning about Ubuntu / Linux.

Liver

---

