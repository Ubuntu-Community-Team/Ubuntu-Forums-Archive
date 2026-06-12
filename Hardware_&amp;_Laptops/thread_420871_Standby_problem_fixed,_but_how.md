---
title: "Standby problem fixed, but how?"
date: 2007-04-24
forum: Hardware &amp; Laptops
---

### Post by alnino2005 on 2007-04-24
I downloaded and installed the beta version of Feisty Fawn about a month ago with little trouble getting it to work the way I wanted it to. (This is amazing for me, because I'm fairly new to the linux world.) Anyway, ever since I've upgraded to the final 7.04 version, standby nor hibernation have been working for me, but I recently found a remedy.

In the grub menu upon boot, boot into the **2.6.20-13-generic kernel**. It seems under any kernel later than this, at least until **2.6.20-15-generic**, standby and hibernation will not work on some machines.

I feel like a doctor practicing medicine, I find the remedy, but I have absolutely no idea how or why it works. Would anyone have any insight as to what might be wrong? I wouldn't doubt it's a bug, but does it have something to do with ACPI or another piece of software?

Thanks guys, being a new convert, Im amazed at the amount of help and info to be found on these forums. You guys are great and Im proud to be part of the community!

Later!
[SIZE="4"]Alan[/SIZE]

---

