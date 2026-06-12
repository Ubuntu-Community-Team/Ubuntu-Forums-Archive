---
title: "Flustered noob: the wireless network card."
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by PnP_Bios on 2005-04-19
Hello everybody. I have a bit of a dillemma. I have an hp pavilion ze5570us, and guess what? It has a Broadcom card in it.

I scoured the vast corners of the internet, and found NDIS wrapper, the one listed on source forge.

yay! I don't have to fork up 50 bucks for a PCMIA or USB adapter.

I get stuck when it asks for the sorce for the kernel.

Call me stupid, but I can't find the kernel source. I looked in /usr/src, and it was blank. I went to the package manager, and added the headers, but I don't think that is what it is asking for.

Then one of my friends suggested that I use apt-get like this
apt-get install build-essentials

it did nothing, says it couldn't find the package.

Am I just kinda screwed here?


Go slow, I'm still kinda new at all this. I'm only sticking linux on here so I can develop for the dreamcast.

---

### Post by spd106 on 2005-04-21
There is a great page in the wiki

[http://www.ubuntulinux.org/wiki/WiFiHowto](http://www.ubuntulinux.org/wiki/WiFiHowto)

This should answer most of your questions

also look at 

[http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards](http://www.ubuntulinux.org/wiki/HardwareSupportComponentsWirelessNetworkCards)

and/or you could search the networking subforum for other peoples problems with your kind of, or similar card.

Hope this helps

---

