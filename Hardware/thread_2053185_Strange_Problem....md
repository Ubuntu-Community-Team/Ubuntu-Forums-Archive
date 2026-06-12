---
title: "Strange Problem..."
date: 2012-09-04
forum: Hardware
---

### Post by SaturnsVoid on 2012-09-04
I installed Ubuntu 12.04 on my lenovo Z575 and it was running great, Until i restarted...

After the restart the Laptop would just freeze on the boot screen... It was completely unresponsive. The only way i was able to get it to boot was to go into my BIOS and make the laptop only use my dedicated video card...

My laptops specs:
[LIST]
[*]AMD A6-3420M APU with Radeon(tm) HD Graphics × 4 
[*]6GB DDR3 (1333)
[*]500GB HDD (5400rpm)
[*]AMD Radeon HD 6520G
[/LIST]

The system in running on the 6520G when i want it to run on the APU too save power...

I have installed the drivers for both and re-installed them, but no luck. Any help?

---

### Post by gdea73 on 2012-11-08
I'm still having issues with this laptop on 12.10, but try the "nomodeset" option if you get a purple screen.

Hold shift while booting, select "e", find the "quiet splash" et al., line of the boot command and append "nomodeset" to the end. That's a typical workaround for this issue.

In the meantime I'm still trying to get the proprietary drivers (fglrx) to work on this.

---

