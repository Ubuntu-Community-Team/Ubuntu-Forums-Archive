---
title: "Computer doesn't shutdown properly"
date: 2008-05-05
forum: Hardware
---

### Post by sirjavabean on 2008-05-05
In the past my various Linux distributions have all been able to shutdown perfectly fine on my hardware (Fedora, Gentoo, Suse, various others). However since installing Ubuntu (or any variants) whenever I try and shutdown the computer hangs at the end of the shutdown screen (ie it shuts down fine, just doesn't switch off). I believe this is an ACPI issue, related to the fact that I have to have ACPI turned off for Ubuntu to boot into X? None of the newer Ubuntu Live CDs will boot graphically without ACPI turned off either.

This is really annoying me! Sorry if I haven't been very specific, I can provide more details if needed. I hope there's a quick fix - I don't want to have to buy a new motherboard!

---

### Post by unutbu on 2008-05-05
This may or may not work for you: Run
```

gksudo gedit /etc/modules
```
Add the line
```
apm power_off=1
```
Then boot with kernel options: "acpi=off apm=power_off".
You have to reboot once before the change will take effect.

---

### Post by jwishnie on 2008-05-28
I'm having a similar problem since I upgraded to Hardy (Xubuntu, running latest updates including linux-image-2.6.24-17-generic kernel)

My system (FIC ION A603) supports full ACPI and I didn't have this problem in Feisty or Gutsy.

Think this is ACPI related and the solution is to turn it off as suggested above?

Trying to understand why this would have happened only after upgrade...

---

### Post by unutbu on 2008-05-28
Hello jwishnie, unlike sirjavabean, you have not yet decided to run the kernel with the "acpi=off" boot option. Since in the past (on Feisty and Gutsy) you have been able to run with acpi on, it is best to find a way to run with acpi on in Hardy as well.

People turn acpi off because of severe problems such as the machine hanging at boot. Turning acpi off, however, can cause certain hardware to go undetected, and it can cause this shutdown hanging problem.
So I would recommend avoiding the acpi=off option if you can.

You could try booting with kernel option "apm=power_off" and editing /etc/modules
to include 
```
apm power_off=1
``` I don't think there is any harm in trying that. 

Also, were you experiencing this problem in Hardy before the linux-image-2.6.24-17-generic kernel update?

---

### Post by nexx on 2008-05-28
Experiencing shutdown problem since heron kernel update also, seems to be related to my antique bios and overuse of the computer (overheating the processor by heavy DVI download and web site javascript programming of my arts diaporamas with GEANY).
I am amazed that the Xnote micro-laptop:popcorn: still work SUPERBLY otherwise.

---

### Post by ubockto on 2008-05-28
> **unutbu said:**
> 
Then boot with kernel options: **"acpi=off** apm=power_off".
You have to reboot once before the change will take effect.

Obviously, if you have Hyper-Threading, you will have to put "acpi=ht" instead

---

### Post by jwishnie on 2008-05-28
> **unutbu said:**
> Hello jwishnie, unlike sirjavabean, you have not yet decided to run the kernel with the "acpi=off" boot option. Since in the past (on Feisty and Gutsy) you have been able to run with acpi on, it is best to find a way to run with acpi on in Hardy as well.

People turn acpi off because of severe problems such as the machine hanging at boot. Turning acpi off, however, can cause certain hardware to go undetected, and it can cause this shutdown hanging problem.
So I would recommend avoiding the acpi=off option if you can.

You could try booting with kernel option "apm=power_off" and editing /etc/modules
to include 
```
apm power_off=1
``` I don't think there is any harm in trying that. 

Also, were you experiencing this problem in Hardy before the linux-image-2.6.24-17-generic kernel update?

Hi Unbunt, the problem has been there since Hardy initial release with the linux-image-2.6.24-16-generic.

I also tested against linux-image-2.6.25-1-generic from the proposed Intrepid packages. 

All exhibit the same problems.

I will try apm.

Any other suggestions?

- Jeff

---

### Post by jwishnie on 2008-06-08
Hi all,

The issue on my FIC ION was the framebuffer module: lxfb

This is not blacklisted in /etc/modprobe.d/blacklist-frambuffer (where a couple dozen others are).

Adding 'blacklist lxfb' to this file solves the problem.

---

### Post by unutbu on 2008-06-09
Wow, thanks for that info jwishnie. How did you track down the problem to lxfb?

---

### Post by jwishnie on 2008-06-09
Tried to APM/ACPI stuff with no luck.

Tracked the problem to bootsplash--booting with 'splash' removed from the kernel options solved the problem, so I figured it was framebuffer related.

Noticed 'lxfb' (the framebuffer module that will load on my hardware) was _not_ on the blacklist, so added it!

---

### Post by unutbu on 2008-06-09
Huh. How about that. How did you find out the problem came from the splash boot option?

---

### Post by jwishnie on 2008-06-09
No great insight--I turned off splash to watch boot-time messages for any info, and noticed that reboot worked fine with splash off...

---

### Post by unutbu on 2008-06-09
Ahh.. Good for you. :)

---

