---
title: "Card reader on HP ProBook 4510s not recognised by Ubuntu"
date: 2010-08-04
forum: Hardware
---

### Post by AndyM3 on 2010-08-04
I recently got an HP ProBook 4510s laptop and, after some distro hopping, settled with the KDE edition of Linux Mint 9.
Today I tried reading a memory card, but KDE didn't auto-mount it. Even more surprisingly, lspci did not find any card reader (output [here]("http://pastebin.com/gctGPmma")).
Card reader is listed as working [here]("http://www.linlap.com/wiki/hp+probook+4510s"), however, so I think it's something about my configuration...
Google only revealed problems with TI card readers, but mine doesn't seem to be one of those.
Thanks in advance :)

---

### Post by meijer.o on 2010-08-04
I have the same computer with the same specs. it should just work. Sometimes this bug, see link bothers me, does your computer shows the same bug? see [https://bugzilla.kernel.org/show_bug.cgi?id=16236](https://bugzilla.kernel.org/show_bug.cgi?id=16236)

Best regards, O. Meijer

---

### Post by AndyM3 on 2010-08-04
> **meijer.o said:**
> I have the same computer with the same specs. it should just work. Sometimes this bug, see link bothers me, does your computer shows the same bug? see [https://bugzilla.kernel.org/show_bug.cgi?id=16236](https://bugzilla.kernel.org/show_bug.cgi?id=16236)

Best regards, O. Meijer

Hmm... might be KDE fooling around with me then... or maybe a BIOS setting?

About your bug, fixing should be as easy as alt-f2, "xrandr", enter. I got it a few times when messing with displays on GNOME.

---

### Post by AndyM3 on 2010-08-22
If anyone has the same problem and finds this thread, here's the solution. You need to turn off the card reader in the BIOS setup (F9 on boot). I think it's under "built-in ports" or something like that. Then save, boot into Linux, reboot to BIOS setup again, turn on the card reader, save, boot into Linux again and you're done.

---

