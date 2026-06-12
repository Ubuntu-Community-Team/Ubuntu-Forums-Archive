---
title: "Laptop screen won't dim!"
date: 2007-08-24
forum: Hardware &amp; Laptops
---

### Post by ghstzr0 on 2007-08-24
I know I've asked this before and it never was answered -- maybe now...

I have a Fujitsu Lifebook 1040 and my screen has NEVER (since dapper) had dimming controls!  Why not?  Is there a kernel option I can use?

Secondly, why can't I tell my laptop to hibernate (suspend-to-disk) after a certain amount of time??

---

### Post by Skerious on 2008-05-22
> **ghstzr0 said:**
> I know I've asked this before and it never was answered -- maybe now...

I have a Fujitsu Lifebook 1040 and my screen has NEVER (since dapper) had dimming controls!  Why not?  Is there a kernel option I can use?

Secondly, why can't I tell my laptop to hibernate (suspend-to-disk) after a certain amount of time??

I don't know how to dim mine either.  Can't find an answer anywhere.

---

### Post by HarM_triade on 2008-06-12
There is a way to dim the screen. It all depends if acpi controls the dimming or not.
to check: see if you've got a file like /proc/acpi/video/VGA/LCD/brightness
on your system.
That's on my fujitsu T3010D. if you read the file it will tell you how many levels it supports and what the current setting is.
I then modified an existing script I found (alas I don't remember where) which I've attached as "dim.sh" and "brite.sh".
Be aware that you might need to modify the scripts to match the levels your laptop provides!

The provided scripts can be either assigned to specific keys in various ways depending on which window-manager you use or "standalone" using a command ("bash dim.sh" or "bash brite.sh")or maybe an icon on the desktop that points to the scripts.

---

