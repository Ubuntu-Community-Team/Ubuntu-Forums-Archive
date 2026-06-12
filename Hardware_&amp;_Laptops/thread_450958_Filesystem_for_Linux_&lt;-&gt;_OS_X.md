---
title: "Filesystem for Linux &lt;-&gt; OS X"
date: 2007-05-21
forum: Hardware &amp; Laptops
---

### Post by ericbarch on 2007-05-21
I have a 320GB external USB hard drive and I need the maximum amount of space possible after formatting. I need to be able to move it back and forth between an OS X system and an Ubuntu system. I need full read/write permissions for both operating systems. Is there a file system that can do all this without much work? I've tried setting up an HFS drive in Ubuntu and it doesn't work well at all.

---

### Post by kidders on 2007-05-22
Hi there,

Linux has full HFS support (albeit unjournalised). It's an especially nice choice, since OSX and Linux use the same filesystem access control paradigm. While they *can* be made to work, many other alternatives (eg FAT or UFS) come with major downsides.

> I've tried setting up an HFS drive in Ubuntu and it doesn't work well at all.Could you be more specific? Perhaps there's something small that isn't quite right.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

