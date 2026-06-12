---
title: "Fast Clock on AMD laptop - Please Read"
date: 2005-12-07
forum: Hardware &amp; Laptops
---

### Post by JackDog on 2005-12-07
<I run breezy, fully updated with the default kernel>

My sempron laptop has a fast clock, as in 2-4 times normal speed (seen via gnome applet). This affects cursors, key repeat and even glxgears.  **While I know that this has been reported before**, there has been no good solution for general Ubuntu-AMD-Laptop users. Disabling APIC or using the notsc kernel option makes most laptop systems unusable in many ways and is thus simply not an option. 

I did not experience this with SUSE10 which is 2.6.13 based. Are there any plans to update the kernel via a breezy update, or should I just consider installing dapper? In my mind this would warrant an update to breezy since it affects nearly every AMD laptop. I dont even know if this is the problem, but it certainly did work.  Most of what I have seen in these forums are work arounds (for specific laptops), not fixes. 

I can easily recompile a newer kernel but I want to make sure I do things the Ubuntu way. One of the things I like about this platform is its easy to maintain. By building and using my own kernel, I am afraid that will no longer be the case. 

Any help would be greatly appreciated.

By the way, this is not 64b install or even a 64b processor.

---

### Post by firetux on 2005-12-07
This helped on my acer 5024WlMi laptop (turion):

add "no_timer_check" and "noapic" (without the ") to /boot/grub/menu.lst after "ro quiet splash"

This fixed my clock (that was running twice as fast) and the battery applet in the gnome dock.

---

