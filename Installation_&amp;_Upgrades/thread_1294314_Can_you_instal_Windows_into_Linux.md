---
title: "Can you instal Windows into Linux?"
date: 2009-10-18
forum: Installation &amp; Upgrades
---

### Post by szaemon on 2009-10-18
I here about using Wubi to instal Linux into a file on Windows, but is there a way to instal Windows into a file on Linux?

---

### Post by arcull on 2009-10-18
Yes you can I a certain sense, using virtualizations, I prefer Virtualbox check [http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by bulldog on 2009-10-18
Not that I know of.
You can use however,something like Virtual Box,which let you install windows on a virtual partition within ubuntu.

---

### Post by Lars Noodén on 2009-10-18
As mentioned, virtual box is an option.  Another is qemu.

However, if you are longing for a specific program, then you might see if it is supported on [WINE](http://wiki.winehq.org/ImportanceOfWine).  WINE allows you to run most Windows programs on linux, so that your transition to Free Software is smoother.  There is another version of WINE known as [CrossOver](http://www.codeweavers.com/products/cxmac/)

The advantage of virtual box and qemu are that you have a whole separate system.  Another advantage of either, is that you can make snapshots so that when Windows succumbs to malware or Windows-bitrot, you can roll back to an earlier Virtual Machine image.  

The advantage of WINE is that you do not have to maintain a whole separate system and that performance is good.  

Can you say which programs you are looking for?

---

