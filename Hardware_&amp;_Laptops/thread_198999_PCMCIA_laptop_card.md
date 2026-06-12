---
title: "PCMCIA laptop card"
date: 2006-06-18
forum: Hardware &amp; Laptops
---

### Post by cnayak on 2006-06-18
Hi,

  I'm planning to buy a PCMCIA card for my old laptop (which runs Ubuntu 6.06 and Win XP Pro) for accessing wi-fi (b/g) in my campus. Though all cards ship with drivers for WinXP but I wanted to use it with Linux too. Can you guys suggest a card that runs with Linux without any major hassles?

---

### Post by K.Mandla on 2006-06-18
I've worked with three or four wireless cards, some good and some bad.

[LIST]
[*]Microsoft MN-520 -- worked more or less out of the box, and isn't expensive.
[*]Linksys WPC11 -- also worked out of the box; Ubuntu recognizes and configures at installation
[*]Linksys WPC54G v.2 -- never could get this one to work, on any machine I tried. In the end it wasn't worth fighting over.
[*]Netgear WG511 -- also had trouble with this one; I think I got it to work, but it was a bit of a pain to handle.
[/LIST]
I also had a Belkin card that I ended up taking back to the store, but I think that one was defective since it didn't even work with the XP drivers it came with.

It's worth taking the time to find out what chipset is in each card, since that can make all the difference. I think the two I liked the best (the MN-520 and WPC11) both used the Prism2 chipset, and handle perfectly.

(As a side note, 802.11b has always been fast enough for me, because my modem-router connection doesn't do much faster than that. :rolleyes: )

Since you mentioned that it's an old laptop, [there is a thread]("http://www.ubuntuforums.org/showthread.php?t=125334") that's worth reading if it's a pre-Pentium 3 machine. There are some kernel issues that might be problems, if your computer is that old.

Good luck! :mrgreen:

---

### Post by cnayak on 2006-06-27
hey thanks!

 I'll get the Linksys card as they're easily available in India. 

 thanks again.

---

### Post by s360 on 2006-06-27
for the wireless cards supported by ubuntu, I prefer you to take a look at [this list]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Linksys cards are quite easy to get and it seems to me that most of them work (according to the list) in ubuntu after some tweaking.

---

