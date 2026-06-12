---
title: "[SOLVED] Belkin Firewire 800 PCI"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by thebucksstop on 2007-03-08
Hi guys, hope you can help me out.

I'm in need of a new external hard drive for video editing, and have been looking at the Western Digital My Book Pro [URL="http://www.dabs.com/productview.aspx?Quicklinx=44D1&PageMode=1"], mainly for its FireWire 800 ports, as I will be using this drive with Macs at work as well as Ubuntu at home.

Currently, I do not have any FireWire 800 ports on my linux box, and am thinking of getting a Belkin 3-port card [URL="http://www.dabs.com/productview.aspx?Quicklinx=3N2Q&PageMode=1"]. Does anyone know if this card works nicely in Ubuntu/Linux in general? If not, has anyone managed to get this working?

Cheers!

---

### Post by TrioTorus on 2007-06-29
Hey,

Did you get it to work in the end? I'm considering the same thing: firewire 800 on linux. Please let me know how you did.

Thanks.

Dries.

---

### Post by thebucksstop on 2007-06-29
Dries,

I actually never got round to ordering the part, and am still blundering through with USB2. I'm going to need to do some video digitising and editing soon though, using an external hard drive and firewire only DV camcorder, so will be needing to get it sorted soon. I'll post back as and when I get something installed and working. 

After doing all sorts of shopping around at the time, [this]("http://www.shoppingcentre.net/shop/firewire-1394b-port-p-2471.html") card  looks like it should work - the chipset is listed as working at the linux1394.org hardware list.

Sorry I couldn't be more help
C

---

### Post by TrioTorus on 2007-07-12
I ordered your suggestion. Thanks. I'll let you know how it goes.

Don't worry. I won't shoot you if it turns out it doesn't work.
(I just might never look at your face again :-))

---

### Post by thebucksstop on 2007-07-13
Cool, thanks for letting me know.

Actually I bought some FW800 bits n pieces two days ago, but only got around to installing them yesterday. One was a PCI card from Maplins, the other was a PCMCIA card, also from Maplins - one for desktop, one for laptop. Cunning, no?

Well, in any case - the PCMCIA card was a plug-n-play job, it worked straight off the bat with no problems, on both FW800 and 400. The PCI card, now that's a different story. I'm not sure why, but I couldn't get it working last night when I dropped it in. It shows up when using [FONT="Courier New"]lspci[/FONT] or [FONT="Courier New"]lshw[/FONT] to list relevant hardware in the terminal, but I can't get it to pick up my external hard drive. Going to spend the day googling it up and pestering people on here to see what suggestions they have, and take another look at it this weekend.

Oh, I think our cards are both based on the same or very similar Texas Instruments chipsets, so it'd be good to know if you hit any problems with yours!

---

### Post by thebucksstop on 2007-07-24
Got the PCI card working - a few clean  boots and it started working and I've not had any problems since. Maybe some dodgy connections? I don't know, but in any case, I can vouch for both the PCI and PCMCIA cards currently stocked at Maplins.

---

