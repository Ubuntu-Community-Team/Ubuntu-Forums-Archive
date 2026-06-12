---
title: "Interrupted release upgrade and broken AMD driver install"
date: 2014-03-17
forum: Hardware
---

### Post by wsaleem on 2014-03-17
I seem to have broken my system hard.
It started with me wanting some Compiz effects. I have a Dell Inspiron 14z with a AMD Radeon HD 7570M card. The card showed up in the output of lspci but not in Ubuntu's system details. I had earlier installed drivers for my card about a year ago from AMD's website which had solved this problem then. However, it seemed to have reappeared. Expecting better support from a newer Ubuntu version, I decided to do a sudo do-release-upgrade but canceled it midway with Ctrl-C because the upgrade was taking very long due to Internet problems. I think that is where the real problem starts.
Because of the unfinished upgrade, my repositories were in a state of flux. Not realizing, I proceeded to install drivers following the instructions [here]("http://wiki.cchtml.com/index.php/Ubuntu_Quantal_Installation_Guide"). I then realized that I was following the page for the wrong distribution so I cleaned up the software repository list through Synaptic and switched over to [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide").
I encountered problems with some packages being newer than others and managed to downgrade some using aptitude. For example, I ended up with different versions of libgl1-mesa-dri and libgl1-mesa-glx but the install went through so I figured everything is okay.
Since the restart, I have been encountering the "System is running in low graphics-mode" error. I have spent the past two hours trying all the fixes suggested [here]("http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error") but to no avail.
Finally, sudo apt-get install fglrx errors out pointing to /etc/ati/fglrx-uninstall.log which reports that certain files are "missing from system": /usr/share/ati/lib64/libQtCore.so.4, /usr/share/ati/lib64/libQtGui.so.4, /usr/lib/fglrx/switchlibGL, /usr/lib/fglrx/switchlibglx, and others.
How do I recover from this so as to boot normally into Ubuntu?

---

### Post by Carl H on 2014-03-18
I had all sorts of problems with a Radeon graphics card. I posted the solution here:- [http://ubuntuforums.org/showthread.php?t=2210877](http://ubuntuforums.org/showthread.php?t=2210877)

---

