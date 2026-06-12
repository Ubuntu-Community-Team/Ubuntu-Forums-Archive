---
title: "mediocre perfomance with linux"
date: 2008-10-28
forum: General Help
---

### Post by ambush_xx on 2008-10-28
I've been using various linux distros(including all the ubuntu releases form 7.04) for about a year and a half.
Some of the distros i've tried are ubuntu knoppix pclos and red hat.
All the distros i tried were a bit sluggish(enough to be a bother).

My pc is a P4 1.6 Gh with 512 MB ram
and i have a nvidia 5200, for which i hve tried multiple drivers.

The reccomended requirement of ubuntu is 1.2 gh and ive read testimonials from people who say they run ubuntu on sysetms lopwer than that specs with good performance. But my performance have been mediocre( even with Xfce/kde.)
Some of the performance problems i face are; webpges are sluggish to scroll, images take time to load, music played in the back ground skips when i open a file or open a new tab in FF, its slow in switching tabs in FF, flash perfomance is awful.


I've seen linux run very well on other PCs.although they all had better specs. Is ubuntu supposed to run below par with XP on my specs(i wouldnt think so)
What could be the problem with mine. I would suspect the Gfx card but i have not heard anyone having trouble with it.

P.S
I have done all the performance tweaks and the system runs XP quite flawlessly.

---

### Post by jespdj on 2008-10-28
I would not expect Ubuntu (or other Linux distros) to run slow on a computer with an 1.6 GHz P4 and 512 MB RAM. It's certainly not normal that it feels more sluggish than Windows XP.

You probably have some hardware component which causes trouble, but it's hard to tell what it is. Try disconnecting as many external devices as possible and then boot Ubuntu, and see if it runs faster.

Type the command **dmesg** in a terminal, this will print all the log messages of the Linux kernel, and see if there are errors or warning messages or anything else that looks strange.

---

### Post by ambush_xx on 2008-10-29
> The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[   25.342624] * this clock source is slow. If you are sure your timer does not have this bug, please use "acpi_pm_good" to disable the workaround

Found this in dmesg

---

### Post by ambush_xx on 2010-01-15
UPdate. I just install Ubuntu on my laptop, which is also a 1.6 Ghz/512MB. And the performance on it is quite satisfactory. But on my desktop the performance is still very bad. From reading amny forum post i have found that many people are facing similar problems with computers that are spec'ed similar to mine. I must be a hardware problem. 
I wish there were some diagnostic tool native in ubuntu that would help with such situations.

---

### Post by kelvin spratt on 2010-01-15
Your down fall may be your graphics card as its not supported by Nvidia any more try to get a card min nvidia 6200 as they a supported I think you will find a difference. Or try a Distro like Zenwalk.

---

