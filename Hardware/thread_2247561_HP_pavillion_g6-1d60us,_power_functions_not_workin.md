---
title: "HP pavillion g6-1d60us, power functions not working"
date: 2014-10-08
forum: Hardware
---

### Post by CYzMLcT on 2014-10-08
Hello,
I am installing ubuntu on a freind's laptop (HP pavillion g6-1d60us), and a number of issues have appeared. To start with, I am installing 14.04.1 onto a blank hard drive (previous hard drive with win7 blew up) I have reinstalled twice, so that is not a fix. now, the issues:
[LIST]
[*]will not shut down. setting "acpi=force" in grub fixed this _until_ I installed updates in one of the previous installs, but now I cannot get the computer to shut down even with this. note: system gets to the point where it reports "will now halt" and then hangs
[*]screen would not turn on after anything turned it off, this was fixed by installing proprietary amd graphics drivers [SOLVED]
[*]after each install, I could access power settings easily and the battery icon was visible, but after 1-2 restart cycles the icon would disappear and any attempt to access the power settings (from system settings or the dash) would result in waiting a long time (in the case of system settings the window was greyed out) and then power settings would appear, but with most of the options missing. at the same time this happened, the font in the clock and some other menus would change from the usual font to a smaller font that did not fit the space it was in very well (some kind of fallback?)
[*]suspend does not work, the screen blinks on and off and then ends up at the lock screen
[/LIST]

Do these symptoms indicate anything to you that could be the source of all of these problems? if not I will continue to attempt to solve them individually, but it is odd that all these problems appeared on the same computer at the same time, as I have installed ubuntu on a number of other machines with no difficulties. any help withany of this would be greatly appreciated.

---

