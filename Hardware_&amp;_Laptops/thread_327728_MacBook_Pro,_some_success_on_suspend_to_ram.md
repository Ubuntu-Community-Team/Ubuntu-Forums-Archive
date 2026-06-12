---
title: "MacBook Pro, some success on suspend to ram"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by rougier on 2006-12-29
Hi all,

I've tried to enable suspend to ram on a macbook pro using s2ram and it seems to almost work, at least when I first boot into single mode: I suspend it with "s2ram -f -p -m", resume it with power button and then exit (Ctrl-D) to X. I'm then able to use "s2ram -f -p -m" to suspend again with fglrx/Xgl/beryl running. The problem is that I do not have wifi anymore at this point.

Now, if I directly boot into normal mode, I got wifi working but I cannot suspend using the exact same command. I suspect some wifi module to be the problem but I did not find any useful hints. Does anyone manage to use s2ram on a macbook pro or have some suggestions on how to investigate further ?

Nicolas

---

### Post by frigaut on 2007-01-29
Nicolas,

You're a life saver!!
This is quite an arcane combination, but it actually works. I've been trying for months to suspend with my macbook pro and fglrx/beryl/xgl, with no luck up to today. Thanks a bunch for your suggestions. Now how you came up with this thing is quite beyond me...

Anyway, on my side, all is working ok (as far as tested, right now, I have no more than 5 or 6 suspends) after the suspend: wifi, X...
What I have done is :
1. booted normally
2. stoped gdm
3. do the first s2ram -f -p -m
4. wake up (power button)
5. now I can start gdm and log in
6. to suspend again, swicth to vt1 and re-issue s2ram -f -p -m

I'll post more comments later as I get more experience with this.

---

### Post by frigaut on 2007-01-30
So far so good. I have not rebooted since I posted the entry above, and I went thru at least 30 suspend cycles. Xgl/Beryl/Network are all fine.
here is a bit of info on my machine:
poliahu:Desktop $ sudo s2ram -i
This machine can be identified by:
    sys_vendor   = "Apple Computer, Inc."
    sys_product  = "MacBookPro1,1"
    sys_version  = "1.0"
    bios_version = "   MBP11.88Z.0055.B08.0610121325"

Running Ubuntu edgy with the 2.6.17-10-generic distro kernel and uswsusp 0.5
I'm booting with noapic acpi=force irqpoll.

---

