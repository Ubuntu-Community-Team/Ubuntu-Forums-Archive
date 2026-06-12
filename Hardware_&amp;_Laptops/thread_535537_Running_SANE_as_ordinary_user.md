---
title: "Running SANE as ordinary user"
date: 2007-08-26
forum: Hardware &amp; Laptops
---

### Post by darenw on 2007-08-26
Running Ubuntu 7.04 with a  Samsung SCX 4100 printer/scanner/copier attached by USB.   Installed latest driver from Samsung, no problems.  Printing works fine.  Been trying to get scanning to work.  Finally got it going, sorta, following the howto by Elijah Lofgren.   xsane, xscanimage run okay as root (sudo, actually) but segfault if run as plain ordinary user.  I'm assuming i should be able to.

Saw old forum posts saying to chmod 755 certain files, but these are already 755.  Also tried advice to chmod +s xsane, but when i try xsane as ordinary user, get a gtk gripe.  

(process:8179): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    [http://www.gtk.org/setuid.html](http://www.gtk.org/setuid.html)

(which leads to some mumbo-jumbo about setuid and gtk but no clear easy solution)


Minor side issue:  oddly, sane-find-scanner reports no scanners found, even if run as root.  It's living in a different world than xsane.   As long as xsane can run somehow, i'll ignore sane-find-scanner.

---

### Post by ddrichardson on 2007-08-26
The mumbo jumbo is just saying to use something like gksudo that's all. There's quite a good howto [here]("http://www.howtoforge.com/sane_xsane_scanner"). I'd ```
sudo chmod -s xsane
``` first though.

---

### Post by darenw on 2007-08-26
so, the solution to avoid running xsane as root is....to run it as root!

---

