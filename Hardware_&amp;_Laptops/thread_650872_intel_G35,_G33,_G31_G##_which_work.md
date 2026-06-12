---
title: "intel G35, G33, G31? G##? which work?"
date: 2007-12-26
forum: Hardware &amp; Laptops
---

### Post by hanasaki on 2007-12-26
Which of the Intel G##? chips are supported in Gutsy? I am looking at boards based on the G33, G35  I was looking at a G695 board but that seems to be older/slower, right?

ASUS P5E-VM HDMI LGA 775 Intel G35 HDMI Micro ATX
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131237](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131237)

MSI G33M-FI LGA 775 Intel G33 Micro ATX 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130120](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130120)

ASUS P5K-VM LGA 775 Intel G33 Micro ATX
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131187](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131187)

---

### Post by Anthony M on 2007-12-27
Bump, I'm interested in finding out which works as well...

---

### Post by iramhernandez on 2007-12-28
Has anybody tried a board with a G35 chipset?  I'm currently running an ATI video board and I'm tired of dealing with stupid driver issues.  Do intel chipsets fare any better?

---

### Post by hanasaki on 2007-12-28
I am new to Intel graphics with Linux - thus the post.  NVidia seems to be a safe choice in my past.

---

### Post by BLKMGK on 2008-01-17
I've got the G35 board - the mATX one from ASUS with the HDMI output. The P5E-VM HDMI. I've followed the instructions at [http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html) but past what they've said I'll be damned if I know what I need to do to complete the install.:confused:

Sound I'll do via optical using an ASUS header, the board also has Coax out. ALSA appears to at least see the hardware but I'm waiting on my optical board before hooking it up. I'm not a Linux wiz but right now I'm quite a bit frustrated with it.

---

### Post by wjlonien on 2008-02-27
> **BLKMGK said:**
> I've got the G35 board - the mATX one from ASUS with the HDMI output. The P5E-VM HDMI. I've followed the instructions at [http://intellinuxgraphics.org/index.html](http://intellinuxgraphics.org/index.html) but past what they've said I'll be damned if I know what I need to do to complete the install.:confused:

Sound I'll do via optical using an ASUS header, the board also has Coax out. ALSA appears to at least see the hardware but I'm waiting on my optical board before hooking it up. I'm not a Linux wiz but right now I'm quite a bit frustrated with it.

Hm.

What did you try to install? Gutsy? That still has a x.org server 7.2; you could try an alpha version of Hardy, which will bring x.org 7.3.

However, even that is dated from September 2k7, and it just brought support for the 965gm (or x3100 if you prefer that), AFAIK.

Intel has just opened (released) their documents concerning the G35 on Jan 31st, 2k8. I've asked Keith Packard, a developer of the intel-xorg-driver about the current development status (he didn't answer yet), but come on - from the release of these documents (with some 1,600+ pages) to a working driver, in just 4 weeks? I really don't believe it.

I'm also very interested in this shiny new hardware, but I guess you'll have to run Hardy (or from April, that would be Intrepid, or even a Debian Sid), and then wait and pray each day... we're only humans after all, right?

Just my 2 (Euro-)cents. If Keith finds the time to answer my mail, I'll post it here.

cheers,
wjl

---

### Post by BLKMGK on 2008-02-27
Yup, Gutsy 7.10 is what is on my box and it's running fine - just not with the Intel hardware enabled. This was replacing a full sized ATX board with a smaller mATX board so I wasn't willing to screw around too much to get it back to working (running XBMC). When I didn't find the results I needed and the Intel driver site didn't seem like much help I slapped an NVIDIA 8500 in it, ran ENVY, and called it a day. If I were doing it again I'd have gone a different cheaper way. Watching the grief some of the Windows guys seem to be having with this board is painful and I'm not willing to go through that on an OS I know less about when what it was replacing worked fine despite being too big. <shrug> Isn't there now a G38 chipset coming out already?

---

### Post by wjlonien on 2008-02-27
Hm I see - so you needed 3D? Or didn't you even get 2D working without that Nvidia card?

Oh, let me guess: you wanted that HDMI output working, right?

Please tell us a bit more about the issues you had.

> **BLKMGK said:**
>  Isn't there now a G38 chipset coming out already?

Hm - I've heard of these X38 and X48 chip sets (without integrated graphics), but I thought I read somewhere that the next IGP chip set from Intel would be the G45 or so... no idea where; must have been in the German c't magazine or so.

I'm very interested in the P5E-V HDMI, because as a normal ATX board that has more PCI slots, which is good if you want more than one TV card.

---

### Post by wjlonien on 2008-02-27
> **hanasaki said:**
> MSI G33M-FI LGA 775 Intel G33 Micro ATX 
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813130120](http://www.newegg.com/Product/Product.aspx?Item=N82E16813130120)

ASUS P5K-VM LGA 775 Intel G33 Micro ATX
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131187](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131187)

hanasaki,

these should run. Note that the Asus P5K-VM board is also built into a barebone from Asus, called the "Vintage3-P5G33" - see also a [Wikipedia page]("http://en.wikipedia.org/wiki/Intel_GMA") about the various Intel graphics.

BTW, BLKMGK, that is also where I read about the G45 aka X4500, which will succeed the G35 aka X3500.

If you get one of these boards with a G33 chip set, hanasaki, would you let us know if they work? Thanks in advance...

cheers,
wjl

---

### Post by wjlonien on 2008-02-27
Have you seen the thread at [http://ubuntuforums.org/showthread.php?t=647449&page=2](http://ubuntuforums.org/showthread.php?t=647449&page=2) - especially answer #12?

Looks like this isn't such a bad board after all...

---

### Post by BLKMGK on 2008-02-27
Do note that the digital out is COAX not optical as NewEgg has it listed. It's not a "bad" board but the cost  vs the utility I've gotten out of it are a bit skewed. I get digital sound out of it with no problem and video setup too but it was too slow running XBMC. My reqs were that I needed an mATX board, digital out (I wanted optical), and I wanted ASUS with an Intel chipset and this board does that - the HDMI wasn't a biggie.

If tis chipset is of interest checkout some of the Shuttle XPCs with 775 sockets too. For what you get these actually look lke deals and I wish I'd seen them first.

---

### Post by wjlonien on 2008-02-28
> **BLKMGK said:**
> checkout some of the Shuttle XPCs with 775 sockets

Well yes I did (I'm a vendor of pre-installed Ubuntu systems, and we offer these already).

cheers,
wjl

---

### Post by BLKMGK on 2008-02-28
Any reliability issues or heat issues with the XPC? Fully supported by Ubuntu? Same chipset being discussed here I believe. I'd like to try getting the accelerated video working on mine one day when I've got time but the NVIDIA closed source driver has worked well. Wish it accelerated as many kinds of media on Linux as it does on Winders.:(

---

### Post by ponzonik on 2008-04-23
G31 won't work with [k]Ubuntu 8.04. there is no way to get anything better than VESA out of it.

---

### Post by rommel74 on 2008-05-05
Just to share my experiences with the ASUS P5E-V HDMI:
  After days wasted trying to get HDMI working on this motherboard in X with my Samsung LCD TV I've given up, going back to my NVIDIA card, it seems to me that the edid info gathered by the Intel driver is incorrect and it ignores any modeline settings. ALSA doesn't work with SPDIF at all but OSS does kinda however no AC3 passthrough. I've also had issues with the SATA cables that came with the mobo which took ages to isolate, then the Intel 8500 CPU which is supposedly supported by this motherboard also doesn't work at full speed, I had to slow it down to a significantly lower speed just to get Hardy to boot into X, funnily enough when I put the same CPU into my second PC which is running an older Inter 965 chipset based motherboard, it works at full speed (3.16GHz), so its not a dodgy CPU. Thinking that I got a flaky motherboard I took it back to the vendor to get a replacement. Guess what, the replacement board is doing the same thing, even with the latest BIOS.
  The whole point of updating my MythTV box was to improve stability over my current setup, lower the power consumption a bit by using an all in one solution and to get AC3 to work which my aging motherboard (A8N SLI Deluxe) did not support. Well I got non of that with this garbage. I knew I should have gotten a Gigabyte board instead of the ASUS but impulse got the better of me again.
Can anyone suggest a good HTPC motherboard with at least 6 SATA ports, 2 PCI, 2-3 PCI Express slots and proper ALSA support with AC3/DTS passthrough ?

Cheers

---

