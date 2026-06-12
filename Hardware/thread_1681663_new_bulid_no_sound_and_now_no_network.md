---
title: "new bulid: no sound and now no network"
date: 2011-02-04
forum: Hardware
---

### Post by pickarooney on 2011-02-04
I built a new machine today and installed my existing hard drives. The machine booted up into Ubuntu no problem but I have no audio output. I've checked the cables and all seems fine. In the sound manager I can see the onboard sound card and all seems fine, volume is maxed on everything. 

I decided to test with a PCI sound card and not only did it still not produce any sound but since I restarted I have no longer got a network connection. 

The network card has now set itself to eth1 and not eth0 but I can't figure out any way to get it to connect either with a fixed IP or DHCP. 

I'm pretty sure I didn't accidentally knock off anything on the motherboard when adding the PCI card. I since removed it but still no network.

---

### Post by pickarooney on 2011-02-04
I booted to a liveCD and have no sound or network there either... has my mothreboard blown up on its first day??

---

### Post by cascade9 on 2011-02-04
Which motherboard?

---

### Post by pickarooney on 2011-02-06
gigabyte ma74gmt -s2 with onboard ati sound card

---

### Post by cascade9 on 2011-02-08
Gah, I hate it when manufacturers do this- 

> LAN
[LIST=1]
[*]Realtek 8111D/E chip (10/100/1000 Mbit)
[/LIST]
[http://www.gigabyte.com/products/product-page.aspx?pid=3582#sp](http://www.gigabyte.com/products/product-page.aspx?pid=3582#sp)

so it could be either a 8111D or 8111E chip. :| I'm running a 8111D, and I dont recall any porblems when tried ubuntu on this machine. So its probably a 8111E. 

I'd check in your BIOS to make sure that the network and sound chips are enabled. You could also post the output from- 

sudo lshw 

Please put the output in 'code' tags. 

BTW, you dont have ATI sound, you have realtek ALC888B.

---

### Post by pickarooney on 2011-02-12
I finally got a replacement motherboard as the network card was confirmed DOA... and now this one (asus m4a78lt-m) will not recognise either of my IDE hard drives. It's enough to drive a man mental.

Before I set fire to the machine, or better yet, the shop, is there anything I could try to fix this? I've switched out the IDE cable and tried 4 separate molex plugs on the drives but the best I can get is one of the drives half-recognised in the BIOS as a garbled version of its actual name and nothing on the other one.

I have at least been able to retrieve the data using an external IDE case via USB but it's damn slow pumping 500GB across to my new internal SATA drive.

---

### Post by cascade9 on 2011-02-13
Network DOA....damn. 

I'd check your IDE jumpers. Its possible that both drives are set to 'master' or 'slave'. You should have 1 drive as 'master' and 1 drive as 'slave'. Or set both to 'cable select'.

---

### Post by pickarooney on 2011-02-13
As far as I know both are set to cable select. I thought the BIOS should at least recognise them as present even if it mixed them up?

---

### Post by cascade9 on 2011-02-13
If its not working with cable select, manually set master and slave, or try the drives one at a time.

---

### Post by pickarooney on 2011-02-14
I had one of the risers in the wrong position on the base of the case just unde teh IDE connector and the motherboard was shorting because of this. D'oh!

---

### Post by cascade9 on 2011-02-15
Doh! Did everything work after you fixed the riser?

---

### Post by pickarooney on 2011-02-15
Like a dream!

---

### Post by cascade9 on 2011-02-15
Good! :biggrin:

Heh, for some reason  alot of the smilies appear to be flashing. I wonder whats causing that?

---

