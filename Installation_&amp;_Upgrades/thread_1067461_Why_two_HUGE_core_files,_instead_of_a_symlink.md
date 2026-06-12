---
title: "Why two HUGE core files, instead of a symlink?"
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by dinodana on 2009-02-11
(eeeXubuntu)
Why do we have TWO of the same HUGE system files
("core", 527,962,112 bytes, in /dev AND /lib/udev/devices)
instead of keeping original in /dev
and using a symlink for the other?

Please, let me know if deleting one and using symlink is an option, seems logical, but is logical it would already be done.
So, I am reluctant to try w/o some affirmative opinions.
Searched first, no results in forums. Since I have this phenomenon on BOTH of my laptops, it appears to be consistent.

This is the difference between 527 MB and 1.1 GIGABYTES.
On my EePC 4g, that is a VERY substantial difference!
Any "opinions/been there before" input appreciated
:)

(2 EeePs): EeePC 4g and EeePC 900a
900mhz/1.6ghz, 4gb SSD/12gb SSD
w98/2K/eeeXubu, w98/2K/solaris/eeeXubu

---

### Post by snova on 2009-02-11
On my system, both are symlinks to /proc/kcore.

But here's a better question- how much memory do you have? :D

If you notice an interesting coincidence, that's because these files do not actually exist. But if you had sufficient permissions to read from them, and did so, you would end up reading the contents of your memory.

---

### Post by dinodana on 2009-02-12
Kcore? Wouldn't that be a KDE core file? EeeXubu is Xfce. Anyway, answering, one has 1gb RAM, the other has 512mb. But both have the same two files/sizes. But this was right after (1st boot) some APT upgrades, so maybe it was a temp situation... But sim links are usually "zero bytes" (directory existence only). I will check anyway, because what is true on yours is more likely than not, true on mine. The look/feel may differ, but most Nix has more in common that differs. Thanks for idea. Will amend this if your theory resolves this.

---

### Post by snova on 2009-02-12
> **dinodana said:**
> Kcore? Wouldn't that be a KDE core file?

K is usually the tip off for KDE... unless, of course, it means Kernel. :)

[What is /proc/kcore?]("http://www.unixguide.net/linux/faq/04.16.shtml")

> But sim links are usually "zero bytes" (directory existence only).

Actually, symlinks are as long as the path they point to.

(Really technically, in the ext2/ext3 filesystems, if the path is short enough it is stored in the inode itself, and takes up no disk space at all. Longer than that, and it uses up a block.)

---

### Post by dinodana on 2009-02-14
Snova: You were absolutely correct. They are both (actually, I found three, at one time, but not now) links, pointing to target: /proc/kcore and identified as "link to program crash data". So I was worried over wasted space that did not exist -except in RAM. Darned if I can figure out why the other 1gb laptop showed up iniitailly with 512mb, too. Maybe RAM reference was split that first reboot while the new software was being configured. Regardless, mystery solved, no alarm at all. Thanks everyone. Unless this might serve as an archive for others who think they are losing HD space, we could kill this thread.

---

