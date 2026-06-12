---
title: "Question on wireless before installing on laptop"
date: 2006-09-10
forum: Hardware &amp; Laptops
---

### Post by comfortablynumb on 2006-09-10
I think I am ready to take the plung and install ubuntu on my IBM T23 laptop, I tried the live cd, and it ran good, I don't think it noticed my wireless card though.

I was wondering if it's because of the live cd and it doesn't load wireless drivers, or if maybe there isn't a driver for my  Cisco Aironet 340 pcmcia card (I beleive it's a Texas Instrutments chip)

Thanks in advance

---

### Post by daller on 2006-09-11
> **comfortablynumb said:**
> I think I am ready to take the plung and install ubuntu on my IBM T23 laptop, I tried the live cd, and it ran good, I don't think it noticed my wireless card though.

I was wondering if it's because of the live cd and it doesn't load wireless drivers, or if maybe there isn't a driver for my  Cisco Aironet 340 pcmcia card (I beleive it's a Texas Instrutments chip)

Thanks in advance

Running the Live CD, what is the output from the following commands:

Open a terminal!

Run this:

```
lspci
```

Sure it doesn't work? - What have you done to test it?

Testing if your system recognized the card as a wifi-card: (post me the output)

**Please have the pcmcia-card plugged in at boot time!**

...Then we don't have to take hotplugging into concideration! (If it does hotplug - that's another problem!)

```
iwconfig
```

---

### Post by A. J. Rimmer on 2006-09-13
"I was wondering if it's because of the live cd and it doesn't load wireless drivers,"

I don't think that is the case.  

Before I installed Breezy on this laptop I went to the library, turned on the WiFi card (Intel Pro/2200), booted with the live CD, and the network was immediately detected and connected.  I subsequently installed Breezy and then updated to Dapper.

I just bought an HP dv5220us.  Before I paid for it, we took it out of the box, put in the 6.06 LTS DVD (the one that comes with the "Official Ubuntu Book") and booted up.  The Intel 3945 WiFi was detected and we were able to get on the store's public network with no problems.

As a side note, we also tried the DVD in an HP 8000-series with AMD processor.  Everything worked but the Broadcom WiFi, but I have read on the forums that it is a simple matter to get that to work, too.

Hope this is of some help to you.  If you can figure out what kind of WiFI adapter you have, you should be able to get info on the forums that will help you find out what you need to do to get it working.

---

### Post by comfortablynumb on 2006-09-14
Thanks all for the replys, I forgot to update this thread. I went ahead and installed Kubuntu, I didn't realize that the wireless connection was considered eth1, I thought wifi0 would be my wireless card :confused: so I configured eth1 with my ssid, and my wep key and it restarted my cisco wireless card and I was online :)

---

