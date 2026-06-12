---
title: "Is this laptop hardware compatible with Ubuntu?"
date: 2019-12-28
forum: Hardware
---

### Post by muscl3s on 2019-12-28
I'm thinking about purchasing this laptop from Dell:
[https://www.dell.com/en-us/shop/dell-laptops/inspiron-15-5000-laptop/spd/inspiron-15-5585-laptop/nnbuc5am102sAFF?prg=1&VEN1=12578053-4485850-076b8f2a299611ea977ed2e5958396b20INT&AID=4485850&cjevent=07eee861299611ea811700ba0a240610&dgc=CJ&DGSeg=DHS&cid=198375&lid=45846&acd=12309198375458460&VEN3=810805246442050758](https://www.dell.com/en-us/shop/dell-laptops/inspiron-15-5000-laptop/spd/inspiron-15-5585-laptop/nnbuc5am102sAFF?prg=1&VEN1=12578053-4485850-076b8f2a299611ea977ed2e5958396b20INT&AID=4485850&cjevent=07eee861299611ea811700ba0a240610&dgc=CJ&DGSeg=DHS&cid=198375&lid=45846&acd=12309198375458460&VEN3=810805246442050758)

Is all of the hardware compatible with Ubuntu?  I really need to know for sure prior to purchasing.

I already have a super high end desktop using Windows. The laptop purchase is to assist me with learning Linux, web browsing, e-mail, and for light gaming occasionally on less intensive games like DotA 2 on Steam.  Any help would be greatly appreciated.

---

### Post by mörgæs on 2019-12-28
Have you considered installing Ubuntu in a dual boot on the desktop?

---

### Post by Autodave on 2019-12-28
*Generally speaking, *most Dell's have very few issues with Linux since Dell does offer some of their machines with Linux installed instead of Windows.

---

### Post by kurt18947 on 2019-12-28
> **muscl3s said:**
> I'm thinking about purchasing this laptop from Dell:
[https://www.dell.com/en-us/shop/dell-laptops/inspiron-15-5000-laptop/spd/inspiron-15-5585-laptop/nnbuc5am102sAFF?prg=1&VEN1=12578053-4485850-076b8f2a299611ea977ed2e5958396b20INT&AID=4485850&cjevent=07eee861299611ea811700ba0a240610&dgc=CJ&DGSeg=DHS&cid=198375&lid=45846&acd=12309198375458460&VEN3=810805246442050758](https://www.dell.com/en-us/shop/dell-laptops/inspiron-15-5000-laptop/spd/inspiron-15-5585-laptop/nnbuc5am102sAFF?prg=1&VEN1=12578053-4485850-076b8f2a299611ea977ed2e5958396b20INT&AID=4485850&cjevent=07eee861299611ea811700ba0a240610&dgc=CJ&DGSeg=DHS&cid=198375&lid=45846&acd=12309198375458460&VEN3=810805246442050758)

Is all of the hardware compatible with Ubuntu?  I really need to know for sure prior to purchasing.

I already have a super high end desktop using Windows. The laptop purchase is to assist me with learning Linux, web browsing, e-mail, and for light gaming occasionally on less intensive games like DotA 2 on Steam.  Any help would be greatly appreciated.

That's a Ryzen 7 machine using Vega 10 graphics. I think you'd want to use 19.10 on it, 18.04 won't work with Vega graphics. At least my desktop didn't. Dell does sell machines with Linux already installed but I think those are higher end machines. I'll bet the Dell machines with Linux preinstalled are Intel machines.

---

### Post by muscl3s on 2019-12-28
Only the developer edition XPS 3 are sold with Ubuntu pre-installed.  Those machines are Intel with integrated graphics for nearly 1k USD.  The machine I linked is just as good IMO for hardware for a lot less in price.  I don't have any problem using 19.10 but I was hoping someone else was on a system with a similar configuration to confirm it works well.  The wireless card that comes included is also something I'm unsure of for Linux.

---

### Post by CatKiller on 2019-12-28
> **muscl3s said:**
> Only the developer edition XPS 3 are sold with Ubuntu pre-installed.  Those machines are Intel with integrated graphics for nearly 1k USD.  The machine I linked is just as good IMO for hardware for a lot less in price.  I don't have any problem using 19.10 but I was hoping someone else was on a system with a similar configuration to confirm it works well.  The wireless card that comes included is also something I'm unsure of for Linux.

There's actually a bunch of them now, although they did start with the XPS 13. Search for "Project Sputnik." 

For WiFi Intel is generally the best supported on Linux, but the mobile page I get redirected to from your link (I'm using a phone to read the forums) doesn't have that info.

---

### Post by kurt18947 on 2019-12-29
> **CatKiller said:**
> There's actually a bunch of them now, although they did start with the XPS 13. Search for "Project Sputnik." 

For WiFi Intel is generally the best supported on Linux, but the mobile page I get redirected to from your link (I'm using a phone to read the forums) doesn't have that info.

I looked further into that link. It does appear that Intel WiFi is available. I think one may have to select Intel as part of the configuration/purchase process. I don't know if Intel is an extra cost option or not.

---

### Post by muscl3s on 2019-12-29
I verified with a Dell rep that the included wifi card with the laptop I wanted is a Qualcomm:
[https://www.dell.com/support/manuals/us/en/19/inspiron-15-5585-laptop/inspiron_15_5585-setupandspecs/communications?guid=guid-ce7d9f99-1b53-42aa-9c1c-2ae4546ae99b&lang=en-us](https://www.dell.com/support/manuals/us/en/19/inspiron-15-5585-laptop/inspiron_15_5585-setupandspecs/communications?guid=guid-ce7d9f99-1b53-42aa-9c1c-2ae4546ae99b&lang=en-us)

I assume that doesn't work with Ubuntu?

---

### Post by jeremy31 on 2019-12-29
The QCA9377 works in ubuntu

---

### Post by kurt18947 on 2019-12-29
If WiFi is the only concern, would a known-to-work USB WiFi adapter serve at least temporarily?

---

### Post by RobGoss on 2019-12-29
**+1 **Autodave, I have a few dells and have no issues installing Ubuntu on any of my machines

---

### Post by muscl3s on 2020-01-06
I just wanted to give an update that I purchased the laptop I linked in my original post.  I installed 16gb of ram and did a fresh install of Ubuntu.  It's working beautifully without any issues thus far.  Loving this new machine.

---

### Post by kurt18947 on 2020-01-14
Great to hear! Your machine probably uses 'standard' components. Ubuntu doesn't have "it supports even the most uncommon/oddball hardware out there" like Windows does. The upside is that once a piece of hardware is natively supported it's likely to remain supported for quite some time unlike some Windows hardware.

---

### Post by CatKiller on 2020-01-14
> **kurt18947 said:**
> Ubuntu doesn't have "it supports even the most uncommon/oddball hardware out there" like Windows does. 

Windows doesn't have that; Ubuntu does. The **manufacturers** support **Windows**, not the other way round. It's a crucial distinction. Uncommon/oddball hardware gets supported under Linux when someone has the itch to scratch of making it work, unless they're prevented from doing so by the secrecy or obfuscation by the manufacturer.

> The upside is that once a piece of hardware is natively supported it's likely to remain supported for quite some time unlike some Windows hardware.

Agreed.

---

