---
title: "Graphic card intel mobil Mobile 915GM/GMS/910GML"
date: 2008-12-12
forum: Hardware
---

### Post by cr4nk on 2008-12-12
Hi, I have the [sony vaio vgn-fs715/w]("http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGNFS715W") with intel Mobile 915GM/GMS/910GML graphics and upgraded ram to ONE gig.

The graphics card seems to be installed properly, although the computer seems to be lagging while performing more graphincal tasks (having more windows open or playing games). I know my computer can perform faster and smoother because I had it for couple of years with xp.

I did the following command to check how much memory my card was using, because I was suspecting it was using not enough.
```

lspci -v -s 00:02.0

```

And this is what I got
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
	Subsystem: Sony Corporation Device 81b8
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0040000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

```

Looking at this as I understand it it seems to be using 256mb of system ram for video graphics. I dont think thats good because as far as I know my card is 128mb shared. 

Does this effect my performance in a good or bad way? and is it changable to 128mb if its no good?

---

### Post by cr4nk on 2008-12-14
^bump^

---

