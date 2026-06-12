---
title: "Any way to monitor a second battery in Gnome?"
date: 2005-08-04
forum: Hardware &amp; Laptops
---

### Post by Chuckaluphagus on 2005-08-04
I have an Asus M3Np notebook and often swap out my CD-ROM drive for a secondary battery, especially when travelling.  While I can check the status of either battery in a terminal window by typing "cat /proc/acpi/battery/.../state", no information for the second battery shows up in the Battery Monitor applet in the panel in Gnome.  

Is there any way to set the Battery Monitor applet to display information for both batteries when both are present in the system, or is there an alternative battery monitor applet that will show that information and is available somewhere for download?

Thanks for any help.

---

### Post by mjwood0 on 2005-08-04
I'm no expert, but I often run two batteries in my Dell Inspiron 8100.  

I was under the impression that the Gnome applet showed the overall battery status of the system.  For instance, if I start the system with two partially full batteries, I see something like 74% remaining.  If I remove one of the batteries, this number changes almost instantly and so does the displayed time remaining. 

I've often wondered if it ere possible to display seperate monitors for each battery so I could tell which one was the full one, etc... but have yet to find a way.

---

### Post by Chuckaluphagus on 2005-08-04
[QUOTE=mjwood0]I'm no expert, but I often run two batteries in my Dell Inspiron 8100.  

I was under the impression that the Gnome applet showed the overall battery status of the system.  For instance, if I start the system with two partially full batteries, I see something like 74% remaining.  If I remove one of the batteries, this number changes almost instantly and so does the displayed time remaining. 

I've often wondered if it ere possible to display seperate monitors for each battery so I could tell which one was the full one, etc... but have yet to find a way.[/QUOTE]

I'm not sure that the battery applet monitors the cumulative battery life when both batteries are in the system; at least on my notebook, it doesn't appear to significantly change the expected running time on battery when I insert the secondary battery, even though actual running time nearly doubles.  It appears to still only be showing the battery life of the primary battery and making its estimation based on that. (I could be wrong about this last part, I have yet to do an actual run-down test under Ubuntu or be in a situation where I've managed to completely or nearly drain both batteries.)

As I said, the information about the status of the second battery is all available under /proc/acpi/battery<etc>, so it should be possible to configure the battery applet or a different applet to show output  for both batteries individually as well.  I haven't been able to find one, though (in Linux at least; it's standard in Windows 2000), and I don't know the first thing that would be necessary to create such an applet myself.

---

### Post by varunus on 2005-08-04
I think the upcoming GNOME power manager will be much better able to deal with situations like multiple batteries.  It's going to be based on HAL.  That said, for now, it wouldn't be very hard at all to write a simple panel applet that displayed each percentage individually; if you want me to write one, drop me a PM, I could have it done by this weekend.

---

