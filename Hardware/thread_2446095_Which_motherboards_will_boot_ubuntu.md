---
title: "Which motherboards will boot ubuntu"
date: 2020-06-24
forum: Hardware
---

### Post by jcdenton1995 on 2020-06-24
Hello all,

Can anyone vouch for a motherboard with an AMD X570 chipset that works fine with Ubuntu?

It would be a helpful starting point for selecting a board for my PC build. 

Also let me know if you have any experience with B450 / X470 boards as I might be tempted to go for one of those if compatibility issues made it necessary.

Thanks!

---

### Post by TheFu on 2020-06-24
I wouldn't "vouch" for the B450 that I've been running Ubuntu on for 18 months.  There are hundreds of settings that have to be configured correctly.  Lots of compatible and incompatible HW makes vouching for anything difficult.

Pretty much any reputable brand of B450 or X470 or X370 board will work fine.  Don't know about x570 - haven't been in the market.  Pay attention to the MB vendors who refuse to suppose Linux in any way. Avoid those.

---

### Post by rbmorse on 2020-06-24
I'm running Ubuntu Focal on an ASUS Crosshair VIII Hero with a 3700x.  No issues not related to the Nvidia 2080 GPU and that there's no driver for the 2.5GHz LAN adapter which I don't use anyway.  

YMMV.

---

### Post by TheFu on 2020-06-25
> **rbmorse said:**
> I'm running Ubuntu Focal on an ASUS Crosshair VIII Hero with a 3700x.  No issues not related to the Nvidia 2080 GPU and that there's no driver for the 2.5GHz LAN adapter which I don't use anyway.  

YMMV.

Excellent point about the NIC.  I specifically select only motherboards that come with Intel PRO/1000 NICs. No realtek. No funky brands I've never heard about.  My B450 has an Intel I211 Gigabit NIC. By filtering out non-Intel NICs, the choices drop and so does the issues with networking.  I was tired of being disappointed/burned by non-Intel NICs. Just look in these forums for problems related to non-working wired ethernet connections that go back to realtek drivers.  There are a bunch.  For a long time, may still be true, BSD didn't have support for Realtek, but Intel has been providing drivers for 25+ yrs.

---

### Post by Yellow Pasque on 2020-06-25
> **TheFu said:**
> I wouldn't "vouch" for the B450 that I've been running Ubuntu on for 18 months.
And which mobo would that be?

> Pay attention to the MB vendors who refuse to support Linux in any way. Avoid those.
There are only a handful of major mobo vendors. So maybe you could be more specific?
That said, I've never needed Linux-specific support from a mobo vendor.

---

### Post by TheFu on 2020-06-25
```
           Desktop: Openbox 3.6.1 Distro: Ubuntu **16.04** xenial
Machine:   Mobo: **ASUSTeK model: ROG STRIX B450-F GAMING v: Rev 1.xx**
CPU:       Hexa core AMD **Ryzen 5 2600** Six-Core (-HT-MCP-)
           speed/max: 1535/3400 MHz
Graphics:  Card: NVIDIA GP108 [**GeForce GT 1030**]
           Resolution: 1920x1200@59.95hz
           GLX Renderer: GeForce GT 1030/PCIe/SSE2
           GLX Version: 4.6.0 NVIDIA 430.64
Network:   Card: **Intel I211 Gigabit** Network Connection driver: igb
Info:      Processes: 528 Uptime: 4 days Memory: 15625.8/32160.7MB

```

I don't game. There are some odd-to-me limitations around storage with that MB. It has 2 NVMe m.2 slots. If either are used in SATA mode, then SATA 5/6 are lost. At the time, NVMe storage was about 2x the cost of SATA SSDs.

That Asus is easy to install firmware updates without Windows. The BIOS has that capability built-in either directly over the internet or from USB storage.  I'm also running "unapproved RAM" at 3200Mhz on the system. That was a problem with early Ryzen releases, but by the time the 2nd-gen Ryzens were out, it was almost completely a non-issue. Just doubled the RAM last month as my use was bumping into the 16G it has previously.

> There are only a handful of major mobo vendors. So maybe you could be more specific?
That said, I've never needed Linux-specific support from a mobo vendor. 

I'm not in the market and things change.  I've been burned by a few vendors who only provided Windows firmware drivers, updates, support. When a MB has a fault and the vendor refuses to help just because you aren't running Windows - well - I don't want to give them any money, ever again.  

When I'm looking for hardware, I'll seek out vendors who support BSD.  To me, even if I don't run BSD on the hardware, it tells me much about their Unix support team. Hardware that works well with BSD usually is absolutely fantastic with Linux.

---

### Post by Yellow Pasque on 2020-06-25
> **TheFu said:**
> There are some odd-to-me limitations around storage with that MB. It has 2 NVMe m.2 slots. If either are used in SATA mode, then SATA 5/6 are lost.

My Gigabyte/Aorus B450 does this too. I know some MSI boards that do the same thing. That doesn't really have anything to do with Ubuntu/Linux though.

> I've been burned by a few vendors who only provided Windows firmware drivers, updates, support. 
What else do you need except BIOS updates? And nowadays, they're mainly done in the BIOS.

> When I'm looking for hardware, I'll seek out vendors who support BSD.
Care to name them? Does Asus support BSD?

---

### Post by TheFu on 2020-06-25
It is true. Some things that feel like "gotchas" aren't important to the OS.  I had plans for 8 storage devices. 7 SATA (1 m.2) and 1 NVMe (m.2). Got to spend more cash on a SATA addon card that doesn't support booting.  I drew the line there - MB, not addon card - when mentioning issues.

Over the decades, I've had lots of issues over minor things. That has taught me many lessons. When I was younger, I ignored the old guys claims because spending $5 less was absolutely critical in my decision.  Remember WinModems?  Remember the Logitech C-series mice that all stopped working?  Remember the years that Seagate lied about problems with their 600GB - 2TB drives?  I do.  I avoided anything from Logitech for about 15 yrs. I won't touch anything new from Seagate when I used to seek them out.  I have some really old Seagate 300-320GB disks here with 12+ yrs of continuous use. Don't get me started about PC HP stuff.

> Care to name them? Does Asus support BSD? 

I don't have the desire to volunteer the 2-weeks of research to nail that down. Feel free if you do.  Start with popular BSD distro lists of hardware - FreeNAS or pfSense.  If you are building a VM host, it doesn't hurt to look at the VMware ESXi "whitebox" list. VMware is really picky, so doing 10 minutes of searching this week may be able to prevent problems in 3 yrs when the OP decides to run that solution and cannot due to very popular HW not working.  Out of 5 systems here in 2010, only 1 could boot ESXi. VMware has only become pickier.

Best to NOT lock yourself out of future desires by a short-term choice today if that can be easily avoided.  Of course, all these things are trade-offs in time, money, effort.  If $20 more for a MB gets me Intel NICs, I've decided that  is worth it.  If the price isn't any different between two MBs and 1 supports ESXi and the other one doesn't - why would I pick the one that doesn't?

And that's my main point here. Seek out the most compatible stuff you can find, but is isn't "Asus always works." We have to look at the different models and compatible components. Most vendors pay attention to the 93% of the world using Windows for desktop systems, as they should. Those who pay attention to other OSes and actually provide support should be on our short list.

---

### Post by Yellow Pasque on 2020-06-25
> **TheFu said:**
> I avoided anything from Logitech for about 15 yrs. I won't touch anything new from Seagate when I used to seek them out ... 
Seek out the most compatible stuff you can find, but is isn't "Asus always works." We have to look at the different models and compatible components. 

Those two statements are completely contradictory. On the one hand, you are ignoring brand name, and on the other, you are regarding it as long-term gospel.

> When I'm looking for hardware, I'll seek out vendors who support BSD ... I don't have the desire to volunteer the 2-weeks of research to nail that down.

So you purchased a mobo recently and didn't follow your own advice? You can't even advise for/against the mobo you're currently using?
FWIW, I recommend the Gigabyte/Aorus B450 Wifi Pro I have. The only thing that doesn't seem to work is the mobo sensor chip (though you can still see CPU temp and NVMe from other sensors).

> Start with popular BSD distro lists of hardware - FreeNAS or pfSense.

I was asking if Asus officially supported BSD/Linux; not the other way around. I mean, if someone contacted Asus about an issue with a bug in their ACPI that only occurs on Linux, would they forward it to their BIOS engineers or would they just say, "We don't support Linux. Bye."? That seems like a fairly simple question that does not require two weeks of research. And I would think that somebody stressing the importance of a vendor's Linux support would know the answer to that question when s/he just bought a mobo for that vendor..

---

### Post by rbmorse on 2020-06-25
>  [COLOR=#000000]Excellent point about the NIC. I specifically select only motherboards that come with Intel PRO/1000 NICs. 
[/COLOR]
Yes...I made sure the ASUS Crosshair had Intel ethernet (I211) in addition to the Realtek before buying.  If ASUS had offered only the Realtek NIC I would have passed on the Crosshair Hero for all reasons you mentioned.

---

### Post by TheFu on 2020-06-25
Where someone sees contradiction, I see grey areas.   Asus has supported RHEL and Ubuntu for some time - for specific hardware.  They have Linux drivers posted.  But it isn't a yes/no answer. I have been inexact with the term "support" in this thread.  Sometimes it means etched in official policy for specific hardware and other times it means - we got this working with zero or minimal effort.  Grey areas.

---

### Post by jcdenton1995 on 2020-06-25
> **TheFu said:**
> Excellent point about the NIC.  I specifically select only motherboards that come with Intel PRO/1000 NICs. No realtek. No funky brands I've never heard about.

I will bear this in mind as I do intend to use Ethernet at some point.

On another note, what was the situation with Seagate drives? I have a Seagate SSD that's probably circa 2015 that has a lot of old photos on there (I know it's daft not to have a backup) is there some specific issue with them?

---

### Post by rbmorse on 2020-06-25
Probably best to start a new thread on this; there are people here who don't care about motherboards but pay very, very close attention to storage devices.

---

### Post by Yellow Pasque on 2020-06-25
> **rbmorse said:**
> Probably best to start a new thread on this

Why? It would probably be best to ask a more specific question (i.e. edit the thread title). Because "Which motherboards will boot Ubuntu?" has a ton of answers. "Which X570 Mobo Works Flawlessly?" seems more like what OP is asking.

---

### Post by Perfect Storm on 2020-06-25
ASUS PRIME X370-A works out of the box.

---

### Post by TheFu on 2020-06-25
> **jcdenton1995 said:**
> I will bear this in mind as I do intend to use Ethernet at some point.

On another note, what was the situation with Seagate drives? I have a Seagate SSD that's probably circa 2015 that has a lot of old photos on there (I know it's daft not to have a backup) is there some specific issue with them?

i know nothing good or bad about SSDs with Seagate branding.  Sorry. 
i believe Samsung is the safe bet for SSDs, but regardless, there is no excuse for not having backups when a WD 2TB usb3 external disk is under $50.  it is actually hard to find smaller sized disks for less.  The 2.5 inch external drives will be slower than 3.5 inch with external power.  The external power is important for speed.  Or get a $20 USB3 dock and an internal 2.5 or 3.5 inch drive.  With a dock, we have unlimited storage as needed using bare drives. That can be really handy.

---

### Post by jcdenton1995 on 2020-06-26
> **Yellow Pasque said:**
> Why? It would probably be best to ask a more specific question (i.e. edit the thread title). Because "Which motherboards will boot Ubuntu?" has a ton of answers. "Which X570 Mobo Works Flawlessly?" seems more like what OP is asking.

No I was literally under the impression that certain motherboards just didn't work at all with Linux and would refuse to boot, but between this thread and one I posted on Reddit, It seems that pretty much any X570 motherboard will boot Linux, but some will have embedded hardware that may not be fully supported, with ITE Super I/O chips and some Ethernet controllers being the most problematic.

---

### Post by Yellow Pasque on 2020-06-26
> It seems that pretty much any X570 motherboard will boot Linux, but some will have embedded hardware that may not be fully supported, with ITE Super I/O chips and some Ethernet controllers being the most problematic. 

Yeah, that seems like a good takeaway. FWIW, I never had issues with Realtek 8111 series NICs, but I've seen reports of 8168/8169 that would discourage me from those.

---

### Post by Paulgirardin on 2020-06-30
I rebuilt my system with a Asus Prime B450M-A , AMD® Ryzen 5 2600 six-core processor  6 months ago .It works great.
When I did my research prior to purchase, I noted that there was a problem with early versions of some BIOS on various mobos.
That could be corrected with a BIOS update.

---

### Post by leowu12 on 2020-07-01
I u need more info. U can read more about motherboards [here]("https://www.bestadvisor.com/best-motherboards")

---

### Post by jcdenton1995 on 2020-07-01
Thanks, it's really interesting that from what I've seen online, it's really hit and miss weather a build has issues or not as there seem to be lot's of people reporting problems with various BIOS, motherboards and hardware that other people say works fine for them. Probably just because of the almost unlimited number of different hardware / software combos

---

