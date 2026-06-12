---
title: "Processor/Graphics Card question"
date: 2013-04-18
forum: Hardware
---

### Post by Nanur on 2013-04-18
Hey everyone.
I was wondering if there is a way that I can allocate  more usage to my graphics card that my processor general uses. In other  words is there a way to make my processor work less, and my graphics  card more?

The reason I am asking this is because Guild Wars 2  runs terrible.. as in 6-11 fps. When I open the System Monitor my CPU  usage goes from the normal 10-20% range to 100%, and stays at 100% while  my graphics card is barely doing anything.
I know that Guild Wars 2  is a CPU-based game, but it would be nice if I could kick that fps up to  a good 20. Also my RAM doesn't exceed 40% usage.

System specs:
CPU: Intel® Pentium(R) D CPU 2.80GHz × 2 (dual core)
RAM: 4GB G.SKILL
GPU: nVidia GeForce 550Ti; 1GB

Note: The WINE versions are up to date.

If there are any questions please ask and I will clarify.

Thanks! 
-Nanur

---

### Post by ahallubuntu on 2013-04-18
~

---

### Post by Nanur on 2013-04-19
Awesome thanks! I will look into upgrading to a Core 2 Duo.

---

### Post by deadflowr on 2013-04-19
You'll need a whole new system, as the core 2 duo processor is incompatible with the netburst architecture of the pentium D.

---

### Post by Yellow Pasque on 2013-04-20
> **deadflowr said:**
> You'll need a whole new system, as the core 2 duo processor is incompatible with the netburst architecture of the pentium D.

That's oversimplified. It depends on the motherboard. Details: [http://en.wikipedia.org/wiki/Intel_Core_%28microarchitecture%29#Motherboard_compatibility](http://en.wikipedia.org/wiki/Intel_Core_%28microarchitecture%29#Motherboard_compatibility)
Basically, if in doubt, check the mobo vendor's page. Also, even if it supports Core 2, you may need to update the BIOS before pulling the old CPU.

---

### Post by ahallubuntu on 2013-04-20
~

---

### Post by Nanur on 2013-04-20
> **deadflowr said:**
> You'll need a whole new system, as the core 2 duo processor is incompatible with the netburst architecture of the pentium D.

Actually, my motherboard is compatible with Core 2 Duo processors. Both are socket type LGA 775.

---

### Post by ahallubuntu on 2013-04-20
~

---

### Post by Nanur on 2013-04-21
> **ahallubuntu said:**
> The fact that your board is socket 775 doesn't mean much.  Does the chipset support a Core 2 CPU?  Does the BIOS have microcode for it?  Is the FSB speed supported?

Your best bet is to look on the motherboard manufacturer's website for a list of supported CPUs for your board.  It would be wise to upgrade your BIOS to latest, if possible, before attempting any CPU upgrades.

If you are able to upgrade to a Core 2, you might wish (if you care about noise) to get a new fan + heat sink as well, because you won't need as hefty of a fan to cool a Core 2 Duo CPU.  Pentium D runs very hot.  A lesser fan would probably run more quietly.


Alright thanks. I will check the motherboard for supported CPUs. Also I'm not sure on how to update/upgrade the BIOS.

---

### Post by ahallubuntu on 2013-04-21
~

---

### Post by Nanur on 2013-04-24
Well yeah, if I was to upgrade my BIOS I would do it in Windows.
I am really having a hard time finding the specs on the motherboard in my system. (Dell XPS 400)

---

### Post by ahallubuntu on 2013-04-24
~

---

### Post by Nanur on 2013-04-24
> **ahallubuntu said:**
> The XPS 400 is basically the same as a Dimension 9100 according to a quick google.

Search for "XPS 400 CPU upgrade" or "Dimension 9100 CPU upgrade" and see what you come up with.  I think you're going to find you can't use a Core 2 Duo however.

I found this list of compatible processors.
[http://ark.intel.com/products/27720/Intel-82945G-Memory-Controller]("http://ark.intel.com/products/27723/Intel-82945P-Memory-Controller#compatibility")
I'm not exactly sure this is the chipset in my motherboard.
Any ideas on how to confirm via a terminal command?
The Core 2 Duo's are on there. But I'm sure I need to update my BIOS, and that may be a chore.

EDIT: The more I search the more I find people saying the Core 2 Duo isn't compatible. I'm not surprised by this, it's more of a let down..

---

### Post by ahallubuntu on 2013-04-24
~

---

### Post by Nanur on 2013-04-24
Yeah, that's what I'm finding..

---

