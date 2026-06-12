---
title: "What video card does it need? (desktop)"
date: 2012-10-07
forum: Hardware
---

### Post by uberBrandon on 2012-10-07
Hello,

A friend recently donated me an old tower desktop his father used for video editing years ago. I tried to boot it up and install ubuntu precise on it, it booted fine but then when loading the system the screen kept on going blank. 
It seemed they had the main graphics card removed and that I got the VGA cable stuck into a sort of integrated "auxiliary" graphics card soldered on the motherboard that gets kind of disconnected when one loads into X or something like that.
I tried to look on google for what kind of graphics card I needed to get the system going, but I seem unable to get it, and my mate told me either him and his dad didn't know. Sorry if this may sound silly, but since I always had notebooks I'm very n00bish with desktop hardware. Here is the pic: 

[IMG]http://sphotos-a.ak.fbcdn.net/hphotos-ak-ash3/560581_10151188652809054_2085484850_n.jpg[/IMG]

May anyone give me some hint on how I may get the machine running? everything else seems to be going fine.

Thanks, best regards.
Fede.

---

### Post by TheFu on 2012-10-07
The bus used could be PCI, AGP, PCIx or PCIe bus.  That brown slot does look like a PCIe slot. [https://en.wikipedia.org/wiki/PCI_Express](https://en.wikipedia.org/wiki/PCI_Express)

I'd check based on the specific motherboard vendor, model and submodel specifications?  Did you look that up to see what type of video slots are in the PC?

Most of the time I put a $50 nvidia card into my systems.

Knowing the specific motherboard will let you google for any tips and tricks to get Ubuntu installed too.  We really need that information **and** exact error messages to be helpful.

---

### Post by uberBrandon on 2012-10-07
Thanks for your kind reply theFu.
It's a Gigabyte ga-7vmm rev. 1 ([http://www.gigabyte.com/products/product-page.aspx?pid=1307](http://www.gigabyte.com/products/product-page.aspx?pid=1307)), which should have an embedded trident blade 3d (sth like 8mb or so) video card.

Actually it does not show any kind of error.. It shows the BIOS loading correctly, but when I try to load any OS (windows, ubuntu, reactos and puppy) the video signal switches off.. like it's switching to another video card (which obviously there isn't). Given even the crappiest video card seem to cost as much as I would pay for a PC with the same specs on a flea market, I would try to make it work with the embedded video card. But how could I? I tried to mingle a bit with the BIOS, but with no effects.

Thanks

---

### Post by robtygart on 2012-10-07
The brown one is AGP not PCI

---

### Post by robtygart on 2012-10-07
[IMG]http://www.gamereplays.org/community/uploads/post-48468-1218710992.jpg[/IMG]

---

### Post by TheFu on 2012-10-07
Did you check that the BIOS is set to use the built-in GPU and not some external one?
It if also very possible that the built-in GPU has failed, so only using an external one will be possible, but if you are seeing the BIOS screen, that probably isn't the issue.

The MB specs don't say anything about AGP.

[LIST=1]
[*]1 x AMR(Audio Modem Riser) slot
[*]3 x PCI slots support 33Mhz & PCI 2.2 compliant
[/LIST]

---

