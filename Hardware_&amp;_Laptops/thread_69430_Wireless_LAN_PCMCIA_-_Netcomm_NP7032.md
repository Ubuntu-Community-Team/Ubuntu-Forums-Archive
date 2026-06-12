---
title: "Wireless LAN PCMCIA - Netcomm NP7032"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by mygoldrush on 2005-09-26
I am a complete novice to Linux and Ubuntu.  I have installed OS on an (older) Acer Laptop - Tavelmate 351TE.  Everything installed OK as far as I can see.  I have a Wireless LAN PCMCIA - Netcomm NP7032 (11Mbps IEEE 802.11b) which I have inserted, but does not work?? I thougt I might need Linux Drivers for it but can't find any, I need some help with this.  Thanks:confused:

---

### Post by dickohead on 2005-09-27
Hello - I too have a netcomm wireless card and have contacted netcomm a few times but have yet to get the card working. The problem with netcomm is that unlike Linksys, Netgear and Belkin, they are not major players in the networking game, they are just an Australian networking company and do not support Linux - sorry to break the news to you.

---

### Post by mygoldrush on 2005-09-27
Thanks for that info
Oh well, I will have to source a card that suports Linux, so you are suggesting I go for the major brands??  Thanks Again

---

### Post by dickohead on 2005-09-28
I am (this afternoon in fact) purchasing a: NetGear WG511T, after finding a fair few good revies and multiple sites claiming that it works well out of the box with the MadWiFi driver - so hopefully i get ti going! Will report back when/if it works.

---

### Post by az on 2005-09-28
[QUOTE=mygoldrush]I am a complete novice to Linux and Ubuntu.  I have installed OS on an (older) Acer Laptop - Tavelmate 351TE.  Everything installed OK as far as I can see.  I have a Wireless LAN PCMCIA - Netcomm NP7032 (11Mbps IEEE 802.11b) which I have inserted, but does not work?? I thougt I might need Linux Drivers for it but can't find any, I need some help with this.  Thanks:confused:[/QUOTE]


Your card will work in linux.  If not with native drivers, then with ndiswrapper.

Open a terminal and type:
dmesg
after you plug your card in a wait a few seconds.

Post the last few lines.

When you say does not work, do you mean no lights?  Do you mean you try but cannot configure it?  Does your old laptop support such a device?  Some old pcmcia slots only suppport 16-bit devices and most new pcmcia cards are32-bit.

There is also this bug which relates to older laptops: [http://bugzilla.ubuntu.com/show_bug.cgi?id=8575](http://bugzilla.ubuntu.com/show_bug.cgi?id=8575)

---

