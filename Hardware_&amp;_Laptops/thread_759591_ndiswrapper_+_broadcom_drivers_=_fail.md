---
title: "ndiswrapper + broadcom drivers = fail"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by ak87 on 2008-04-19
Hi!

I have bought a new laptop from HP, dv6544eo, and I struggled with graphical issues a long time.
Finally I installed the beta version of the new Ubuntu, 8.04... And it worked!

The only problem is that my wireless doesn't work :(. I have a broadcom wireless card. In Ubuntu 7 there was restricted drivers I could enable, but in the new Ubuntu there is none... So I decided to try ndiswrapper. I followed a guide [http://aldeby.org/blog/?page_id=87](http://aldeby.org/blog/?page_id=87)

Here is the steps:
> 5.2 Wireless Broadcom

HP Pavilion Laptops with AMD Turion platform ship with a Broadcom wireless card. Unfortunately Broadcom is one of the least Linux friendly companies and in fact it does not provide any support for linux OSs (differently from e.g. Intel). Given this, support for linux is provided via ndiswrapper hack.

You can download the windows drivers here (these are for a Broadcom BCM 4328 but should work for all the series) then extract the archive in a folder you call DRIVER in your home directory.

Install ndiswrapper and follow the procedure:

sudo apt-get install ndiswrapper-utils

sudo ndiswrapper -i $HOME/DRIVER/bcmwl5.inf

sudo ndiswrapper -l

sudo modprobe ndiswrapper

To make ndiswrapper automatically run at each startup:

sudo ndiswrapper -m

OR we can add ndiswrapper module to boot modprobed drivers

gksu cat ndiswrapper >> /etc/modules

At next bootup your Broadcom wireless card will be recognised!

But nothing worked when I restarted my computer

So I downloaded the Broadcom Wireless drivers for WinXP from HP, and installed them with ndiswrapper, but still no good.

When I run:
```
sudo ndiswrapper -l
```

I get:
> bcmwl5 : driver installed
	device (14E4:4312) present (alternate driver: ssb)

So it seems to be installed... But the LED lamp on the front of the laptop is still orange (should the blue if it's on), and in network configuration no wireless devices are present.

What should I do??

Thanks 
//Alex

---

### Post by VeN0mizer on 2008-04-19
Did you try this workaround? Worked for me with this...

[http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

---

### Post by ak87 on 2008-04-19
It actually worked!

Thanks!

---

