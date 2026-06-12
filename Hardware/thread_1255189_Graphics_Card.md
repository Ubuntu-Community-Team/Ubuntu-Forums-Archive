---
title: "Graphics Card"
date: 2009-09-01
forum: Hardware
---

### Post by RumboPumbo on 2009-09-01
I am building a new desktop computer and i am wanting a graphics card that has a memory size of 512mb, i am using a site which shows the compatability of all the things put together. Anyway i have got the new Ubuntu coming and i was thinking about the compatability with linux, anyway this is the product number of the graphics card:
471846200-9900
So if anyone could tell me wether this graphics card is ok or if I would need to get some drivers for it, thanks in advance.

---

### Post by karamu on 2009-09-01
It's an Nvidia so should be OK- I don't know this particular card but I used to use an Nvidia in my old machine.

After you install Ubuntu you will need to select the hardware drivers option from the admin menu and it will check for proprietary drivers (you need to be online)- then you will need to authorise the use of non free drivers.

it is a pretty painless process- not like on Windows when you need to get the drivers yourself!

---

### Post by cascade9 on 2009-09-01
471846200-9900 = Gainward GeForce 8400GS 512MB. 

If your after 512MB for some particular reason, you might want to think about that card. Sure, it will run a desktop fine. But for some things, its not much good- slow core, 64bit bus, etc..most '512MB cards' would be much faster than a 8400GS. It wasnt even meant to be a 512MB card anyway-

[http://www.nvidia.com/object/geforce_8400.html](http://www.nvidia.com/object/geforce_8400.html)

---

### Post by RumboPumbo on 2009-09-01
ok then, thanks for the help. So most Nividas should be ok? and by the looks of the driver search it seems easier

---

### Post by gradinaruvasile on 2009-09-01
If u like AMD processors u might as well buy a mobo with integrated graphics card such as ASUS M3N78-VM or the like... Much cheaper and works with ubuntu out of the box...

---

### Post by RumboPumbo on 2009-09-01
> **gradinaruvasile said:**
> If u like AMD processors u might as well buy a mobo with integrated graphics card such as ASUS M3N78-VM or the like... Much cheaper and works with ubuntu out of the box...

Good idea but got practically the whole computer built already, so instead i found a different graphics card i could have:
GM9400GN2E50X-SB
The reason for the specific of the 512mb is as it is to be able to play a certain game.

Thanks

---

### Post by the_dark_light on 2009-09-01
Fortunately Ubuntu makes it really easy to use NVIDIAs Binary driver (A must for gaming/compiz) through the restricted drivers tool.

The big question is what do you want to use the card for?  Is it just as a VGA card?  Do you want to use Compiz? Do you want to play games? Are you dual booting with windows and going to be using modern games?

If you are looking for mainly 2d usage and Compiz then you should be okay with a 9400 (Personally I see no reason to get a card of an earlier generation - unless you are looking to a hihg end one like an 8800.  I hear previous gen high end works better than current generation mid range)

I've seen cards like: Asus 9400GT 512MB DDR2 VGA DVI HDMI PCI-E on suppliers like ebuyer for around £30

I'm recommending NVIDIA as that's the type of card I've had the most experience with.  Anyone here use ATI and can advise on how easy they are to work with?

---

### Post by RumboPumbo on 2009-09-01
with the card i am going to be using for a fairly modern game and may have to be dual booting with windows if i cannot get everything wanted from Ubuntu.

Also some older games like Sims 2 i wouldnt mind on there, other than that it is for internet usage

---

### Post by hockeytux on 2009-09-01
Ive got an ATI 2100 and it doesnt work well. Compiz yes, but no cube and very, very slow 3D graphics.

Unless theres some major work on ATI drivers for Linux my next graphics card will be a Nvidia.

---

### Post by gordintoronto on 2009-09-01
> **RumboPumbo said:**
> Good idea but got practically the whole computer built already, so instead i found a different graphics card i could have:
GM9400GN2E50X-SB
The reason for the specific of the 512mb is as it is to be able to play a certain game.

Thanks

The first video card was AGP, this one is PCI.  If you are building a new computer, you probably need a PCI card.

Within the last month I built a new computer.  I used a 9400GT video card, and I'm quite happy with it.  Windows' "experience index" (benchmark) is not impressed, though.

---

### Post by cascade9 on 2009-09-01
> **gordintoronto said:**
> The first video card was AGP, this one is PCI.  If you are building a new computer, you probably need a PCI card.

Within the last month I built a new computer.  I used a 9400GT video card, and I'm quite happy with it.  Windows' "experience index" (benchmark) is not impressed, though.

Nah, they were both PCI-E. 

RumboPumbo- the GM9400GN2E50X-SB (Geforce 9500GT) is a bit faster than the 8400GS. Considering that even graphic intensive games like crysis have a 256MB 'minimum' requirement, I dont know if low end cards like 8400/8500s and 9400 series nVidia cards are going to get you the experience you want.  It really depends on what game you want to play.

---

### Post by RumboPumbo on 2009-09-01
ok thanks, the main thing i wanted to know from this overall was whether it was able to be sued with linux

---

### Post by karamu on 2009-09-02
> **gradinaruvasile said:**
> If u like AMD processors u might as well buy a mobo with integrated graphics card such as ASUS M3N78-VM or the like... Much cheaper and works with ubuntu out of the box...

I had an ASUS MOBO with integrated ATI graphics (Radeon Express) and it was a major pain getting the drivers to work- from what I have read online it seems that Nvidia is the much better choice to run with Linux.

---

### Post by cascade9 on 2009-09-02
> **RumboPumbo said:**
> ok thanks, the main thing i wanted to know from this overall was whether it was able to be sued with linux

Yes, they will work. I dont think that there are _any_ nvidia cards that dont have some sort of linux driver to be honest.

---

