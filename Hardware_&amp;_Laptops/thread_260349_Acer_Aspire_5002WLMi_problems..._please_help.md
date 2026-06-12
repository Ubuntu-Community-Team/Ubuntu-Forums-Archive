---
title: "Acer Aspire 5002WLMi problems... please help"
date: 2006-09-18
forum: Hardware &amp; Laptops
---

### Post by gtkourounis on 2006-09-18
Hey there, i just installed ubuntu on my laptop, kind of a ubuntu noob, anyhow, i have two problems...

1. My graphics are not working corectly. Every inch or so there are vertical "bumbs" along the monitor. i guess i will have to install a specific driver to fix that problem (if you know what and how to do please show it in the most elementary way... as i said i am a linux noob)

2. My WiFi Card doesnt work, and as i have seen it is the one card that is doomed (broadcom 4318). This specific card tends to never work, so i was thinking of buying another card to connect to my computer (in the specified slot for WiFi cards), but if you could give me a tip on which card i should buy, so that it works "right out of the box" or with small modifications, please do.

Thats it for now.

Thanx in advance

PS: My computer Specs

# AMD Turion 64 ML-30 processor (1 MB L2 cache, 1.6 Ghz)
# 15.4" WXGA CrystalBrite TFT LCD
# 100 GB Toshiba MK1031GAS Hard drive (4,200 rpm) [80GB hard drive (4,200 rpm)]
# DVD-Dual (DVD RW/CD-RW)
# 1 GB DDR [512MB]
# SiSM760GX graphics card
# 8-cell Battery
# 802.11b/g wireless (with Acer SignalUp and Bluetooth) [ Bluetooth optional ]
# Windows XP Home Edition [Windows XP Pro ]
# Weight: 6.7 pounds (7.4 with adapter)
# 1.5" thick, 11 inches deep, 14.3 inches wide
# 3 USB ports, 1 type II PCMCIA slot, 1 VGA connector for an external monitor, 1 phone jack, 1 Ethernet jack, Line-in, Mic-in, Stereo-out

[http://www.notebookreview.com/default.asp?newsID=2657](http://www.notebookreview.com/default.asp?newsID=2657)

---

### Post by dyous87 on 2006-09-19
Aright i feel your pain I was a complete noob just like you a little over a year ago but little by little I'm getting much better. Don't give up you'll love ubuntu.

Anyway in order to get your graphics displaying right you may want to try selecting the sis drivers. Do this by opening up a terminal and typing:

```
sudo dpkg-reconfigure xserver-xorg
``` 

This should try to auto detect your graphics and monitor setup. When it gets to the drivers just make sure you select "SIS". This should work!

Now for the wireless I wouldn't go ahead and buy a wireless card just yet. Did you go to the ndiswrapper wiki page to see if you could get the windows drivers to work with ndiswrapper?

---

### Post by Azrael Nightwalker on 2006-09-19
I have the same laptop. Wifi works perfectly with ndiswrapper.

---

### Post by gtkourounis on 2006-09-19
dyous87 thanx a lot, i will try that when i get home. It should work, if not then i guess i will re-post. Thanx again. And for the WiFi card i guess azrael knows...

Azrael, i have tried to make my WiFi work so many times with so many different ways and it never seems to work. Could you please show me the exact steps that you took.... i really want to make this work, because windows just sucks... :P

And again, thanx a lot guys!!!

---

### Post by gtkourounis on 2006-09-19
The graphics card works perfectly now. thanx again dyous87

About the wifi i tried some other HOWTO's from the forums but none of them seem to work :(

EDIT:
just to inform you all, i guess all my problems have been solved. i fixed screens resolution problem and finally i got my wifi card to work YEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEEY. i have been trying for such a long time and now finally i am able to do it. (was able to do it with a program called Wifi-Radar)

and again thanx to everyone that helped me.

PS: I guess thats what makes ubuntu so good :P

---

### Post by bheema on 2007-07-30
Hey guys - I also have an aspire 5002, though mine is the LMI not the WLMI as most of you seem to be talking about... lucky me, the screen works out of the box (Ubuntu Feisty)... but I have been having a (*&^%$# nightmare of a time getting the WiFi to work. I've tried ndiswrapper with no effect 
ndiswrapper -l says:
bcmwl5: driver installed
device (14E4:4318) present (alternate driver: bcm43xx)

but nothing happens - the wee light on my wireless card doesn't light up and system>admin>netwrk shows no wireless at all. I have blacklisted bcm43xx in modprobe.d/blacklist.

I've followed instructions from 7 or 8 different threads and all of them have much the same result. I've also tried a whole flock of distros with the same problem. Windoze does work (well, it works as well as anything from Muckrosoft works...) so I know it's not a hardware problem... PLEASE SOMEONE - I'm just about willing to sell my soul for a solution to this one!

---

