---
title: "Dell Latitude CPi D300XT"
date: 2005-11-11
forum: Hardware &amp; Laptops
---

### Post by E-werd on 2005-11-11
I got a laptop from a friend of my father and I am trying to get Ubuntu (specifically Hoary as I haven't gotten a Breezy CD yet) and am unable to. 

My main problem is that I cannot get through the installation without the screen changing colors and completely halting.  Sometimes it will halt before I get it to the install dialog.

I have reseated the CPU, verified that the hdd is fine and checked the memory.  Now what? :confused:

---

### Post by gmc on 2005-11-12
I've installed Hoary / Breezy onto an old CPI 233XT. Are you passing any parameters to the kernel when you are booting the CD?

I know the CPI 233XT uses a NeoMagic chipset. One problem I discovered was that under Windows98, the screen resolution was 1024x768, however the neofb driver would only allow 800x600. The long and the short of it was had to used the parameter "vga=0x314" (800x600x16).

Give that a try and see if it sorts the problem.

G.

---

### Post by hagis on 2005-11-12
I've installed hoary on my older CPi 366 laptop without any problems but sometimes I need to specify nodma when launching from cd's with other distros. Maybe your problem? May not though. Give it a try.
/Håkan

---

### Post by gmc on 2005-11-12
[QUOTE=hagis]I've installed hoary on my older CPi 366 laptop without any problems but sometimes I need to specify nodma when launching from cd's with other distros. Maybe your problem? May not though. Give it a try.
/Håkan[/QUOTE]

Good point Hagis,

That was one problem I had tring to install Hoary/Breezy on my CPI233XT. During the point where it tries to load the ide-generic driver, I found that I had to switch (f2) to the console and enter 'echo "using_dma:1" > /proc/ide/hdc/settings' to turn the DMA back on, before the CDROM would continue reading and installing.

Thanks for that reminder.

G.

P.S. Are you Scottish?

---

### Post by E-werd on 2005-11-12
Actually, this isn't just Ubuntu specific, it is anything.  I tries XP a few times and Ubuntu a few more times... tried swapping out memory and all.

Argh.  Ideas?

---

### Post by E-werd on 2005-11-13
I think I have resolved this to be a cooling problem... what can I do about this?

---

### Post by gmc on 2005-11-15
[QUOTE=E-werd]I think I have resolved this to be a cooling problem... what can I do about this?[/QUOTE]

If it's a cooling problem, and the internal fan is broken or just not being activated for some reason. You could try setting the processor speed to it's low speed and see if that helps or get a desk fan and make a paper cone to stick in the side of the laptop and blow air from the desk fan into the cone. (I use this method as the fan on my 233 is broken).

G.

---

### Post by r0ll3r on 2005-11-15
You could also try boot the installer with acpi=off. In my case, my laptop has a terrible ACPI, which reported 4000 celsius degree at start for CPU temperature, so the kernel always shut my machine down. With acpi=off, this is solved. I compiled a kernel for myself, without acpi thermal module. All other acpi modules  remained functional.

---

### Post by Manzabar on 2005-11-15
I also have a Dell Latitude CPi D300XT and originally had similar problems getting the Ubuntu loaded on it.  I found part of the problem was my CD-ROM drive would overheat very quickly, causing the install to fail.  Fortunately, I have a co-worker with the same laptop but a newer CD-ROM and I was able to borrow his drive to do the install.  Later, I found I could complete the install on my laptop with my CD-ROM by leaving the computer off for a couple of days and using the coolest room available to setup the laptop in to run the install.

---

