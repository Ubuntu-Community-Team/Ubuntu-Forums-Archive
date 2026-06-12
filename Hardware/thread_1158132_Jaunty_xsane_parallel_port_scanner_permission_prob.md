---
title: "Jaunty xsane parallel port scanner permission problem?"
date: 2009-05-13
forum: Hardware
---

### Post by CEB2nd on 2009-05-13
Since installing (clean install) Jaunty 9.04 my parallel port flatbed scanner isn't detected when xsane is run as a normal user, it is only detected by Jaunty when xsane is run as root in terminal. I uncommented the same lines in dll.conf and mustek_pp files in Jaunty that enabled Hardy to detect the scanner. The scanner 
still only works when run as root, I didn't have this problem with
Hardy 8.04. There isn't a scanner option in user permissions list
in Jaunty, so I temporarily enabled all options to see if it would cure the problem, it didn't. I am triple booting my system--Jaunty 64 bit, Hardy 32 bit and Win XP 32 bit. When I boot to Hardy the scanner will still work as a regular (non-root) user, so I guess there is a permissions problem with Jaunty. The scanner is a Mustek 600 EP III. If I open terminal and enter "gksu xsane" the scanner is detected by Jaunty 
and works properly. Thanks in advance for any help!

On edit:
I found [this]("http://www.xs4all.nl/~ljm/SANE-faq.html#48") in Sane FAQ, looks like I will just have to live with it and run the scanner as root from terminal.

---

### Post by CEB2nd on 2009-05-13
Bump

---

### Post by CEB2nd on 2009-05-14
One last bump.

---

### Post by CEB2nd on 2009-07-23
After a lot of searching, I found this [_thread_]("http://ubuntuforums.org/showthread.php?t=1008227") that cured the problem.

Opening terminal and entering:

sudo usermod -a -G lp *username*

solved the problem in Jaunty.

Thanks leospart!
=D>__

---

