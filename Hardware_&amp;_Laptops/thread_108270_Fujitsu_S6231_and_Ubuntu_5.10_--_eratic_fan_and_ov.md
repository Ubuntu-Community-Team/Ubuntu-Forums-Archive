---
title: "Fujitsu S6231 and Ubuntu 5.10 -- eratic fan and overheating"
date: 2005-12-25
forum: Hardware &amp; Laptops
---

### Post by vanden on 2005-12-25
Hi all,

a few days in to my first use of Linux. Lots I like, but the erratic functioning of the fan on my Fujitsu Lifebook S6231 is freaking me out ](*,)

When I boot plugged into the AC, sometimes the power icon shows me running on AC, sometimes on battery. When it shows on AC, after a while, it will change to showing me running on battery (this while still plugged in).  

Whenever it is shows I'm running on battery, the fan does not function. The box is getting real hot, and smells a bit :shock:

I've tried reading around the forums and STFW, but I'm a linux noob and haven't been able to find a solution I recognize as such. Forums have, however, got me thinking it is likely an ACPI or laptop mode problem. But I do not know how to proceed.

I have run acpi -V in a terminal. When it shows me on AC power, the command reports battery 1 at 95%, with a steadily *increasing* time until fully charged. Once it switches to showing battery, it claims 100% charge and discharging.

Any help sorting this out would be appreciated. I'd love to leave WinXP behind, but I cannot afford to fry my box!

---

### Post by vanden on 2005-12-26
Sorry for a self-reply, but I've made a lot of progress.

What I've learned is that the Fujitsu supplied DSDT file compiles under Microsoft's ASL compiler but not the standards compliant one from Intel. I determined this by decompiling the DSDT and recompliling with the Intel compiler I downloaded, all as detailed here <http://forums.gentoo.org/viewtopic.php?t=122145>. When doing so, the code failed to compile as it employed undefined names. 

I've certainly hit my limits in terms of what I can do -- I can't fix C code meant for the BIOS :-)  But, in case someone else googles this up, I thought it worth posting.

(Don't let that discourage you from posting any suggestions you might have, though ;-)

---

