---
title: "Installation Compiling Times"
date: 2008-03-18
forum: Gentoo and derivatives
---

### Post by regomodo on 2008-03-18
I'm currently at the 12th hour of installation of the base system. It took me previously 6 hours messing with the kernel before i gave up and used the genkernel after not being able to get rid of kernel panics.

If i'm almost 1/2 way through an *emerge --update world* how long would it take to get an xserver and kde done? At this rate i'm starting to think i won't be able to touch my laptop until next week!

Umm, it's a 448Mhz P3 processor.

---

### Post by regomodo on 2008-03-19
28th hour and still compiling. Compiling xfce4 and gdm atm

---

### Post by erginemr on 2008-03-19
You didn't go for stage 3rd installation. May I ask why?

---

### Post by regomodo on 2008-03-19
> **erginemr said:**
> You didn't go for stage 3rd installation. May I ask why?

i did go for the stage 3 as the guide suggested. It's been updating itself, and compiling Xorg, xfce4, and gdm since the kernel compilation. I'm almost finished compiling the first bit of software, firefox.

I switched to xfce as i tried the kde4 guide and it crapped out when i try to install kde.
[edit] holy crap! 2hours in and still compiling firefox
took just shy of 3 hours in the end

---

### Post by regomodo on 2008-03-20
Well it's getting on for almost 3 days of near constant compiling. I missed out about 8hours of compiling time as i left it to compile some basic applications whilst i was asleep. Unfortunatley  hadn't specified the "svg" USE tag when compiling cairo earlier so it stopped at 4of57 packages to compile and then recompile cairo.

ATM wireless (rt2500) doesn't work correctly. Cannot get it to work with dhcp and haven't tried iwpriv commands yet.

Currently at 24of54 packages (gimp) and if all goes well i'll have a usuable laptop, minus wireless, after 4days of near constant compilation. I feel sorry for that P3 and its teeny fan.

---

### Post by regomodo on 2008-03-21
i gave up on all the packages as gimp failed. Installed icecc which helped somewhat. Unfortunately, a "*emerge --update --deep world*" has borked my system. Got so far as busybox and now it fails everytime. I'm currently emerging gcc as it appears to be the problem, but, it is taking forever to emerge and icecc appears to have stopped partway through the compilation.

Wow, i thought the Gentoo hater trolls were joking
[edit] oh boy. what a waste of time. Can't even install gcc anymore

---

### Post by mips on 2008-03-22
> **regomodo said:**
> 
Umm, it's a 448Mhz P3 processor.

That is going to be slow.

If you do decide to give up then try Arch.

---

### Post by regomodo on 2008-03-22
> **mips said:**
> That is going to be slow.

If you do decide to give up then try Arch.

i have in the past for a fair bit but i could not get the Arduino to work correctly in it. Tried again recently but couldn't find libgtk2+ development package to compile rutilt with --launcher=nopasswd option

---

