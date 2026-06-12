---
title: "RocketRaid 620/622/640/644 (updated kernel drivers support to 3.5+)"
date: 2013-04-30
forum: Hardware
---

### Post by GiveMeYourBacon on 2013-04-30
I was updating my system earlier tonight and I found from HighPoint, RocketRaid has updated their drives for the following cards.


[LIST]
[*]620 
[*]622 
[*]640 
[*]644 
[/LIST]

This latest open source driver supports v2.6.31 and above, I was able to install the driver by extracting the archive, [http://www.highpoint-tech.com/BIOS_Driver/rr62x/linux/rr62x-linux-src-v1.2-120601-1355.tar.gz](http://www.highpoint-tech.com/BIOS_Driver/rr62x/linux/rr62x-linux-src-v1.2-120601-1355.tar.gz) to get the other models the link is here. [http://www.highpoint-tech.com/USA_new/rr600_download.htm](http://www.highpoint-tech.com/USA_new/rr600_download.htm)

/Downloads/rr62x-linux-src-v1.2/product/rr62x/linux$ sudo make
/Downloads/rr62x-linux-src-v1.2/product/rr62x/linux$ sudo make install

Now I know that Ubuntu has a guide to setup through DKMS, this method works as well. However I thought I would share my experience by downloading these drivers. The installation was a breeze, also, I'm averaging 90-130MB/s on coping/moving.

I am running this off my home server system, I had to switch from Windows Home Server to something else. I was running Windows Home Server for almost 8 months and I noticed lag, and heavy fragmentation on several drives being Windows trying to install any 3rd party defragger was impossible. This desktop is accessed by 2-3 people in my house daily who love to stream videos. Speeds with this card and Windows were lower from 60-80MB/s a second.

I'm running kernel 3.5.0-27-generic, on an Intel I7-860, with 16gb DDR3-1333 | (1) 1.0tb WD Black [boot], (3) 2.0tb WD Green, (3) 2.0tb Samsung 2040ui, (2) 2.0tb Hitachi | Dual 5 Bay Sans Digital TRM5B with 5x2.0tb Samsung 2040ui and 5x3.0tb Seagate's. | **This machine doesn't have the sans digital configured in a RAID array** **due to the drives not being enterprise level or NAS level drives they are all run in JBOD Mode.**

I hope this helps, I know what struggle people have had with this card. I figured I would post this here so people could find it.

---

