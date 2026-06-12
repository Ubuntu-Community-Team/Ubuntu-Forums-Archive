---
title: "another system freeze with Hoary"
date: 2005-04-19
forum: Hardware &amp; Laptops
---

### Post by aledin on 2005-04-19
This morning I had another system freeze: i was in framebuffer console (like the other time the laptop freezed with Hoary), reading newsgroups. No control of keyboard or mouse and the fan of the laptop up running wild... I had to manually power off the computer.

I don't know if is it fault of the kernel or of the Xorg system (i think more about the kernel...). And i have no time to rebuild a new kernel trying and trying to solve the problem. All I can say is that Hoary is NOT stable for me. I'll wait next days to see if there will be a new kernel upgraded with less problems in the repository...

i'm sorry, because the work of Ubuntu developers is very good, but i'm seriously "tempted" by changing distro and come back to Debian Testing.

---

### Post by aledin on 2005-04-21
[QUOTE=aledin]This morning I had another system freeze: i was in framebuffer console (like the other time the laptop freezed with Hoary), reading newsgroups. No control of keyboard or mouse and the fan of the laptop up running wild... I had to manually power off the computer.

I don't know if is it fault of the kernel or of the Xorg system (i think more about the kernel...). And i have no time to rebuild a new kernel trying and trying to solve the problem. All I can say is that Hoary is NOT stable for me. I'll wait next days to see if there will be a new kernel upgraded with less problems in the repository...

i'm sorry, because the work of Ubuntu developers is very good, but i'm seriously "tempted" by changing distro and come back to Debian Testing.[/QUOTE]

I have put "noinotify noapic" in the kernel line of grub.
Hope this will help avoiding the freezes...

---

