---
title: "recompile SIS Mirage 1 (662/761) Windows XP driver for Ubuntu Linux"
date: 2008-08-02
forum: Hardware
---

### Post by m4c13k on 2008-08-02
I done the big mistake and bought an Intel D201GLY2 main board with an SIS 662/761 gpu chipset. Now I have the problem to find a 3D drive for this chipset. 

I tried out the drivers on the intel support site, but they will not work. Then I wrote SIS an email, they told me, that only intel can give me the driver.

A new idea is to recompile the MS Windows Xp driver, and make it usable for GNU/Linux and specially for Ubuntu-Studio.
Can someone tell if there is a possibility to recompile drivers and how can I do that?

In the other way, is there a possibility to use the MS Windows XP gpu drivers in Linux (like ndiswrapper for wifi cards)?

The driver for MS Windows XP is very fine :(. It works stable and supports the full functionality for this chipset. I tried this out on an parallel boot on the same board.

---

### Post by C.S.Cameron on 2008-08-10
I have been looking for a fix for the D201GLY2 video problem for months. The only solution I have found is the DG945GCLF. It is just as cute and the same price but much more Linux friendly.

---

### Post by m4c13k on 2008-08-11
I fixed the D201GLY2 video problem within two days, but only with 2D support. Here is a mini HOWTO I wrote in an other threat:
[http://ubuntuforums.org/showthread.php?t=875418]("http://ubuntuforums.org/showthread.php?t=875418")

For some aplications like counter-strike 1.6, proe wildfire 3, compiz-fusion, etc. i need 3D support. This is the only reason I looking for a wrapper or a way to recompile the MS driver.

---

### Post by jocko on 2008-08-11
I'm pretty sure you can never compile a windows driver to run on linux, and I doubt there is a way to make a wrapper to use a windows graphics driver in linux.

---

