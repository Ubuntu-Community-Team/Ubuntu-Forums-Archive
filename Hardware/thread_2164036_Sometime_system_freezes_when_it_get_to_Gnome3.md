---
title: "Sometime system freezes when it get to Gnome3"
date: 2013-07-20
forum: Hardware
---

### Post by LastStarDust on 2013-07-20
Hello,
My issue is that often, when I boot, the system freezes just when I get to the desktop.
Grub2 is fine. Log In is fine. But when eventually I get to Gnome3 the only thing responding is the mouse. I can move the pointer but I can't click anything. Even keyboard is freezed. Ctrl-Alt-Stamp RSist-REISUB or Ctrl-Altr-Backspace or even Ctrl-Alt-Canc seem to not work. The only option available is hard reset. This issue happens randomly a time about ten. The other times everything seems ok.

I don't know what to log, the only thing I found was this warning in /var/log/dmesg
```
[    0.494964] ACPI Warning: Incorrect checksum in table [TAMG] - 0xF8, should be 0xF7 (20110623/tbutils-314)
```

Some usefull info:
[LIST]
[*]Ubuntu: 12.04 amd64
[*]uname -a : Linux zion 3.2.0-49-generic #75-Ubuntu SMP Tue Jun 18 17:39:32 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
[*]MB: GA-P55A-UD5 rev 1.0
[/LIST]

---

