---
title: "Ralink wifi driver &amp; overheating issues"
date: 2011-08-24
forum: Hardware
---

### Post by DeceptiveHornet on 2011-08-24
Hello!

I am really trying to migrate to xubuntu, though i am having two major issues of which i am hoping that some kind soul here might be able to help me with.

The first issue is overheating.

My laptop is HP Pavilion G7 1110so and is brand new. Just two weeks since i bought it.

I have tried installing both Ubuntu and Xubuntu, in case it had something to do with the gnome / XDE interface but they both have issues. I start the installation, and then the laptop gives me a black screen. When i reboot it tells me the computer was shut down or put into standby becuase it had become overheated. 

Is this a known issue with HP Pavilion laptops? I tried googling, but found nothing.

The second issue is the wifi. My laptop is using Ralin RT5390 802.11/b/g/n Wifi adapter. When i did manage to install *buntu, i can never connect to the internet. It doesn't recognize any wifi hardware at all. I tried plugging in the Ethernet cord directly to the router and it does connect to the net. But it still won't automatically detect the appropiate wifi drivers.

Any suggestions on these issues?

---

### Post by foresthill on 2011-08-24
On my brother's notebook with Ralink wifi, I was able to find a driver on the Ralink site. Ralink wifi does not seem to be supported right out of the box in Ubuntu, so you're going to have to hunt down that driver and install it.

IIRC, installation was a bit of a pain, because you have to "build" the driver yourself. It comes in a tar.gz file that you have to unzip, then you go into the terminal and navigate to the file and run the commands "make" and then "make install". 

That's the basic idea of how I did it. I think if you Google the Ralink driver and how to install it, and follow the instructions carefully, you ought to be able to get your wifi working like I did.

---

### Post by DeceptiveHornet on 2011-08-25
This sounds pretty promising. Is it as straightforward as it sounds, just unpacking it and running make / make install? 

This unfortunately still leaves me with the overheating issue. If i can't solve that, then there's little hope of using xubuntu at all. Any suggestions on this?

---

### Post by DeceptiveHornet on 2011-08-25
Bump

---

