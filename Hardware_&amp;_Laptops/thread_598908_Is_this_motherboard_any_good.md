---
title: "Is this motherboard any good?"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Yes on 2007-10-31
Well, this motherboard seems to be pretty good, but it's so cheap I figure there has to be something I'm missing.  What you all think?

Here it is: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813130082R](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130082R)

---

### Post by Tanker Bob on 2007-10-31
I built my system around a slightly different version of that board. Works great. I have run 64-bit Feisty on it and now run 32-bit Gutsy. The board is very flexible and supports overclocking just about everything on it that has a clock. You can see most of my system components in my signature.

One caution--don't try to use the NVidia fakeraid in Linux. Use the Linux software RAID tools instead.

---

### Post by Yes on 2007-11-01
What would the Linx sofware RAID tools be?

And if the motherboard has a 24-pin power pin, could I use a PSU with a main connector that has only 20 pins?  Or would I run into problems?

---

### Post by Tanker Bob on 2007-11-01
The RAID software is mdadm. The manual says that 20-pin connectors will work. The manual recommends a minimum 450 watt PSU for stability. Upper end video cards have dedicated power pins as well with specific power requirements, which an older PSU wouldn't support.

---

### Post by Yes on 2007-11-01
So would 500W be enough, or do you think I might need more?

If a video card says that it needs a 450W PSU, and the motherboard needs 450W, then that does not mean that I need at least a 900W PSU, correct?

---

### Post by Tanker Bob on 2007-11-01
No. 500W should be fine. That's what I'm running in my system and it works fine. I've got not only the NVidia 8800 video card, but 4 hard drives and other intermal peripherals. You'd probably only need more if you used 2 NVidia 8800 cards in SLI.

---

### Post by Yes on 2007-11-07
Thanks.  That board seems to have jumped to $100, so I'm still looking.

I've found this one now: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813121099R](http://www.newegg.com/Product/Product.aspx?Item=N82E16813121099R).  It seems great - 3 PCI slots, up to 8 GB RAM, built in firewire, for only $55?  I'm just a bit worried because there's no reviews.  Anyone use this before?  Can you overclock with it at all?

And can you use slower RAM than what it says the memory standard is, or will I run into trouble?  I'd like to use some DDR2 667 sticks, but this board's memory standard is DDR2 800.

---

### Post by Tanker Bob on 2007-11-07
I'm not familiar with that particular board, but I believe that Intel's chipset doesn't suport IDE natively. They use an auxilliary chip to provide PATA/IDE support. Others have had serious issues getting IDE drives to boot in Linux with that aux chip setup. If you have SATA boot drives, it will probably work fine. That's just something that I remember from earlier this year. You can probably search this site for the original posts.

---

### Post by Yes on 2007-11-08
I won't be booting from an IDE device, but that's what my CD-burner would be.  Will that not work, or is the issue only with booting from IDE devices?

---

### Post by Mondoman on 2007-11-08
You will need to boot from the optical drive at least to install the OS, so that might cause a problem.  Remember, too, that "open-box" items from newegg may not come with any driver CDs, manuals, cables, or even the thin metal I/O shield with the cutouts for the rear ports.

---

### Post by Mondoman on 2007-11-08
Also, it's worthwhile to buy at least a decent-quality power supply.  On modern boards, the overall wattage rating is just an approximation; what really matters is the total wattage or amperage available on the +12V circuit(s).  The +12V circuit(s) are what power the CPU, the graphics card, and miscellaneous MB and other items, such as the hard drive(s).  
All modern power supplies should have a sticker on the side that lists the max current for each circuit (newegg usually includes a photo of this for each ps listing), as for this Hiper: [http://www.newegg.com/Product/ShowImage.aspx?CurImage=17-128-005-09.jpg&Image=17-128-005-09.jpg%2c17-128-005-01.jpg%2c17-128-005-06.jpg%2c17-128-005-07.jpg%2c17-128-005-08.jpg&S7ImageFlag=0&Depa=1&Description=HIPER+HPU-4M480-PS+480W+Power+Supply](http://www.newegg.com/Product/ShowImage.aspx?CurImage=17-128-005-09.jpg&Image=17-128-005-09.jpg%2c17-128-005-01.jpg%2c17-128-005-06.jpg%2c17-128-005-07.jpg%2c17-128-005-08.jpg&S7ImageFlag=0&Depa=1&Description=HIPER+HPU-4M480-PS+480W+Power+Supply)

You really want to avoid the lower quality power supplies, in order to reduce the chances of intermittent problems and/or sudden power supply failure.  The Hiper above will run you about $50 and is OK; for better quality expect to pay closer to $100 or more, and definitely avoid the "free" PSs that come pre-installed in cases.

---

