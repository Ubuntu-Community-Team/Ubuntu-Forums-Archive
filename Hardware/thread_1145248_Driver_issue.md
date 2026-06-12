---
title: "Driver issue"
date: 2009-05-01
forum: Hardware
---

### Post by dE_logics on 2009-05-01
This is my complete problem - 

Chipset ATI RS690 (or 690G...the opensource driver docs claim it to have full 3-d support, which doesn't seem so) which comes with x1270 graphs chip.

Ubuntu 8.10

There were no radion drivers installed in the OS initially (there was an ATI driver wrappers though), problem was I could not see any video (forget 3-d)...or actually nothing was happening except the desktop effects getting enabled and very slow.

I also tried the proprietor drivers, but they did not work...they gave flicking videos.

Then I reinstalled ubuntu and upgraded the driver wrapper (which came pre-installed), apart from that I also installed the radion drivers this time; this result in videos getting played properly and 3-d rendering, but the 3-d rendering was very slow, so were the desktop effects (even the simple GUI was very slow).

I also tried the HD drives after reading this article

[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)

And realised this article was crap.

I also tried this -

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

And it was also crap.

In the above 2 links, they ask to modify the xrog.conf file, after which every rendering stops (and I boot into commandline)


Then I came across this article -

[http://www.phoronix.com/forums/showthread.php?t=9951](http://www.phoronix.com/forums/showthread.php?t=9951)

Which also contained the setting of the xorg.conf file which worked perfectly and so my desktop effects and 3-d rendering performance multiplied.

It also explained how to activate the radionHD drivers (which are still installed) but that disables the desktop effects...so HD wont work with my GPU.

Still there are many issues -

1)Performance still a fraction to what it was in windows.

2)3-d rendering issues.

3)Slow GUI (scrolling and all with the desktop effects still being slow)


Aero used to work perfectly with this IGP, so it is of course suffice to handle gnome effects.

I went to ATI's website; yes I tried the x1200 and 1250 drivers (I did this in a separate installation), but that ruined my display.

Dell does not provide such drivers.

The binary drivers (radion) that I've installed claim to have full 3-d support for my chipset.

---

### Post by dE_logics on 2009-05-02
God damn!...no answers yet?

---

