---
title: "Desktop Won't Power Up"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by rschram on 2007-07-29
I successfully installed Feisty on a Systemax (Tigerdirect.com store brand) P4 on a Foxcomm 661MX motherboard. It works fine and there were no problems in the install. I tried hibernating the desktop from the top (Gnome) desktop panel power icon. Gnome stopped and I got a screenful of output followed by a "kernel panic" error. The display went off and the computer became unresponsive. I powered down the system from the power button. When I tried to power up from the power button, the fans spun for a bit, then cut out. Nothing started up. No lights or any activity on the keyboard, display or anywhere I can see. (No lights on the motherboard when I tried to power up with the case off.

Any help or advice about starting up the computer and/or getting access to the hard drive would be much appreciated.

---

### Post by bwhaley on 2007-07-29
Unfortunately, this sounds like a fairly serious hardware problem, perhaps a bad power supply. You can try removing components one at a time (if any of them are PCI/AGP add on devices), unplugging the cdroms and hard drives, etc to see if it boots up. You might also try removing and reseating the memory modules. It's curious that this happened right as you first hibernated Ubuntu but perhaps it's a coincidence.

---

### Post by rschram on 2007-07-29
Thanks for your reply. Yes, this is a hardware problem. I am a novice at diagnosing and repairing hardware problems like this, but I would like to learn, and everyone's advice is appreciated. As suggested, I unplugged the drives and PCI cards and tried to boot. Nothing. I also reseated the memory and got no result. I then looked up how you should determine whether this is due to a bad motherboard or a bad power supply. I disconnected the main bundle from the psu to the mb and used a bent paperclip to short the green wire to the left black wire. (Being sure to ground myself.) When plugged in, the fan hummed quietly and the power button on the front glowed blue. It stayed on even when I hit the power button. I had to unplug it to shut down the fan. So, does the PSU work? It's a bad MB, right? (Foxconn 661 MX [661M04MX6L])

This isn't strictly relevant to this forum, but I would like to know how to rebuild my desktop. Can anyone suggest what I should do next. From what I see, I have 

* Working peripherals (monitor, keyboard, mouse) 
* Working drives (HD [successfully removed and mounted on a laptop via USB enclosure], CDRW) 
* Working PSU, fans
* Case

But what about the processor? Can it be saved? RAM? Anything else? 

Also, since the HD works and there was no apparent data loss, I was wondering if I could investigate the problem in error logs. Where should I look for an error log of my problem? 

Pointers to online resources about how to learn more would be very helpful. Thanks in advance.

---

