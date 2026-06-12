---
title: "Installation on old computer"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by P_Aleksandrov on 2009-07-28
Can Ubuntu 9.04 (from alternate CD) be installed on computer with Pentium 180 MHz and 32 Mb RAM? Or is it better to use another distribution of Linux?

---

### Post by chrisinspace on 2009-07-28
You may want to install something lighter like [Damn Small Linux]("http://distrowatch.com/table.php?distribution=damnsmall") or [Puppy Linux]("http://distrowatch.com/table.php?distribution=puppy").  You could probably run Ubuntu, but you'd need to do a customized install.  I'd say install from a server disk (there's no GUI to start with) and add in a lighter desktop than XFCE, Gnome, or KDE.  They all require more resources than you have in their current incarnations.  I've been hearing good things about LXDE, but it's still in development.

---

### Post by x33a on 2009-07-28
as chris said, dsl or puppy should be the best. or, you could try a debian minimal+xfce, or arch linux + xfce or some other lightweight DE.

---

### Post by Sef on 2009-07-28
Try [DeliLinux]("http://delilinux.de").

---

### Post by prshah on 2009-07-28
> **P_Aleksandrov said:**
> Pentium 180 MHz and 32 Mb RAM?

> **Sef said:**
> Try [DeliLinux]("http://delilinux.de").

+1 vote for DeliLinux. I'm using Deli on a very old Pentium 200 MMX with 32 MB (Originally 16MB) RAM.

I tried a lot of distros before finally settling on Deli for this crappy machine. See a screenshot of it running in a virtual machine with only 12 MB RAM ! (Yes, TWELVE, not ONE-TWENTY-EIGHT). (I wanted to see how low I could go, 12 is the absolute minimum for GUI, otherwise I could go lower).

---

### Post by lindsay7 on 2009-07-28
For a small distribution, I like Siltaz. It has a very easy setup and sees wireless cards and printers without a lot of work.

[http://www.slitaz.org/en/get/](http://www.slitaz.org/en/get/)

---

### Post by P_Aleksandrov on 2009-07-28
I forgot to say that I don't want to install any desktop environment on it. I want to install only samba and telnet servers (to access floppy disk drive and so on).

---

### Post by chrisinspace on 2009-07-29
> **P_Aleksandrov said:**
> I forgot to say that I don't want to install any desktop environment on it. I want to install only samba and telnet servers (to access floppy disk drive and so on).

Then just use the Ubuntu server installation disk.  The Alt installation disk still installs a DE, it just uses a more basic* installer to get there.  If you use the server disk, when the installation completes you will only have the cli unless you explicitly install a DE.

* "more basic" as in, not as graphical.  It is still fully functional.

---

