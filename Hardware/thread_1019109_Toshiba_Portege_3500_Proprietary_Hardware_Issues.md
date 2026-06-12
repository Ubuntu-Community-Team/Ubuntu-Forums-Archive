---
title: "Toshiba Portege 3500 Proprietary Hardware Issues"
date: 2008-12-22
forum: Hardware
---

### Post by foxmajik on 2008-12-22
Hello,

I used the excellent and free [Wubi]("http://wubi.sourceforge.net/") to install Ubuntu 8.10 the Intrepid Ibex - released in October 2008 on my Toshiba Portege 3500 laptop/tablet convertible.

Initially the screen was limited to 800x600 and it was unuseably slow, however by reading the community forums I was able to find an xorg.conf replacement file that fixed the graphics, allowing me full support of the unit's Cyberblade XP graphics adapter at 1024x768 resolution and much faster redraw rate.

Everything that one would expect to work on any PC works fine and Ubuntu is usable now, however none of the devices specific to the Portege are working:

[LIST]
[*]The stylus does nothing.  The cursor doesn't move when the point or eraser are in proximity of the screen and touching the screen with it does not result in a mouse click event.  I followed the instructions in [this forum post]("http://ubuntuforums.org/showthread.php?t=120369&page=2") but they did not resolve the problem.
[*]I am unable to use the Fn keys because I cannot start the fnfxd deamon that supports them.  I am unable to start it after installing it with Apt because the toshiba_acpi module cannot be loaded.  The module cannot be loaded because it is not included with Ubuntu.  The module is not included because someone decided it would be a good idea to replace toshiba_acpi with tlsup [which is garbage and does nothing useful]("https://lists.ubuntu.com/archives/kernel-team/2008-November/003516.html").  In order to fix this I would have to recompile the kernel manually every time there is a new kernel release, which is far from "human."
[*]Bluetooth doesn't work.  That's okay, Bluetooth is like ice cream in the desert at this point.  I wasn't even expecting it to work.  Hell it barely works in Windows.  This is also a problem because of tlsup being used instead of toshiba_acpi.
[*]Scrolling with the touchpad does not work even though there's a check box for it presented in the mouse control applet.
[*]None of the buttons on the display frame work because there is no support for configuring them.
[*]Rotating the display doesn't cause the screen to rotate according to the orientation of the panel.  It can't be done manually, either.  This is because making that work requires implementation of randr which is incredibly difficult to set up and configure (I know this because [I spent six hours doing it for my desktop machine]("http://ubuntuforums.org/showthread.php?t=682821") which has an nvidia video adapter).
[/LIST]Since Toshiba laptops are pretty common I don't understand why Ubuntu can't detect and properly configure the Cyberblade XP video adapter.  

Also, because tablet PCs are pretty common I don't understand why the stylus and screen rotation can't work "out of the box."  It seems like it wouldn't be too hard for someone with the know-how to implement these things.

**EDIT:**  [Here's a bug that addresses the issue]("https://bugs.launchpad.net/ubuntu/+source/fnfx/+bug/127611") but no one seems to care.

---

### Post by Favux on 2008-12-25
Hi foxmajik,

Try LapTopTesting team's site.  It has toshiba's, not your model however:

[https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba]("https://wiki.ubuntu.com/LaptopTestingTeam/Toshiba")

might find some help in there.

The main thing is what kind of tablet does a 3500 have?  Is it a Wacom?   Serial or USB?  What model?

Loic2 and others are trying to get more tablet support.  There's been a big snafu with introduction of HAL in Intrepid.  Some of this is out of Ubuntu's control.  Some is up to Xorg  and their response to the Linux Wacom Project, etc.

---

### Post by Taneli on 2009-02-23
Hello

I have installed Ubuntu 8.10 on my portege 3500 with wubi too.

I have managed to get both the stylus and the Fn keys to work, the scrolling worked from install for me.

The buttons on the display frame are possible to configure so that all three of them have the same function, for example running some application.

If you haven't managed to get them to work i might be able to help you...

---

