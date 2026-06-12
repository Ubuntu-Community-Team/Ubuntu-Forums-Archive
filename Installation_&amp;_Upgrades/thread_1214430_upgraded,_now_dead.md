---
title: "upgraded, now dead"
date: 2009-07-15
forum: Installation &amp; Upgrades
---

### Post by svelter on 2009-07-15
Hi, there.  I believe this is somewhat similar to a couple threads, but not really the same and cannot be fixed by suggestions I've found elsewhere thus far.

I was running Intrepid up until 2 days ago. I updated to Jaunty, and everything ran with no problem at all. Last night I tried to boot and got a screen similar to the one shown [here]("http://ubuntuforums.org/showthread.php?t=1206355") (see third image). I cannot do anything - there is no sound. I cannot do ctrl+alt+F1. I have to hard power down and restart. 
 
These are the steps I've tried:
 
[LIST]
[*]pressing esc to enter GRUB menu, I have tried all the options listed (kernel 2.6.28-13-generic; same kernel in recovery mode; kernel 2.6.27-14-generic; same kernel in recovery mode)
[*]running dpkg, i get a long list of errors (failed to fetch various items from various URLs; some index files failed to download; you way want to run apt-get update to corect these problems). it tells me it will upgrade wine and wine-gecko. I agree, and it fails to fetch the items
[*]have chosen items to update grub bootloader and xfix to auto repair graphic problems
[*]dropped to root and ran apt-get update. fails to retrieve all items and tells me to run apt-get update to correct the problems.
[*]entered the following at root:
[LIST]
[*]sudo dpkg-reconfigure xserver-xorg
[*]went through all steps to no avail
[/LIST]
 
[*]downloaded the .iso and burned to CD. through boot menu, booted from hard drive with various options selected (acpi=off; noapic; nolapic). none worked.
[*]tried following the how-to in [this]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=edit+xorg.conf") thread, but "gksudo gedit <anything>" returns this:
[LIST]
[*](gksudo:5006): Gtk-WARNING **: canot open display
[/LIST]
 
[/LIST]
I can run Jaunty from the LiveCD - no problem there. So I don't know if the problem I have is related to my graphics card or not. I do have an ATI mobility radeon, but believe I also have a pentium video chipset integrated into the motherboard. I'm not sure which my computer is reading at this point, as my BIOS doesn't list this info.  I'm running an HP Pavilion dv4000 series, pentium m 2.13 GHz. 
 
I am feeling a bit desperate at this point, as I am a relative noob in linux and would really prefer not to reformat and lose my files.  I also feel like I should be able to conquer this problem.

I wouldn't mind reverting back to intrepid, but I'm not really sure if that's an option.  

A fresh batch of virtual cookies to anyone who can help. ;)

Thanks in advance.

---

### Post by philcamlin on 2009-07-15
kinda looks like a graphics error but it doesnt appearthat way 

maybe im wrong 

can you get to terminal or not boot at all

---

### Post by svelter on 2009-07-15
> **philcamlin said:**
> kinda looks like a graphics error but it doesnt appearthat way 

maybe im wrong 

can you get to terminal or not boot at all

i can boot in recovery mode and drop to root with network.  from there i can log in and run some commands.

---

### Post by philcamlin on 2009-07-15
if its what you say it is in the 3rd pic in the post you sowed it looks like a graphics error

---

### Post by svelter on 2009-07-15
if it's a graphics error, would it still work running off of the cd?  sorry if that's an inane question.  it just seems as though an incompatibility between my hardware and the OS would be the same whether booting from hard disk or cd.  unless it's a driver issue.  of course, i could be misunderstanding things as well.

any idea how i could fix it if it is a driver issue?

---

