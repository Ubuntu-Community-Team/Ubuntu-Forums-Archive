---
title: "Anybody know which brand/model PCMCIA wireless card support ubuntu?"
date: 2006-06-24
forum: Hardware &amp; Laptops
---

### Post by JordanN on 2006-06-24
I'm planing to get PCMCIA wireless card G on my laptop using ubuntu 6.06. Anybody know which model and brand is suitable and plug and play? Thanks in advance!

---

### Post by evilghost on 2006-06-24
AFAIK just about anyone on the shelf that is a 'name' brand such as Cisco, LinkSys, NetGear, etc.

---

### Post by K.Mandla on 2006-06-24
For what I've seen, it's not so much the model and brand as the _chipset_ inside of it that determines how well it will play with Ubuntu.

I've had two or three Prism2 cards that were fantastic, but I've also had some Broadcom chipsets that I immediately turned around and sold on eBay. 

My advice would be to spot one in the store, see what chipset is in it, then search the forums to see how much work it will take to get it going. It's adding a step, but believe me, it's time saved in the end.

---

### Post by evilghost on 2006-06-25
There's always ndiswrapper too ;)

---

### Post by sawjew on 2006-06-25
I just bought one a couple of weeks ago and it wasn't until the 3rd try that I got one that worked.  I bought a Spirit (which you may not know as it's an Australian brand) which didn't work even though the chipset was supposedly supported (I can't remember what chipset now) then I tried a D-Link DWL-G630 which didn't work either (apparently Hardware Versions A to D work but I bought H/W Ver E which is not supported) and then I bought a D-Link DWL-G650 (H/W Ver C3) which I just plugged in, put in my WEP key and away it went.

By the way I tried the other two with Ndiswrapper too and couldn't get them to work that way either.

Happy hunting.

---

### Post by evilghost on 2006-06-25
Perhaps I'm just lucky, I've had a Compaq WL-110, Ambicom CF (with PCMCIA adapter), and a Cisco Aeronet card work fine.  My laptop uses a BCM4306 integrated wifi chipset and I'm using ndiswrapper with it... :D

---

### Post by JordanN on 2006-06-25
Just bought Linksys Wireless G WPC54G. I'm gonna try it tonight. If this doesn't work,  ndiswrapper can help? how can I install ndiswrapper as i'm new to linux, any guide for that?

---

### Post by sawjew on 2006-06-26
[QUOTE=JordanN]Just bought Linksys Wireless G WPC54G. I'm gonna try it tonight. If this doesn't work,  ndiswrapper can help? how can I install ndiswrapper as i'm new to linux, any guide for that?[/QUOTE]

The easiest way is to just open a terminal and type 
```
sudo apt-get install ndiswrapper-utils ndisgtk
```
then go to >Applications>Internet and you should find the graphical ndiswrapper cofiguration utility there.  This should detect your adapter and install the driver for you.

Good luck.

---

