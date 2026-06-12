---
title: "Lexmark S505 (S500, S400, S300 etc series) + 64 bit?"
date: 2009-09-23
forum: Hardware
---

### Post by velmont on 2009-09-23
My father has gone and done a stupid, stupid thing. He bought a Lexmark printer.

This printer needs all sorts of proprietary evil Java software to run. It requires some special mDNS thingy to run.

Thing is, his computer is 64 bit linux. Quite ordinary, yes. But Lexmark wants to protect their rotten code and only made this run on x86.

Actually, now that I saw this thing runs Java (I tried installing it on a x86 computer), it might work to just fool dpkg into installing it regardless.

Anyway, thought I just give heads up to everyone that might search for this. Do *NOT* buy Lexmark printers Intuition series S500, S400, S300, S200.

---

### Post by velmont on 2009-09-23
OK, I found a PPD in there, but since this thing uses mDNS (it's wireless) I don't know how to make CUPS find it.

I tried system-config-printer, but to no avail, no printer shows up. Grrr.

---

