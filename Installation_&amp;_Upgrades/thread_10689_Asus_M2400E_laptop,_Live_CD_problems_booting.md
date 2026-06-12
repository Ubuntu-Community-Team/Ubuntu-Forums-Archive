---
title: "Asus M2400E laptop, Live CD: problems booting"
date: 2005-01-10
forum: Installation &amp; Upgrades
---

### Post by malesca on 2005-01-10
Hello,

I'm trying to boot from the Ubuntu Live CD on my Asus M2400E (a.k.a. M2E) laptop. The installed OS is Windows XP Pro. [Some system details from CPU-Z](http://henrik.nyh.se/dump/ubuntu/cpuz.txt).

I first had problems with the progress bar freezing at something like 20 or 30%. I resolved that by booting with "acpi=off".

However, when the progress bar reaches 100%, my computer simply shuts down. I've tried pressing F2 to get a "text view" of the boot process. I don't know how to log that text, however. I took [a few (bad) photos of the screen](http://henrik.nyh.se/x/http://henrik.nyh.se/dump/ubuntu), but I imagine that's not enough to help.

EDIT: I think the last line shown before it shuts down (at least when i tried to boot "failsafe") is

running morphix/*something*/adduser

---

### Post by randy on 2005-01-10
File a bug in bugzilla.

---

### Post by malesca on 2005-01-10
Thank you.

To file a bug, I would suppose I need more information. Do you have any suggestions as to how I can get a log of what happens (and fails) during boot?

---

### Post by alightly on 2005-01-29
Hi, I too have this laptop and have the same issue, either the progress bar stalls at about a quarter way through or the whole boot process just hangs.

I've also tried to install it as a dual boot with WinXP but same problem, just hangs.

Will keep an eye on this thread, I guess!

---

