---
title: "Linux not ready?"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by coolmike890 on 2005-07-05
Hi,

I've been trying to install ubuntu on a hardware RAID0 setup. My mb is an ASUS A8N-SLI deluxe. My research thus far indicates that what I am attempting is not possible. If this is not true, please let me know the basic steps for installation.

If this is true, my question is: is this a failing of linux (and/or ubuntu) or of the mb/chipset/controller providers to provide adequate drivers. If linux is ever to be ready for prime time, things like this need to stop happening. True RAID 0 is not a mainstream use, but other hardware raids are used extensively in the business world. It is disappointing to see that these issues are left unaddressed. I don't know how to fix this, but I wish I did.

Thanks

---

### Post by nocturn on 2005-07-06
[QUOTE=coolmike890]Hi,

I've been trying to install ubuntu on a hardware RAID0 setup. My mb is an ASUS A8N-SLI deluxe. My research thus far indicates that what I am attempting is not possible. If this is not true, please let me know the basic steps for installation.

If this is true, my question is: is this a failing of linux (and/or ubuntu) or of the mb/chipset/controller providers to provide adequate drivers. If linux is ever to be ready for prime time, things like this need to stop happening. True RAID 0 is not a mainstream use, but other hardware raids are used extensively in the business world. It is disappointing to see that these issues are left unaddressed. I don't know how to fix this, but I wish I did.

Thanks[/QUOTE]

I don't know the board, but if your controller is supported and supports raid0, there shouldn't be a problem.

Now, it is possible that your controller is not supported (this happens).  The Linux community gets no support from most hardware vendors and I believe that Asus in particular is pretty hostile (last time I checked).

Our devs have to obtain all information by reverse engineering protocols and hardware, this is a time consuming task.  This situation should improve as Linux reaches critical mass (the number of users that make it impossible to ignore for manufacturers). 

Did you find some information about Linux support for your controller?  If so, can you post some links?

---

### Post by poptones on 2005-07-06
*is this a failing of linux (and/or ubuntu) or of the mb/chipset/controller providers to provide adequate drivers.*

Look at it like this: you bring home your shiny new motherboard and install it in your system, then are about to install windows when you discover... there are no drivers! You cannot install windows because your motherboard manufacturer did not include them on the installation CD.

Is this the fault of Microsoft?

What if you want to install OS X?

* If linux is ever to be ready for prime time, things like this need to stop happening.*

Linux has been playing prime time for a while now. But, just as with Windows or Macs, when you shop for hardware you need to buy products that are compatible. If documentation exists or if manufacturers supply drivers themselves, these are the people we need to support with purchase dollars.

the motherboard you mention is pretty new. And it's based on the newer Nvidia chipsets, which means it is very likely the manufacturer will NEVER give adequate documentation to the community - Nvidia hasn't done this yet, anyway. I too made the mistake of buying an Nvidia motherboard but will not be making that mistake again. 

Nvidia provides linux drivers themselves and so technically should be "supported" via those purchasing dollars I guess, but the reality of things is that their drivers often suck. I chose my motherboard specifically for the fancy Nvidia sound features but none of it works in linux and probably never will. They'll probably get the hardware RAID on your board worked out, but it may take some time.

[Did you look at this?](http://www.google.com/search?q=asus+a8n+linux+raid&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox&rls=org.mozilla:en-US:unofficial) It seems clear you are not alone.

---

### Post by c_dog on 2005-07-06
> I've been trying to install ubuntu on a hardware RAID0 setup.


Yes, you can set the the ASUS A8N-SLI deluxe up as RAID 0 under Linux.
Both of the controllers (Nvidia and Silicon Image) on the A8N-SLI deliuxe are not "real" hardware raid controllers, though. That said, it's probably isn't the best idea to use a sorftware RAID 0 for boot or root partitions. This is the same for when running on Winbloze too. If you're still set on doing it, you'll probably want use the Silicon Image controller. The Linux drivers for it are available on the ASUS sites.

---

