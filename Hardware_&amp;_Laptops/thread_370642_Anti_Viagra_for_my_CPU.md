---
title: "Anti Viagra for my CPU"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by bodycoach2 on 2007-02-26
I had Dapper on my HP Pavilion ze5200 before. I had it doing everything I needed, even frequency scaling. I'd followed a post on the Ubuntu Document Storage Facility site (which doesn't seem to be working at the moment), and got the CPU to throttle when I needed it. My battery is almost shot, but I could get 30 minutes more out of it with the cpu set to 1.4 GHz instead of the normal 2.8.

I recently upgraded to Edgy Eft, and I can't the the cpu to do the frequency scaling again. I followed thread on this [HOW TO GUIDE for frequency scaling]("http://ubuntuforums.org/showthread.php?t=248867&highlight=frequency+scaling"), but once I get to step three, I can't sudo modprobe anything. It doesn't recognize centrino or acpi setting. 

There are times when I just don't need to 'get it up' with this laptop. Help me get my cpu frequency to scale. Please? Someone?

---

### Post by bodycoach2 on 2007-02-26
Please? Someone help me on this. Someone? Anyone?

The power my computer is producing is getting to me. I feel the urge to wear dark clothes, and call myself "Darth" something. I even started a plan to take over Sealand, and declare myself Emperor. 

To quote Jim Carey in ***The Mask***, "Somebody stop me!"

---

### Post by bodycoach2 on 2007-02-27
The Ubuntu Document Storage Facility is back up. I found the 'missing link' in the instructions:

> sudo modprobe p4_clockmod

Frequency scaling is working. Sealand is safe. For now.

---

