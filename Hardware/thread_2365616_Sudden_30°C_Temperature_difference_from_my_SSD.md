---
title: "Sudden 30°C Temperature difference from my SSD"
date: 2017-07-08
forum: Hardware
---

### Post by lammert-nijhof on 2017-07-08
This summer I bought a somewhat strange 256GB SSD on Ebay. It was a case-less SDD, basically the card with a SATA connector. I put it in my desktop and via Conky it displayed constantly temperatures of 71°C while more or less idling. It continued in the seventies during the 2.5 weeks I had it installed. Compared to the normal HDD which showed 36°C it seemed very high. It did not go very much higher normally, only when copying GBs of data it would run up to 80°C. I took the panel of my desktop off and that saved 2°C. I tried to google the matter, some people also mentioned 70°C, but in the end I only saw only opinions and no reliable facts. Not knowing what was normal, I stopped worrying, put the panel back on and continued with my life. I live in the Dominican Republic and the  daily temperatures are around 30-32°C in the day and that is hot. In the  evening before going to bed, I switch on the airco at 28°C to lower the  temperature in the rooms, since the walls give part of the heat back at night.

Yesterday in the evening I noticed suddenly, that the SSD temperatures were 30°C lower and the temperature while idling was 42°C. It noticed it shortly after I switched on the airco, but that might not be the correct causality, since I did that all nights. I switched off the airco after 3 hours and for the whole night till 8 a.m. (now) the SSD stayed on 41-43°C.  

Yesterday I did run a software update on Ubuntu 16.04.That is the only logical explanation I can think off. Maybe the SSD got used to the tropical temperatures? :)  I did not touch the Desktop and it has been closed all the time. In the past weeks I never have seen the temperature drop below 70°C. Do you have any better idea?

---

### Post by CatKiller on 2017-07-08
It seems likely that it was simply mis-reporting the temperature before. It might be more accurate now, or it might be mis-reporting in a different way.

---

### Post by Autodave on 2017-07-08
Why is it doing that? I have no idea. However, if it were my machine, I would be looking for an extra cooling fan to mount in the case. Preferably, the fan would blow or draw air directly over the SSD. My SSD is normally around 40C and that is in a room that is air conditioned to 24C.

---

### Post by CatKiller on 2017-07-08
> **Autodave said:**
> Why is it doing that? I have no idea. However, if it were my machine, I would be looking for an extra cooling fan to mount in the case. Preferably, the fan would blow or draw air directly over the SSD. My SSD is normally around 40C and that is in a room that is air conditioned to 24C.

It hasn't changed so that it appears hotter, it's changed so that it appears cooler. I do not believe that the SSD was ever actually 70°C running in free air. The 40°C that it's reporting now seems feasible, but I wouldn't put too much stock in that reading either. It doesn't need any change in cooling as a result of the change in reading.

---

### Post by Autodave on 2017-07-08
I understand that. However, I have never had problems with anything inside a normal PC running cooler or too cool. A $5 or $10 high flow cooling fan would calm my fears about it ever overheating. Normal off-the-shelf PCs rarely have excess cooling capacity and especially in the climate that he is in.

---

### Post by lammert-nijhof on 2017-07-08
I had been thinking about mounting a cooling fan, I had lying around, but I did not do it yet. Partly because here they sold me a fan with a Molex connector and my power supply has no Molex connectors anymore. Partly because none of the other temperatures (CPU nor GPU) ever exceeded 75°C. Now I think I don't need it. I like to agree with most of the replies, The reporting has been wrong in the past and it has been corrected by the last update/actions. Why?

I remembered that the SSD on /dev/sda replaced a 80GB HDD on /dev/sda and I used the same sata cable, but I re-installed the system including hddtemp, but all in the same way as before. Ubuntu recognised the SSD and installed it correctly, also running trim periodically. I did change the BIOS boot priority yesterday, by putting the disk before the USB in that list. Strangely it reads now:

Hard Drive
--- Internal SATA
USB Device
ATAPI CD Drive
Network Boot Disabled

and the device configuration in the BIOS reads

Hard Drive
---- Sata0   253GB, 256GB
---- Sata1   500GB, <and the full Seagate type number>

It boots from the SSD, so the BIOS thinks the SSD is a HDD. My HP dc5850 system is from October 2008 and its/my latest BIOS is from 2011. The BIOS also recognises my Phenom II processor as "Phenom type unknown". The SMART implementations of SSD and HDD will be different, maybe the BIOS and/or hddtemp were confused with respect to SMART. Changing the boot sequence or an Ubuntu update corrected that. At least that is what I want to believe.

Wild guesses but I am happy now with the temperature displayed. During the day it was in between 43-47°C and now after starting the airco and during this update it dropped to 38°C or as I remember 100°F.

---

### Post by gordintoronto on 2017-07-08
Many SSDs have no temperature sensor, including my Samsung 750 EVO. Are you using hddtemp to get the temperature? What is the brand and model of the SSD? It might be reporting some number which has nothing to do with the temperature.

---

### Post by lammert-nijhof on 2017-07-09
Yes, I do use hddtemp. The brand and model of the SSD is completely unknown to me. I bought it on ebay from a 99% UK seller and like I said; it is without case and basically a card with the electronics (Samsung nand flash) and a sata connector. It has 253GB and I bought it cheap for $66. I assume this type of case-less SSDs have been used in the past in servers, but now they are too slow and obsolete. Maybe that is why this SSD has a SMART function unlike your Samsung 750 EVO. 

The Conky (hddtemp) read out moves like a temperature read-out, It moves in proportion to the room temperature, while idling and if the load increases it get higher fast. So if it walks like a duck and quacks like a duck, it is probably a duck. SMART as presented by the Disk Utility, only has a few read outs and error counts are zero, only temperature; power-on count and power-on hours are non-zero values. The SSD seems brand new.

End of the day if nothing changes I will close this thread. That splendid piece of Open Source Technology: 'Ubuntu' has solved a potential temperature problem. How, I think it's magic and beyond our comprehension.

---

### Post by gordintoronto on 2017-07-09
The brand and model would probably appear in lshw. In a terminal windows, I enter two commands:
cd Desktop
sudo lshw -html > myconfig.htm

The file goes onto the Desktop, and opens in the default browser. Drive information is at the bottom of the page.

If you know the brand and model, you can probably find the specs.

---

### Post by lammert-nijhof on 2017-07-09
No, I tried everything, BIOS, Disk Utility and lshw all give as type information 256GB or 256GB (P1003BR) and as size 253GB and nothing else. Google does not give any useful link unless you are interested in brim stones. One day I want to look, if there is small print at the card again, but now the SSD is lying on its bed of an old mouse-pad in the disk bay, tied down by a rope.

---

