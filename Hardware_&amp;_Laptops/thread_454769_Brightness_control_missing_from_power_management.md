---
title: "Brightness control missing from power management"
date: 2007-05-25
forum: Hardware &amp; Laptops
---

### Post by TwiceOver on 2007-05-25
Running Feisty on a Dell 1501 laptop.  The Fn key shortcut will dim only one stage so full on or very minimal.  Also there is no Brightness control under the power management.

I'm using XGL/Beryl and fully updated.  Anyone have any ideas?

---

### Post by TwiceOver on 2007-05-26
I found that this is a known problem with Dell LCDs.  

I have found [This]("http://www.berthon.eu/wiki/foss:ubuntu:wikishelf:hal:feisty") link to install the backport of libsmbios.  Unfortunately I get a dependancy error when I get to the buildpackage step.  I have double and triple checked the listed dependencies and I have the ones required.  Anyone else have an idea, or a way for me to find what dependencies are expected?

This is the last thing wrong with this laptop.  Everything else seems to work flawlessly.

---

