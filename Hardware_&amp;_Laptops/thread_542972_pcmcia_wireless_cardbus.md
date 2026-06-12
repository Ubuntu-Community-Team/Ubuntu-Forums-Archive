---
title: "pcmcia wireless cardbus"
date: 2007-09-04
forum: Hardware &amp; Laptops
---

### Post by Lanman on 2007-09-04
Hi,  I,m an absolute newbe and I am trying to migrate from windows xp to Kubuntu on my IBM Thinkpad.  All has gone very well so far, but I have a wireless cardbus problem in Linux the card is not recognised and does not work, so i cannot connect to the wireless hub. The manufacturer (Peak) Mod 283717, Do not have any info on their site referencing the Linux system. Has anybody configured one of these cards, or can somebody suggest a Pcmcia card make to use instead, or other workable solution to my networking of this IBM Thinkpad. I have had to resort to posting this from windows, as you can see the dual boot installed just fine also. Thanks All for any helpfull advice.

---

### Post by PeterF on 2007-09-05
First we need to know what chipset the card is, you can find this by using the command lspci in the terminal. If the lspci command returns more then one result you can check which one is the correct one by removing the card. 
Once you know the chipset you can google for the right driver and a way to get it working or post back here.

---

