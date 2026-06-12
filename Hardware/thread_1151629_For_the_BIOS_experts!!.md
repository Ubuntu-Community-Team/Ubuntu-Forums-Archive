---
title: "For the BIOS experts!!"
date: 2009-05-07
forum: Hardware
---

### Post by jocheem67 on 2009-05-07
Hi all, here's one for the BIOS-guru's:

I just bought me some new hardware: an asus M4A78T-E board,a AMD Phenom X3,  two strips of OCZ mem. ( 4 GB ), and a new 1TB harddrive...
All works pretty well ( I'm surprised Ubuntu all reads and loads well )..

Well, I've been playing around with the BIOS-settings a bit ( am not a Newbie regarding this stuff ). Here's a couple of questions...

What about Plug 'n Play OS, is it smart to enable/disable this??
Does Ubuntu know about all hardware to detect and load/not load or let the BIOS decide?

What about AHCI, is there an advantage over IDE ??

Is it normal, that the BIOS only reports 3,8 GB of mem. when 4GB is installed?
Of course I'm running 64bit Ubuntu...

---

### Post by Barry Carroll on 2009-05-07
I have PnP OS set to yes on my 64-bit Ubuntu machine and it works.  I haven't tried PnP OS set to No and I'm not sure if I want to seeing as everything works so well.

AHCI mode gives you some features which might enhance performance with your SATA drives.  I think that the performance might be more for server type tasks but you can google for "AHCI vs IDE mode"and there are a few sites that have articles on it such as:

[http://expertester.wordpress.com/2008/07/24/ahci-vs-ide-%E2%80%93-benchmark-advantage/](http://expertester.wordpress.com/2008/07/24/ahci-vs-ide-%E2%80%93-benchmark-advantage/)

The graphics hardware on your board has shared memory and any assigned to the graphics is taken away from the displayed amount of RAM.

---

### Post by HyRax on 2009-05-07
> **jocheem67 said:**
> 
What about Plug 'n Play OS, is it smart to enable/disable this??
Does Ubuntu know about all hardware to detect and load/not load or let the BIOS decide?

Ubuntu is a "Plug'n'Play" OS, so you can enable this if you like, but it's mostly a Windows setting. Linux doesn't really care either way.

> **jocheem67 said:**
> 
What about AHCI, is there an advantage over IDE ??

AHCI is a SATA specification - it does not have anything to do with IDE.

> **jocheem67 said:**
> 
Is it normal, that the BIOS only reports 3,8 GB of mem. when 4GB is installed?
Of course I'm running 64bit Ubuntu...

When someone sells you 4GB of RAM, they are selling you 4000MB of storage space. However computers can only count in base 2 (binary) and 4GB in binary expressed as a decimal is 4096MB (1GB = 1024MB, not 1000MB). 1024 divides into 4000 roughly 3.8 times, hence the system reports 3.8GB of RAM.

---

### Post by jocheem67 on 2009-05-07
Thanks guys..

The IDE vs. AHCI issue I adressed 'cause it's just a choice within the BIOS.
Surely it's different things/ways..

The mem. issue is clear now.

Did you guys do some tweaking towards your BIOS, to speed up loading times, or improve compatibility??

---

### Post by Barry Carroll on 2009-05-07
> **jocheem67 said:**
> Thanks guys..

The IDE vs. AHCI issue I adressed 'cause it's just a choice within the BIOS.
Surely it's different things/ways..

The mem. issue is clear now.

Did you guys do some tweaking towards your BIOS, to speed up loading times, or improve compatibility??

Yes, the *terms *relate to different things, but when you have an option of "AHCI/IDE" that means you can run your SATA drives in the AHCI mode *or* a legacy mode without NCQ and the rest. 

Most BIOS vendors name this "IDE" or "LEGACY" or something along those lines.

---

