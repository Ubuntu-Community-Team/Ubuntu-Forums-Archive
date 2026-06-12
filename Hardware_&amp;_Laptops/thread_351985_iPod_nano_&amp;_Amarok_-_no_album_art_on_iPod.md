---
title: "iPod nano &amp; Amarok - no album art on iPod"
date: 2007-02-02
forum: Hardware &amp; Laptops
---

### Post by enigma_0Z on 2007-02-02
Hi all,

I'm not sure if this is the right forum but...

I've just got an iPod Nano, and am able to put songs onto it by using amarok just fine, however, I did mess with gnupod to try and get it going at first. Now, gnupod shows up in my about screen, and album art does not show up for songs that I add to my iPod from amarok.

How can I get it up there, and do I need to blow away the database on my iPod and let Amarok rebuild it?

---

### Post by enigma_0Z on 2007-02-04
--bump--

OK I've found the problem.

Basically, libgpod depends on a file caled "SysInfo" on you iPod to determine what kind of iPod you have, but this file was missing...

Furthermore, the libgpod that ships with ubuntu edgy is slightly old, and has some issues with x86_64 & album art, as well as lacking several features...

I've got a howto on my blog at [http://blog.pause.homelinux.net/index.php?/archives/8-Linux-+-Amarok-+-iPod-Nano-2nd-Gen-or-others-w-updated-firmware-+-WORKING-album-art.html](http://blog.pause.homelinux.net/index.php?/archives/8-Linux-+-Amarok-+-iPod-Nano-2nd-Gen-or-others-w-updated-firmware-+-WORKING-album-art.html)

---

