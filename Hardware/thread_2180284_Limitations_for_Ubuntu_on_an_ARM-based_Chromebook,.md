---
title: "Limitations for Ubuntu on an ARM-based Chromebook, and solutions?"
date: 2013-10-12
forum: Hardware
---

### Post by vuniverse143 on 2013-10-12
Hi guys, I'm thinking of getting a new Chromebook (my sights are right now set on the [HP Chromebook 11]("http://www.google.com/intl/en/chrome/devices/hp-chromebook-11/")) and dualbooting Linux on it for work and study. Thing is, I'm not very familiar with the drawbacks of running Ubuntu on an ARM machine.

Misc info:
[LIST]
[*]CPU: Exynos 5250 GAIA Application Processor
[*]Dualboot solution: Crouton
[/LIST]

I've found that closed-sourced softwares are the primary concern, as the distributors might not be so thoughtful as going the extra mile and providing an ARM-compatible version for their app.

My questions are: **How bad is the situation?** What are some popular apps that you know aren't available? **What are my options? **How do I go about compiling ARM-compatible OSS myself? How about alternative replacements for those apps mentioned before?

Thanks for your time, I'll be doing my own reading in the meanwhile. I have a feeling that this is a topic that's big in its own right, independent of my wish to use a Chromebook.

EDIT: Extra question. If any of you own this Chromebook, do you know if it's possible to swap the internal RAM and SSD for an upgrade? I have a feeling that the SSD might not be the standard 2.5'' form factor, seeing how it only has 16GB.

---

### Post by techzilla2 on 2013-12-31
I purchased the Samsung Series 3, ARM Chromebook, about 6 months ago.   Generally I love it, and would recommend it for someone like myself, but I know it's not for everyone. 

While the ARM instruction set is standardized, the platforms are extremely fragmented.  Getting a distribution installed on a new ARM device, is practically embedded development.  If the particular device is very popular, like the Samsung series 3,this process is much simpler due to ready made instructions. 
  
Basically if you've not done ARM Linux install previously,locate good ready instructions, and verify sure you're comfortable executing those instructions.  I've done multiple ARM installations, and I still wouldn't want to attempt this without some degree of platform documentation.  I can't say offhand what the status is for the HP ARM model, but since each one is different you need to investigate

Second the driver support is generally fairly weak, but may be mitigated with closed drivers.  Unfortunately due to API/ABI changes, I'd expect this to need more footwork than you normally encounter.  Thankfully the basic video stuff has been added to Ubuntu, for the Exynos chipset, and X support shouldn't be too bad.  The touch pad could be different for the HP, so I can't say anything about it specifically.

Software isn't horrible, due to most of it being opensource and available in the repositories.  I personally love Komodo Edit, but they don't make an ARM release.  Otherwise that leaves Flash support, which is how you'd expect... horrible.  You may be able to get the Chromeos version running, but I wasn't able on 13.10, although I still may with some effort.

---

