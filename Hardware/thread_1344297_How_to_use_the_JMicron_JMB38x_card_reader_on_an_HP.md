---
title: "How to use the JMicron JMB38x card reader on an HP dv4 laptop"
date: 2009-12-02
forum: Hardware
---

### Post by madengineer on 2009-12-02
Hope this helps somebody...

I was having trouble with the card reader not working on my HP dv4-1500 laptop; although it would work in Windows, lspci didn't even show that the device existed when running Ubuntu (Karmic). Putting a card in didn't help, nor rebooting with a card installed.

It turned out that there was a BIOS setting, under "System Configuration", called "Card Reader Power Saving", that is on by default. Apparently the kernel doesn't know to look for the device and go through whatever procedure the Windows driver was using to wake it up. Turning off that option made the card reader show up in lspci and function normally. Hopefully this won't be a significant power drain; it is just a card reader, so it doesn't seem likely that it'll do much.

---

### Post by kay-man on 2010-01-10
Thanks, it just did.

I thought I was was going crazy trying to find the kernel module I forgot to compile. Never thought of checking the bios. So thanks again!

---

