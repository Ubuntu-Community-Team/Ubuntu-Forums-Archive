---
title: "SparkLAN WPEA-110N"
date: 2009-08-18
forum: Hardware
---

### Post by Strange_Movement on 2009-08-18
I am considering buying a SparkLAN WPEA-110N mini PCI-E wireless adapter as a replacement for my Asus eee 901. I am particularly interested in this card as it has an Atheros chipset, is capable of draft-N, is cheap and requires only 2 antennas.

What I need to know is; will it be directly supported by Ubuntu (out-of-the-box) to work **completely** with **no** messing around at all ?

I really want to start being able to use the current kernel instead of having to stick with the kernel I have been using from *array.org*, as that doesn't appear to get updated. I believe that the only reason I have to use the *array.org* kernel is because the standard wireless adapter in the eee 901 won't work with WPA/WPA2 if I use the proper Ubuntu kernel; and I **must** have WPA/WPA2 usability !

If anyone's got a better hardware suggestion that would also be appreciated.

---

### Post by HiTechRedNeck on 2009-11-10
don't know if you ever got this answered or not... but I just installed one of these cards in my 1000HEB (removed RaLink RT2760). I too bought this for the Atheros chipset, as I have always had good experience with the company and their products.
 
before I switched, I was getting 130Mbps connecting to my WRT610N... and I could easily move about my 2600sqft home and most of my 9k sqft lot without loosing signal.
 
bear in mind, I didn't change the antennas... but that is my next project.
 
after the switch, I still had the same performance (speed & signal) from the 2.4GHz side of the card... but the 5GHz side was an impressive 300Mbps. the signal strength on the 5GHz side was a bit lower... but I'm on ch11 (lots of problems in general) and I didn't upgrade the antennas to 5GHz (hence my next project).
 
now at 300Mbps, with this card, signal was about the same in linux and windows (but less than 2.4GHz side)... linux had higher downloads speeds from the same sites/files (always been that way for me, better use of bandwidth).
 
I am carefully considering all options for a 5GHz antenna... but I'm leaning toward this one... [http://www.oxfordtec.com/us/p172/Laptop-Internal-Aerial-Antenna-U.Fl-plug-connector-60cm-Electrically-Isolated--easy-installation-no-need-to-open-the-Base-or-LCD/product_info.html](http://www.oxfordtec.com/us/p172/Laptop-Internal-Aerial-Antenna-U.Fl-plug-connector-60cm-Electrically-Isolated--easy-installation-no-need-to-open-the-Base-or-LCD/product_info.html)
 
unlike the tab kind, it would fit nicely in the right and left edges of my screen housing and the dipole design should increase signal. I'm planning on using drops of sillicon to keep the antennas in place. the actual antenna section of the unit is only about 2.25" long with the rest being cable and the u.fl connector for the wifi card. I think it will do real well... and I expect to see an increase in the 5GHz band signal strength...
 
on another note... if the signal increases as predicted, I will be installing a third antenna of the same type for my bluetooth module... I'm planning to scrape off the PCB antenna and solder the cable to the PCB to create a remote antenna... that should give my bluetooth headphones house-wide.
 
good luck...

---

### Post by HiTechRedNeck on 2009-11-17
well, I've had my AR9280 Dual-Band Wifi for about a week now and I learned something very important.
 
DON'T USE STOCK OS DRIVERS!!
 
let me explain... I've used this card in Windows XP SP2 & SP3; Vista SP1 & SP2; and Linux Flavors (Moblin, Ubuntu, Mint, Kubuntu, PCLinxOS). the one thing that any of the OS drivers had in common is that the card sees both 2.4GHz & 5GHz wifis, but there are not enough controls of the chipset options. Doing some testing in all of these OSs, most connected "out of the box". those that did, were actively scanning 2.4GHz & 5GHz at the same time. once connected, they continued to monitor both frequencies.
 
I noticed that when I loaded the client connection utility in windows (any), the utility allowed me to turn off the 2.4GHz radio when connected to a 5GHz wifi... and visa versa. when this specific setting was set, I seen a HUGE improvement in RF gain and throughput. (by throughput, I mean overall avg of download and upload speed... not connection speed)
 
the OS-based drivers in linux and those available through windows update without the client utility (using windows connection manager) lack the ability to turn off the other radio that isn't being used.
 
therefore the Atheros Drivers & Client Utilities are an absolute MUST for this card. I'd be safe to bet that other dual-band cards benefit from this same idea... just thought anyone thinking of this or other dual-band cards should know... this is what I found.
 
now I know that in Linux there is no Atheros Client Utility... but those that write the managers should consider the ability to control features on dual-band cards... it may just help system/network stability...

---

