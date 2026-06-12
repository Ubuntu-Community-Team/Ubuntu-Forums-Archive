---
title: "[SOLVED] Need help picking a MoBo/Chipset for 64bit Ubuntu w/ 8gb of RAM"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by BassKozz on 2008-01-05
It's time to upgrade my D865GBF/P4 3ghz system, and I am looking to build a new computer that will be used mainly for VM of multiple OS's.  I will run 64bit Ubuntu as the host OS so I can utilize 8GB of RAM and spread that out over the various VMs (WinXP, etc), this way I can run multiple VMs on this computer and consolidate some of the other machines I have in my house.  For example I could run 3 VM's and spread out the 8gb's across the various machines like so: **2gb host, 2gb VM1, 2gb VM2, 2gb VM3**.

I plan on initially going with the [Q6600]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115017") CPU to get the most bang for my buck, and then later upgrade to a Penryn 45nm proc once the novelty & prices drop on them (in a year or so).

I would prefer to stick to DDR2 only boards, due to the cost of DDR3.  But my concern is that once I upgrade to a Quad Core Penryn proc I won't be getting its peak performance due to the DDR2 memory I'll be using.  I've read that there are boards that support both types of memory (DDR2/DDR3), but the only boards I've seen that will support this only have 2xDDR2 & 2xDDR3 slots, and because I want to run 8GB of RAM I would have to purchase 2x4GB DDR2/DDR3 chips which as far as I know these don't even exist :(

My main concern isn't DDR3 compatibility but Penryn compatibility. I was wondering how much of a performance hit I will get by using a Penryn proc with DDR2 instead of DDR3, if the difference is negligible then I'll be happier saving money and going w/ DDR2.

Bottom-Line Requirements:
[LIST]
[*]Must support 8gb of RAM
[*]6+ Sata Ports (preferably w/ RAID support, but not nessesary as I can setup Software RAID in ubuntu)
[/LIST]

So the two main questions here are:
[LIST=1]
[*]How much of a performance hit will I see using a Penryn proc w/ DDR2 memory (vs. DDR3)?
[*]What's the best board/chipset I should use for this build?  Should I go X38 or save $$$ and get a P35 board?
[/LIST]

p.s. I am not a gamer, and I don't OC, so these features (overclocking ability, sli support, etc...) don't pertain to me.

Thanks in advance for any/all comments, suggestions.
-BassKozz

---

### Post by Joe Jarvis on 2008-01-05
Penryn is primarily a shrinking of the current C2D architecture, so there aren't a lot of new features planned.  Have you considered sticking with the current-scale architecture?  It will be a lot cheaper.  I'm partial to the Intel G965 boards, and own several DG965WHMKRs.  Driver support is good, supports 4 x 2 GB memory, and has 6 SATA II ports.

---

### Post by BassKozz on 2008-01-06
> **Joe Jarvis said:**
> Penryn is primarily a shrinking of the current C2D architecture, so there aren't a lot of new features planned.  Have you considered sticking with the current-scale architecture?  It will be a lot cheaper.  I'm partial to the Intel G965 boards, and own several DG965WHMKRs.  Driver support is good, supports 4 x 2 GB memory, and has 6 SATA II ports.
Wow, and only [$116 @ NewEgg]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813121052")... This might work.

But aren't the new Penryn chips going to be faster then the current chips that are available.  The main reason I want to beable to upgrade to a Penryn chip in the future is because I was under the impression that these chips would not only be smaller, cooler, and use less power, they would also be faster.  Is that not the case?

---

### Post by Joe Jarvis on 2008-01-06
I'm not familiar enough with the Penryn design to give a good answer to this.  Generally speaking I would think Penryn is bound to be somewhat faster.  Intel is now using a two year cycle for CPU releases.  First, they introduce a new architecture, like C2D.  Then the next year they refresh it, shrinking it to a smaller manufacturing process and adding some features incrementally.  It's a matter of opinion, but I think it makes sense to buy each time the new architectures get released rather than each refresh.  The next new architecture is Nehalem and is scheduled for release in 2008.  I would think they would be in peak production and reasonably priced by 2009.

---

### Post by Joe Jarvis on 2008-01-06
BTW, one afterthought.  Be forewarned that some of the Intel 965 boards are picky about memory voltages.  I mistakenly ordered the wrong voltage memory when I first started building around it.

---

### Post by BassKozz on 2008-01-06
Thanks again for your feedback Joe,

Why is it you prefer the **G965** over say a P35 or X38 chipset?

---

### Post by Joe Jarvis on 2008-01-07
> **B/-\ssKozz said:**
> Why is it you prefer the **G965** over say a P35 or X38 chipset?

The G965 includes the GMA3100X integrated GPU capable of 1080p60 video (i.e., full HD).  In August, 2006, Intel released working (but not fully featured) GPL video drivers for it.  Since then they have paid to continue the development of the drivers.  While not all the features are supported yet, they're more mature a year on now.  You can use Ubuntu's auto-update feature for packages and even delete your X.org.conf file (thus forcing defaults built into X) and it "Just Works" since people have had the freedom to build around it cleanly.  This is such a convenience compared to the old days with ATI & nVidia drivers.

---

### Post by BassKozz on 2008-01-07
> **Joe Jarvis said:**
> The G965 includes the GMA3100X integrated GPU capable of 1080p60 video (i.e., full HD).  In August, 2006, Intel released working (but not fully featured) GPL video drivers for it.  Since then they have paid to continue the development of the drivers.  While not all the features are supported yet, they're more mature a year on now.  You can use Ubuntu's auto-update feature for packages and even delete your X.org.conf file (thus forcing defaults built into X) and it "Just Works" since people have had the freedom to build around it cleanly.  This is such a convenience compared to the old days with ATI & nVidia drivers.

Ahh, I see, Thanks for clearing that up for me...

Will this on-board GPU also be able to handle Beryl ?
I am not a gamer so I don't need anything crazy, but if this could handle Beryl that would be AWESOME... anyone know?

Also will this board be able to support any 1333 FSB processors (i.e. QX9650 or QX6850)?

---

### Post by fivemack on 2008-01-09
> **Joe Jarvis said:**
> Penryn is primarily a shrinking of the current C2D architecture, so there aren't a lot of new features planned.  Have you considered sticking with the current-scale architecture?  It will be a lot cheaper.  I'm partial to the Intel G965 boards, and own several DG965WHMKRs.  Driver support is good, supports 4 x 2 GB memory, and has 6 SATA II ports.

I have just bought a DG965OT.

It does not support 4 x 2GB memory under Ubuntu, unless you downgrade the BIOS to version 1669; without this, the machine runs at about 1% of rated speed.  You can get it to run at full speed by adding mem=4096M to the kernel boot line; but this means you have two purely decorative memory modules, and there are prettier and cheaper decorations to be had than memory modules.

---

### Post by Yellow Pasque on 2008-01-09
The last time I checked, the G965 and G3x were blacklisted in compiz/beryl. Has this changed?

---

### Post by BassKozz on 2008-02-17
Went with P35 (see signature)
Thanks for all the help everyone :)

---

