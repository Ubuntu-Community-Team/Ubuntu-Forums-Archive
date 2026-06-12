---
title: "Dell Inspiron 15 7537 Intel Gfx: Transparency checkerboarding issues"
date: 2014-02-19
forum: Hardware
---

### Post by Echoloc8 on 2014-02-19
Ubuntu 13.10 64-bit, there's no discrete graphics card in this unit, just integrated Intel Haswell graphics.

Seeing intermittent but pervasive checkerboarding wherever transparency is used, e.g., Gnome3 Activities view, Steam, Android emulators.

Loving this laptop for Linux use, but the checkerboarding thing is annoying, especially when showing it off. :-D Gaming is almost unusable.

What info can I provide to help work this issue? 

Also, I'm planning to go to 14.04 LTS when it's out, so are there any updates it will have that 13.10 won't necessarily get?

Thanks!

-Rich

---

### Post by johannes-hidding on 2014-04-17
I have the same on my Lenovo Thinkpad S1 Yoga with Intel i7-4500U. 'lspci' gives:
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
In addition I have issues with firefox intermittendly showing little black blocks when scrolling on some pages.
The few games that I have tried worked fine.
There is a bug-report that shows the same problem here: [https://bugs.freedesktop.org/show_bug.cgi?id=73835](https://bugs.freedesktop.org/show_bug.cgi?id=73835)
Cheers, Johan

---

