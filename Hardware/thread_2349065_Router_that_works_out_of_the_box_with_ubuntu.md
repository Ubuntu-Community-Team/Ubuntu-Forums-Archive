---
title: "Router that works out of the box with ubuntu?"
date: 2017-01-10
forum: Hardware
---

### Post by coldmachinery80 on 2017-01-10
hi i have been trying to get my mom on ubuntu but we bought three different routers and none of them worked. i realize now they were designed for windows and mac. the tech guy told me i should order a router that was designed for ubuntu. i would prefer the hardware to work with any linux distro but ubuntu compatibility is whats most important. 

i have an i7 4770 16 gigs of ram but she has a dual core with 3 gigs of ram that i upgraded to a quadcore q9450 and 4 gigs of ram. 

i should make clear that the modem upstairs is modem that connects by data cables and is cable not dsl based. 

the first floor has no data cable connection only a coax for the hd tv. so as far i know, she needs a usb dongle or someway for the computer on the first floor to receive the internet on a pc that i am not sure even has a nic card and im not sure if a nic card is required. what should i buy, and where?

---

### Post by lisati on 2017-01-10
It shouldn't matter that much. All the routers I've regularly used in recent years came with Windows and Mac support available, but no mention of Linux. I haven't had any issues using them with a machine running Ubuntu, either for regular use or accessing their browser-based control panel.

---

### Post by Irihapeti on 2017-01-10
You could occasionally get a router where the browser-based control panel would not work with any of the Linux browsers. Usually, it was Internet Explorer-specific. But it's been a long time since I saw any of those.

It might be useful to know what models the routers are/were that aren't working.

---

### Post by bearlake on 2017-01-10
Just a quick read, but can it be a hardware issue with the computer or as well a bad cable.

---

### Post by Irihapeti on 2017-01-10
True. If the ethernet NIC isn't working in Ubuntu, it wouldn't matter what router you were trying to connect to.

---

### Post by coldmachinery80 on 2017-01-10
i think you misunderstand. i have the cox modem an arris and everything the downstairs computer however does not any way to get internet service. so i have to use a wireless usb dongle to send the signal via wi-fi but with no usb wifi dongle we bought works with linux. both netgear and linksys do not have drivers for linux, its an issue of proprietary drivers. so i need a wireless usb dongle that work with foss and or linux software. i hope thats clear.

---

### Post by lisati on 2017-01-11
Oh, you're after recommendations for a USB dongle........
):P

---

### Post by Irihapeti on 2017-01-11
It might be worth looking at the adapters made for the Raspberry Pi. I've not used them, but they should work on Ubuntu. It will depend on what chip they use.

---

### Post by bearlake on 2017-01-11
First search done on [Linux USB dongle]("http://www.wirelesshack.org/top-linux-compatible-usb-wireless-adapters.html").

Many more available.

---

### Post by howefield on 2017-01-11
> **coldmachinery80 said:**
> .... so i need a wireless usb dongle that work with foss and or linux software. i hope thats clear.

[https://ubuntuforums.org/showthread.php?t=2346570&page=2&p=13583896&viewfull=1#post13583896](https://ubuntuforums.org/showthread.php?t=2346570&page=2&p=13583896&viewfull=1#post13583896)

---

### Post by efflandt on 2017-01-11
It is best to get a USB WiFi dongle that specifically mentions that it works with Linux (even if it mentions an older kernel version). For example when I was looking for one for a Raspberry Pi (computer on a credit card size board that runs Linux) I got a Sabrent from Fry's Electronics that specifically mentioned that it worked with some old 2.6 kernel I think, and it works fine. I also have a Linksys 56G WiFi dongle that works in Linux, but it is an older model and may use a chip that was more common and/or has had plenty of time for Linux people to figure out.

So it is not an issue with the router (which should be OS independent), you just need a USB WiFi dongle that Linux supports. Some that only have Windows drivers (and do not even mention Mac computers) can be rather complicated to set up to use Windows drivers, if they work at all in Linux.

---

### Post by SeijiSensei on 2017-01-11
I've used these USB adapters successfully with Ubuntu: [https://www.amazon.com/gp/product/B002SZEOLG/](https://www.amazon.com/gp/product/B002SZEOLG/)

It's a bit large but works well.  For something much smaller, I recommend this little guy from Edimax: [https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY/](https://www.amazon.com/Edimax-EW-7811Un-150Mbps-Raspberry-Supports/dp/B003MTTJOY/)

It doesn't have quite the range as the D-Link with its external antenna, of course.  If you need to reach a router across multiple floors, I'd probably go with that.

---

### Post by Autodave on 2017-01-11
I have had issues with the wireless USB, but I have never had any problems with a wireless card. I am assuming this is a desktop: if so, get a card for it. The external antenna on the card will be a plus, too. Any card seems to work: I don't even bother checking to see if they say Linux compatible.

---

### Post by him610 on 2017-01-11
I can recommend two external USB wireless adapters that work out-of-the-box using Ubuntu 16.04+ ....
TP-Link  TL-WN822N
Rosewill  RNX-N180UBE

Neither costs more than $20. Both have very good range.

---

