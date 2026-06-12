---
title: "Microsoft keyboard disabled on Grub screen"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by unclescotty on 2007-05-23
Hi,

I used Ubuntu Linux v6.06 to create a partition on my HD. On one partition, I installed WinXP Professional and afterwards on the other Linux.

When I restart my PC to see how grub will manage my boot, it tells you to use the up and down arrow keys to select the OS you want to boot from a list, but then those keys are inoperative for that menu. In fact, the whole keyboard doesn't function for that menu. So, I cannot access my XP partition. And, the keyboard is a known-good keyboard- working in both XP and in Linux once Linux boots up. It is a Microsoft keyboard.

Have you ever encountered such a snag? Are there special Linux drivers for various keyboards? Somehow that doesn't seem to be the issue either, because the keyboard works once the Ubuntu desktop comes up.

Any thoughts? Scott

---

### Post by bernied on 2007-05-23
Grub is not linux. Grub is like a mini operating system in its own right, so this is not a linux issue as you suggest. This is also clear because the keyboard works in linux.

Can you access your bios setup using the keyboard? Is there anything in the bios that refers to the keyboard?

Is it a USB keyboard? PS2?

If it is a USB keyboard, you can try it in a different USB socket (probably the one on top or furthest to the left), I think sometimes the bios looks in only one socket for a keyboard at startup - I had a USB wireless keyboard like this once.

---

### Post by bigyes on 2007-05-23
yes, if it is a USB keyboard,
 you would like to check the BIOS to enable USB keyboard to boot:-)

---

