---
title: "old hardware boots faster"
date: 2011-07-20
forum: Hardware
---

### Post by Redsandro on 2011-07-20
I can't wrap my head around this.

I have this **9 year old laptop**, and I installed **Lubuntu 10.10** on it. It automatically logs in and starts XBMC 'cause I mainly use it to watch manly television shows while doing the dishes.

The dvd bay is fried, USB boot didn't exist, and I cannot seem to do a PXE install without rewiring 8 blocks, so I'm gonna be stuck with it for a while. Not too much of a problem. It boots up really quick, and I now have a new laptop anyway.

This is a **brand new laptop**, and I installed **Linux Mint 11** on it. You know, just like Ubuntu 11.04, but without the grandpa interface. But is this new piece of equipment an improvement? Ofcourse it is. *But not while booting!* It takes 3 times as long to boot!

Remember this press-release? [*Ubuntu aims for ten-second boot time with 10.04*]("http://arstechnica.com/open-source/news/2009/06/ubuntu-aims-for-ten-second-boot-time.ars") lol! :P

Here, let me be totally specific:
```

Product Name		Intel Core i3-350M			Intel Pentium 4
Purchased in		2011					2002

Cores			2					1
Threads			4					1
Clock Speed		2.26 GHz				2 GHz
Cache			3 MB					256 KB
Lithography		32 nm					180 nm
Transistors		382 million				42 million

Distro			Mint 11					Lubuntu 10.10
Kernel			2.6.38-x				2.6.28-x
Boot time		55s					15s

```

Most of this time is booting, not loading the desktop or some graphical login. Come on! I want to be part of the future too, please.

For your entertainment, well actually for my own, I had Ubuntu 10.04 LTS on the new laptop for a while, too. It booted equally slow with a 2.6.32 kernel. I manually updated to a 2.6.35 kernel, because the .32 one didn't support my Thinkpad's ACPI, so I thought maybe it'd boot faster. When that didn't work, I went to Ubuntu 11.04 to Xubuntu 11.04 to Mint 11. Still slow on the boot.

Is everything getting slower? I remember surfing the channels on my analog television. I could clear 6 channels by the time my frickin' digital television changes one channel. Anyway, these laptops are ofcourse both digital and you can clearly see in the data specified above that the new laptop was built to be faster.

Can somebody explain why this isn't working like I pictured the future to be, or tell me why it's better this way?

---

### Post by tgalati4 on 2011-07-20
The Intel i3 is a consumer/crappy processor.  The P4 is a business-grade processor.

But to be fair, XBMC is a lightweight, single-purpose distro, with a lot of crap removed.

---

### Post by Redsandro on 2011-07-20
I am running Lubuntu. XBMC is just a software that runs after it is booted, not the distro I am using. I mentioned it to keep the reading more casual, but in fact it has nothing to do with it.

Consumer or not, 10 (!) times as much transistors and cache while booting 3 times as slow... Your point on quality is taken but far from satisfactory.

---

### Post by jocko on 2011-07-21
Install the package "bootchart" (I guess it is available in Mint too, since Mint is based on Ubuntu).

Reboot, wait one minute and then reboot again (the first boot after installing bootchart the boot is re-profiled by ureadahead, so that boot will not be representative for the typical boot process of your computer).
Browse to /var/log/bootchart to find a graphical representation of what happened during boot (note that the image for the latest boot does not appear until one minute after your desktop is loaded).
The bootchart should at least give some hint into what's causing the slow boot.

---

### Post by mastablasta on 2011-07-21
10.04 booted in 15 seconds when i had it on. no i moved to Kubuntu which take a bit longer.
 
10.04 still uses about 45 seconds to boot on a really old mashcine (1,2Ghz, 256MB ram). so i guess something is wrong in your configuraiton or during boot.

---

### Post by Redsandro on 2011-07-21
@jocko:

Thanks for the tip, but I had tried that already. The thing is, there's sooo much going on at the same time, it really doesn't show an obvious problem.

[SIZE="1"]Note that I found a PCMCIA WLAN card for the laptop which hadn't been updated since like ever, and after the update it booted in like 30 seconds, way slower than before. Still a lot faster than the future, but it's like were looking at a graph in the mirror. Oh noes. I hope it will get faster again after a bunch of boots.[/SIZE]

---

