---
title: "Mouse clicks stop working in certain places on screen"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by Jethro_uk on 2009-11-03
upgraded to 9.04. Pleased everything went smoothly. BUT ... after a few days, a problem with my wireless USB mouse (which works 100% when I boot windows, so it's not batteries or hardware). The mouse moves, but some clicks just don't respond. it's weird because I can't click the main menu, but the toolbar icons in FF work. But I can't close FF, as the "X" in the corner (and the main menu) ignore the mouse. Also hyperlinks don't respond.

Currently my machine is unusable ... can anyone suggest where to start ?

I can log into a terminal (ctl-alt-F1) so can run stuff there, but I am not a guru.

---

### Post by Jethro_uk on 2009-11-17
> **Jethro_uk said:**
> upgraded to 9.04. Pleased everything went smoothly. BUT ... after a few days, a problem with my wireless USB mouse (which works 100% when I boot windows, so it's not batteries or hardware). The mouse moves, but some clicks just don't respond. it's weird because I can't click the main menu, but the toolbar icons in FF work. But I can't close FF, as the "X" in the corner (and the main menu) ignore the mouse. Also hyperlinks don't respond.

Currently my machine is unusable ... can anyone suggest where to start ?

I can log into a terminal (ctl-alt-F1) so can run stuff there, but I am not a guru.


Have identified this along with a few others as a definite bug [https://bugs.launchpad.net/ubuntu/+source/logitech-applet/+bug/375905]("https://bugs.launchpad.net/ubuntu/+source/logitech-applet/+bug/375905"). Sadly no fix

---

### Post by Jethro_uk on 2009-12-02
After a while playing with this problem, I have got it down to be an annoyance, rather than a showstopper.

Not being a Linux guru, my opinions are of limited value, but I firmly believe this is an X-Server/XOrg problem. I've seen it happen under GNOME and KDE, and with all combinations of window managers, and decorators.

There appears to be a connection with ALT-TAB ... as soon as the mouse focus issue happens, you lose ALT-TAB.

Anyway, I have discovered that if I activate ALT-TAB as soon as I login, it seems to "protect" my system, and I don't seem to lose mouse focus.

I have also discovered, that CTL-ALT-D (show desktop) seems to recover mouse focus ... once all windows are minimised to the taskbar, then ALT-TAB seems to work again, and mouse focus is restored. Hopefully this workaround will prove useful to people, and can remove the need to logout/login again, or to restart the machine with the loss of data that implies.

---

### Post by Jethro_uk on 2009-12-23
Having lived with this problem for a few weeks now, I believe I can have a stab at suggesting what is going on, and the intermittent nature of the bug.

I *think* that when GDM starts (after I login), some process somewhere starts up, and creates a window. I have read various reports that it's possible to create a window which does not appear in the panel area. This window then steals focus. Because it's hidden, you can't switch to it to close it. From that point on, you're stiffed.

I've read a lot about the modified behaviour of the update manager/notifier, and I would like to propose this as the app which is killing mouse focus.

I'm researching ways to kill it so it never starts ...

---

### Post by agalindo on 2010-01-06
tagging along, have the same problem.

---

### Post by johansson on 2011-01-04
Agalindo, posted a response in Jethro's other thread: [http://ubuntuforums.org/showpost.php?p=10313490&postcount=22](http://ubuntuforums.org/showpost.php?p=10313490&postcount=22)

Basically though I switched my mouse and it fixed itself.  Old mouse that was giving me a poblem works fine in Windows XP.

---

