---
title: "Looking for small devise for Linux project"
date: 2012-04-06
forum: Hardware
---

### Post by samalex on 2012-04-06
Hi,

*s/devise/device in topic :-/  Just noticed that and UF won't let me change it.*

I'm looking for a small, low wattage motherboard that'll run Linux that has the following inputs/outputs:
- PS2
- Serial
- Booting from SD Card or USB thumb drive (need solid state storage of some sort)
- Onboard Soundboard (mic and speaker connectors)
- Onboard video with VGA output (basic video, nothing fancy)
- Networking would be nice, but it nor wifi are a must

I'd like the CPU to be somewhat mainstream but it doesn't need to have much memory or even a fast CPU... I just don't want much fuss installing Ubuntu on it.  Is Mini ITX still around?  I'm so disconnected with hardware anymore I'm not sure if this is even still an option or if there's anything smaller.

What I'm building is a device that'll handle X.25 APRS and packet signals using [soundmodem]("http://www.baycom.org/~tom/ham/soundmodem/"), which any amateur radio operators should be familiar with.  Basically I want the device as small as possible so I can mount it in the car with a small monitor and keyboard, and using soundmodem I should be able to connect a small 2m HT radio to handle that part.  But given I can build something around LInux I can add other capabilities to it as needed.

So any suggestions on an all in one board that's low power that Linux will be happy with?  I'll build my own case, but i'd like it as small as possible and as hassle free as far as getting Linux going.

Thanks and take care,

Sam

---

### Post by Paddy Landau on 2012-04-06
I'm not sure if it would suit your purposes, but have you looked at the [Raspberry Pi]("http://www.raspberrypi.org/")?

---

### Post by samalex on 2012-04-06
> **Paddy Landau said:**
> I'm not sure if it would suit your purposes, but have you looked at the [Raspberry Pi]("http://www.raspberrypi.org/")?

I actually looked at this, but I was afraid it would be too limited.  There's no real time clock and I'm not sure all the software I hope to run (soundmodem and xastir specifically) are supported on ARM... but at the price it would be worth trying since this little device is sweet.

---

### Post by winh8r on 2012-04-06
Pico ITX MBoards from here :

[http://www.mini-itx.com/store/?c=39]("http://www.mini-itx.com/store/?c=39")

might be of use to you.

they also sell small ssd's and various other components.

Hope this helps

---

### Post by samalex on 2012-04-06
> **winh8r said:**
> Pico ITX MBoards from here :

[http://www.mini-itx.com/store/?c=39]("http://www.mini-itx.com/store/?c=39")

might be of use to you.

they also sell small ssd's and various other components.

Hope this helps

Nice, thanks.  In the Mini ITX gambit I'm looking at this one was well from Newegg:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813121442](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121442)

It has pretty much exactly what I'm hunting for, and hopefully it'll run Ubuntu, unlike the Raspberry Pi which I thought was VERY promising until I read deeper.

---

### Post by ldsnet on 2012-05-08
> **samalex said:**
> Hi,
 
*s/devise/device in topic :-/ Just noticed that and UF won't let me change it.*
 
I'm looking for a small, low wattage motherboard that'll run Linux that has the following inputs/outputs:
- PS2
- Serial
- Booting from SD Card or USB thumb drive (need solid state storage of some sort)
- Onboard Soundboard (mic and speaker connectors)
- Onboard video with VGA output (basic video, nothing fancy)
- Networking would be nice, but it nor wifi are a must
 
I'd like the CPU to be somewhat mainstream but it doesn't need to have much memory or even a fast CPU... I just don't want much fuss installing Ubuntu on it. Is Mini ITX still around? I'm so disconnected with hardware anymore I'm not sure if this is even still an option or if there's anything smaller.
 
What I'm building is a device that'll handle X.25 APRS and packet signals using [soundmodem]("http://www.baycom.org/~tom/ham/soundmodem/"), which any amateur radio operators should be familiar with. Basically I want the device as small as possible so I can mount it in the car with a small monitor and keyboard, and using soundmodem I should be able to connect a small 2m HT radio to handle that part. But given I can build something around LInux I can add other capabilities to it as needed.
 
So any suggestions on an all in one board that's low power that Linux will be happy with? I'll build my own case, but i'd like it as small as possible and as hassle free as far as getting Linux going.
 
Thanks and take care,
 
Sam
 
I am looking at almost the exact same project! I was plannig on using Debian (because I am used to it!)
 
I am using an older laptop (that I already have) and the 7" stereo display in the dash for the display. Would like the opprotunity to compare notes as your project progresses (what radio, TNC, GPS and configurations settings you found that worked).

---

### Post by Evil-Ernie on 2012-05-25
I agree that Mini ITX is probably your best shot, I would also look at [www.linitx.com]("http://www.linitx.com") as they are specialists and I have got a lot of my MITX parts from there.
 
Raspberry PI is going to be a great hacking device and its unfortunate that Canonical wont be supporting ARM v6 but older versions can run on it, however if you look at the Raspberry PI route you should consider other distros.

---

### Post by james_xxx on 2012-05-25
I just wanted to interject that I built a machine using the Intel BOXD525MW motherboard/CPU a year or so ago. 

It's a great little board, and has worked flawlessly for me.

---

### Post by kd5mkv on 2012-06-28
Raspberry Pi, $25 to $50 dollars, people are running xastir, Linux RMS Gateways on this little machine.

---

### Post by pe7er on 2012-06-29
> **Evil-Ernie said:**
> I agree that Mini ITX is probably your best shot, I would also look at [www.linitx.com]("http://www.linitx.com") as they are specialists and I have got a lot of my MITX parts from there.
 
Raspberry PI is going to be a great hacking device and its unfortunate that Canonical wont be supporting ARM v6 but older versions can run on it, however if you look at the Raspberry PI route you should consider other distros.

I have various small Linux devises: SheevaPlug (ARM CPU, no VGA, runs on Ubuntu 9), PogoPlug (both ARM, and no VGA) and the Raspberry Pi (also ARM, it has HDMI + RCA Video, running on ArchLinuxARM).

I agree that regarding your needs & probably wanting to run it on Ubuntu, that building your own Mini ITX (with i686 and x86-64 architecture) might be the best solution for you.

---

### Post by onebir on 2012-06-29
How about [Via's Pi-alike](http://www.cnx-software.com/2012/05/22/via-technology-unveils-the-apc-an-arm11-49-android-pc/)?

Some other options [here](http://www.cnx-software.com/2012/06/26/list-of-39-low-cost-linux-friendly-boards-and-products/).

---

### Post by rg4w on 2012-06-29
Mini-ITX is alive and well.  While ARM offers cheaper options, if you need x86 there are a lot of affordable mobos available, from $69 and up:
[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007623+600009028&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=446&description=&hisInDesc=&Ntk=&CFG=&SpeTabStoreType=&AdvancedSearch=1&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007623+600009028&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&IsNodeId=1&Subcategory=446&description=&hisInDesc=&Ntk=&CFG=&SpeTabStoreType=&AdvancedSearch=1&srchInDesc=)

---

