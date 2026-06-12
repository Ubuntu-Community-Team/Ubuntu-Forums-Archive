---
title: "burning a cd compatible with old pc?"
date: 2008-11-18
forum: General Help
---

### Post by Bulletbeast on 2008-11-18
I want to burn a CD of Windows 98 SE from an iso from Ubuntu. The old machine I intend it for, though, boots only from a Windows 98 boot disk, which then loads some old CD drivers, and the CD I burnt using Brasero was unreadable. What filesystem should I use, and what's a good ISO burning app (Brasero doesn't seem to let me choose a filesystem anyway)?

---

### Post by Th3Professor on 2008-11-18
> **Bulletbeast said:**
> I want to burn a CD of Windows 98 SE

To avoid making a suggestion that could lead to possible piracy, I'll recommend that you not burn Windows to a CD and use an original MS install CD. ;)

...however...

> **Bulletbeast said:**
> from an iso from Ubuntu.

There are several CDs/DVDs that have encryptions preventing copying, though there are always new means of cracking and making it possible.

Check out the package manager for apps that could assist you with burning CDs/DVDs. You might try searching for "iso" or "burn". There are several applications designed for burning, though each has its own pros/cons.

> The old machine I intend it for, though, boots only from a Windows 98 boot disk, which then loads some old CD drivers, and the CD I burnt using Brasero was unreadable.If you properly burn an ISO to a CD, and if the start-up application on the CD is designed for a specific purpose, then the CD should work.

However...

If you are having difficulties booting from a CD it may not be the CD at all but, rather, your BIOS.

Try this:
1. Put in the CD.
2. Reboot.
3. During reboot press "del" or "f8" or another key (f2, f10, f12, etc.) (get the boot screen).
4. Select boot from CD if it is offered.
5. CD boots.

or...
3. During reboot press the key to go into BIOS set-up.
4. Set the boot order to include boot from CD (and put it up top on the list for now).
5. Save/exit, reboot, CD boots.

> **Bulletbeast said:**
> What filesystem should I use, and what's a good ISO burning app (Brasero doesn't seem to let me choose a filesystem anyway)?

ISO = an image/archive file, it is the ISO format (International Organization for Standardization).

If you see 9660 in your options when burning your ISO, select it.

You could technically opt for the UDF file system, though most burning software these days is designed to do most of the work for you automatically. However, you will still need to tell it that you are burning an ISO or, more specifically, ISO 9660.

DISCLAIMER: I am not advocating piracy. I encourage using the original.

---

### Post by Bulletbeast on 2008-11-18
It is impossible for me to obtain an original for monetary reasons as well as because Windows 98 is not sold anymore, and the PC I'm trying to fix for my father wouldn't run anything newer, and dad can't, or doesn't like using Linux. And booting from CD isn't a necessity, although it turned out that this particular PC could do it after all. And the PC's CD drive turned to be broken, anyway.

*However,* I discovered **K3b** (right? right.). It's SO much better than Brasero. Although Gnome may be kinda prettier than KDE, all KDE apps I've tried are superior.

---

