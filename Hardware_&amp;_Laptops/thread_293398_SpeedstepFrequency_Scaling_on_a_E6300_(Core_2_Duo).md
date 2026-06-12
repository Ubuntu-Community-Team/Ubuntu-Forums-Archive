---
title: "Speedstep/Frequency Scaling on a E6300 (Core 2 Duo)"
date: 2006-11-05
forum: Hardware &amp; Laptops
---

### Post by keltren on 2006-11-05
I recently got myself a Core 2 Duo E6300 (1.86 Ghz), frequency scaling seems to work but it only offers 2 speeds, 1.86 Ghz and 1.6 Ghz. Is the cpu only capable of running at these 2 speeds? Seems a bit pointless to only be able to reduce the frequency by so little...or are the drivers for this cpu just not completely ready yet?

Running "cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies"
returns:
1862000 1862000 1862000 1862000 1862000 1862000 1862000 1862000 1862000 1596000 

At 1.6 Ghz the cpu is still running fairly hot (52c idle,stock cooler, no case fans) I'll probably need to add either a case fan or a better cpu fan but first I'd like to know if there's a way to make the cpu run at a lower speed and thus cooler(and based on that I'll then see what cooling solution I'll go for exactly)

Does anyone know what speeds this cpu is capable of running at? Or can anyone test under windows at what speeds it's capable of running? (haven't got any windows myself so I can't test...)

---

### Post by JayTee on 2006-11-05
I'd go to [www.intel.com](www.intel.com) and click on their Support menu. Here's a link for your particular CPU specs. 

[http://processorfinder.intel.com/details.aspx?sSpec=SL9SA#](http://processorfinder.intel.com/details.aspx?sSpec=SL9SA#)

 The nominal temp is 61.4C so I wouldn't worry about the temp. My Pentium D likes to run hot so I installed a better CPU heatsink/fan unit. My Pentium D only has two cpu scaling modes, 2.4GHZ and 3.2 GHZ and I suspect Intel has done that for most of their newer desktop lines. The laptop versions of the chips may offer more scaling options.

---

### Post by keltren on 2006-11-05
Thanks for the link but I've already searched the intel site from top to bottom and wasn't able to find any info there. 

From what I understand 61.4c is the max tempt that the cpu should be? The reason I'm a bit worried is that under load it easily hits around 58c...and that's with only one core at full load...

---

### Post by pras2k on 2007-02-25
It is possible to disable the speedstep on the OS level rather than disabling on the bios?

---

