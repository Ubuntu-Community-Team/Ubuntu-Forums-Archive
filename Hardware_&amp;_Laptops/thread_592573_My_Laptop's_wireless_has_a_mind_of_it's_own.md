---
title: "My Laptop's wireless has a mind of it's own"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by kavon89 on 2007-10-26
Laptop Specs: [http://kavon.org/sig.png](http://kavon.org/sig.png)

I am currently trying out 7.10 in Live mode, I have to use Safe Graphics Mode to boot into it, I'm assuimg that is because of my uncommon graphics chip. Restricted drivers manager has the Arthos HAL Layer enabled and after looking over at the Hardware Information, It seems I do have an Arthos chip.

On first boot nothing really went on with my wireless networking. The switch to turn it on or off didn't work, nor did the Fn+ F-key with a wireless picture on it. The wireless light was off when I managed to get it on somehow. Either I was lucky or after hitting the Fn + F-key a couple of times to turn on the device wireless it picked up my network.

I used Pidign and talked on TeamSpeak with friends but then when I tried the sleep function (I was testing compatibility with my laptop, brightness and microphone etc), returning from it was fine but I had no wireless connection afterwards. Neither the Fn combo or the physical switch did anything to get it back.

I will be able to post more specs when I get home. I think it's lspc or somthing which you guys need.

Also: 
#1 The Networking configuation thing in either Administration or Preferences never loads up, it just freezes. Network Tools work and while I had a connection up I pinged a computer on my network and it was fine.
#2 I had 100% cpu use on one core while the other idled. Seemed odd for a Live session as there isn't anything to index or really do, I'm pretty sure the system was just idling while I was trying to get wireless back and it might have been maxed on one core before I managed a connection, it was 1am when I was trying all of this.

---

### Post by MaximusTG on 2007-10-27
Yes, you should probably post an lspci output

I already found this link for you:
[http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller#UbuntuKUbuntuXUbuntuLinux710](http://www.linlap.com/wiki/Configuring+the+iwl4965+driver+for+the+Intel+4965AGN+wireless+controller#UbuntuKUbuntuXUbuntuLinux710)

---

