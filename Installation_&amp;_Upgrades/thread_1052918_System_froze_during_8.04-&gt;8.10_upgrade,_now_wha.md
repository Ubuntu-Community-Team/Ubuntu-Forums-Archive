---
title: "System froze during 8.04-&gt;8.10 upgrade, now what?"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by Metar on 2009-01-28
Having recently found the way to bypass my lost password, I've fired up my copy of Ubuntu 8.04 yesterday, and started the upgrade to 8.10. After about three hours of download and installation, when the little bar said I had 10 minutes left, my screensaver came up, and this froze my system solid - a bug related to the VIA graphics card's lack of drivers.

That meant that, essentially, I'm stuck with a system that froze in the middle of an upgrade: I couldn't move the mouse, or switch to the terminal. I pushed the restart button on the case, and Grub offers the new kernel - but selecting it only caused a kernel panic. Restart again, and I selected the old one - and it reached the X login screen - but mouse and keyboard wouldn't input anything, even though the buttons themselves worked: I could, for example, switch to the terminal. For some reason, when I tried selecting the new kernel again, it reached the login-screen too, and allowed me to enter my info - but froze in an orange-ish screen afterwards.

Now, my question is: Other than a clean reinstallation, is there a way to complete the upgrade? I tried using apt-get's "upgrade" option, but it gave me dpkg errors much like [**[COLOR="Blue"]these[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1052827") - except that running 'dpkg --configure -a' (under sudo) didn't help, and apt-get still shows that error message.

---

