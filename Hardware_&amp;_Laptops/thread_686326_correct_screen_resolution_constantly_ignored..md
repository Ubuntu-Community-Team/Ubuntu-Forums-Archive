---
title: "correct screen resolution constantly ignored."
date: 2008-02-03
forum: Hardware &amp; Laptops
---

### Post by mättu on 2008-02-03
Hi folks

This is a compaq Evo n880v running xubuntu gutsy. It has an ATI Mobility Radeon 7500 (unsupported by fglrx)

Problem: Screen resolution (which should be 1400x1050) is reset to 1280x800 every time X is restarted even if I
- can reset it manually inside X (using this new "screen"-GUI in Settings) to 1400x1050
- edit xorg.conf to what I think must be correct
- replace xorg.conf with xorg.conf from feisty (which worked there, but does not under gutsy)
- run dpkg-reconfigure xserver-xorg and get results I think are correct

Grrr! Since in old times when I had to manually edit xorg.conf under the at these times testing debian sarge, my monitor always and automatically displayed at nothing else but 1400x1050. (debian sarge, edgy, ubuntu breezy, dapper, feisty)
Even if they misinterpreted the card as Mobilty Radeon 9000, there was never a problem with the screen resultion..

I've read many threads about wrong refresh rate, ati & fglrx-drivers, tested & tried.

To make it short: I could manually adjust my screen resolution via this cool fresh tool under "settings", but it seems quite inappropriate.

In the hope that a I overread a simple solution anywhere on these forums or the internet, I post this.

:m(

---

### Post by Yellow Pasque on 2008-02-03
Does this command change the resolution?:
```
xrandr -s 1400x1050
```
If so, put it in a script that runs when X starts, maybe /etc/init.d/x11-common

EDIT: Ok, I guess this is more of a workaround than a fix, but if you really want to find the cause, try looking in /var/log/Xorg.0.log for clues

---

### Post by mättu on 2008-02-03
thanks! this works manually, but as soon as I log out, I'm back at 1280x800.
Doesn't work at startup either..

/var/log/Xorg.0.log:

snip

(II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)

/snip

there are lots of other messages.. I'll post back as soon as I'll find out what to do.

First of all I'm considering reinstalling feisty.

:m)

---

### Post by Yellow Pasque on 2008-02-03
Post your /etc/X11/xorg.conf file

---

### Post by mättu on 2008-02-04
Thanks for your caring & help!

Anyway I gave up on gutsy and reinstalled feisty, which was by far a faster procedure. ;-)
As I can see, there are many related bugreports, so the issue will hopefully be fixed in hoary (LTS!)

Sidenote: I installed using UNetbooting from lubi.sourceforge.net. Very cool, as it offers an alternative to the constant burning & throwing away of CD's. The only downside is that one has to use the "non-graphical" installer. But then this can be an "upside" as well, because it's faster and asks more precise questions.

:m)

---

