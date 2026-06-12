---
title: "Compiz Help"
date: 2009-04-16
forum: Hardware
---

### Post by lsproductions on 2009-04-16
Hey Guys. 

I was Wondering If You Could Help Me! I want Compiz On My Laptop And I Have done a test to see if it will work. Here Are The results -


Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 


Any Ideas On How I Can Fix This! Please!!

Thanks

Lewis

---

### Post by ajmctaggart on 2009-04-16
Have you tried to go to system>Admin>Hardware Drivers and seen if you can enable a proprietary driver that would help?  There are usually 2 drivers (at least w/ my ATI) and if I mistakenly enable the wrong one, compiz wont work either...

---

### Post by lsproductions on 2009-04-16
I went to Hardware Drivers and theres nothing there. The Box is empty!

"No proprietary drivers are in use on this system"

---

### Post by ajmctaggart on 2009-04-17
Okay, a couple of things...

If you're trying to get the long-term support out of 8.04...you can see if this will work for you
[http://ubuntuforums.org/showthread.php?t=974245]("http://ubuntuforums.org/showthread.php?t=974245")

Or

Im pretty sure by upgrading to Ibex (8.10)or waiting a couple more days and going straight to Jaunty 9.04, this problem may already be fixed.

I bought a cheap Dell off Craigslist to run some Microsoft stuff on for school, and also threw a Ubuntu partition on there...I've only used Ibex or Jaunty on the system and haven't had the problem you're describing, but have a very similar ATI card in there...So although my setup is nowhere near exact, I feel your problem may be solved by upgrading because of my experiences...

I hope this information is somewhat helpful, you should proceed with the link above before upgrading your system (If Hardy Heron satisfies you in other regards, that is...)with every release there will be some issues initially, so you'll have to decide if Compiz is worth going forward an possibly losing the stability of 8.04 LTS

Finally, I just found this...
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English")

I think these option are in the order of safest to crippling, in other words, ATI driver directly from site may mess something else up, so try the top 2 steps first!

Good Luck!

---

