---
title: "Intrepid: Freeze on Boot, dv6809wm laptop"
date: 2008-12-22
forum: Hardware
---

### Post by snl2587 on 2008-12-22
After I finally had a little time, I decided to upgrade my laptop from Hardy to Intrepid. Everything went fine, except that whenever the laptop boots I have to continuously switch the wireless on and off.

I decided to completely reinstall Intrepid and the problem persists.

I saw that there was one hit on google for this with no solution. Does anyone know what could be causing this or what I could do to diagnose it?

(I'm also working on getting the wireless working...it's one of those Atheros cards and the restricted driver isn't working...maybe this is part of the problem?)

Thanks in advance for any help!

---

### Post by Neard on 2008-12-31
I seem to have the same issue, only I've got a dv6815nr. It's got an Atheros AR5007 wireless card.

I actually haven't tried switching the wireless on and off, but if I hold down the Ctrl key (I think it's any key, but that's what I always use...) it keeps going.

It didn't occur on 8.04, but happens on 8.10, both booting with the disk (it was an RC disk) and after installing with Wubi (using the final disk image as downloaded by the program).

---

### Post by snl2587 on 2009-01-13
I figured I should write a follow-up to this.

Long story short: I was not able to solve the problem and am writing this from a fresh Wubi install of 8.04 (the booting was not the only problem, not by far). I'm guessing it was a driver issue that was not solved by following the wiki, but if anyone knows what might have caused it I appreciate the input, especially if Jaunty retains the regression.

---

### Post by xyos on 2009-01-14
sorry for my bad english

i've got a similar bug in my hp dv6709, the solution for my problem was in this topic in launchpad [https://bugs.launchpad.net/ubuntu-release-notes/+bug/272247](https://bugs.launchpad.net/ubuntu-release-notes/+bug/272247) "This bug happens with 2.6.26 and 2.6.27 kernels with a computer that has Nvidia MCP67 motherboard. A known workaround that sometimes works is to add nolapic to GRUB boot kernel options. acpi=noirq is also known to work."

just edit yor /boot/grub/menu.lst and add the acpi=noirq to ypur kernel.

---

### Post by snl2587 on 2009-01-14
Wow thanks. I think for now I'll stick with 8.04 but I'll definitely keep that in mind if I have the same problem with Jaunty.

---

