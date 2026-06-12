---
title: "Distorted console output on Nvidia GTS 250M"
date: 2010-02-10
forum: Hardware
---

### Post by MikeZ83 on 2010-02-10
Hello

Whenever I switch from a graphical session to a console output (e.g. moving to a different tty) the result is a distorted image almost like an old CRT monitor during a cell phone call but much finer. This makes it extremely hard to read what's actually on the display.

The same problem occurs if I lock the screen, try to suspend the system or during shutdown (once the system returns to the console output). The distortions also remain if I switch from the default Gnome to another tty and back again (making the GUI-based output extremely hard to read as well).

Gradually upgrading from 185 through 190 and to 195 didn't solve the problem either during any step. Since the problem first occurred after a vanilla install without anything but the pre-installed stuff and the pending updates I assume it might have happened to more people.

There was one post about something similar where suggested it might be related to the horizontal sync but they never mentioned any solution. The hsync was also mentioned as fixed in one of the 190's changelogs in relation to this chip but apparently still occurs in some form.

I mainly use the Windows install for graphics work when I'm not at home but since I'd also like to use Ubuntu for app development (J2EE, general J2ME, Android and maemo) it would be really great to get rid of this problem.

A few specs:
18.4" Toshiba Qosmio X500-10U with 6GB DDR3 RAM
 Nvidia GeForce GTS 250M with 1GB dedicated video RAM
Ubuntu 9.10 Karmic Koala amd64 with all the latest updates

Does anyone else have a similar problem?
Any ideas on how it might be solved?

Thanks in advance for your replies.

---

### Post by unclebeer on 2010-02-11
Ditto on the old tv effect-
Like the OP, it happens whenever you switch to console mode or log out of gnome.

Qosmio X505-Q860
4GB DDR3
1GB Geforce GTS360M
Ubuntu 9.10 x86

---

### Post by MikeZ83 on 2010-03-02
One of the recent updates seems to have fixed the problem.

Switching between to another tty now works like a charm, same as hibernate/suspend/shutdown handling.

---

