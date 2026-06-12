---
title: "[SOLVED] Vertical flickering lines down monitor!!  Please help!!"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by Slimo on 2007-08-16
I am running Ubuntu Feisty with a Radeon 9800 graphics card and a Philips 107S 17" CRT monitor.  I have had display problems before but they appeared to be fixed after I changed to the open source ati drivers.

However the other day after about 10 minutes use about 5 or 6 thick flickery vertical lines appeared on my monitor.  I could still use my computer but could only see the desktop in between the flickering lines.

Would this suggest that it is a hardware (monitor) fault rather than Ubuntu?  My monitor is about 5 years old and I am looking to replace it shortly.

Has anyone else had similar problems?  I have searched the forums and some people suggest changing the refresh rates and resolutions but so far that has not worked for me!

Please help!  I have had so many Ubuntu problems lately!!

---

### Post by ddrichardson on 2007-08-16
It sounds more like an incorrectly configured modeline in xorg.conf although they're usually many thinner lines. If it happens in multiple resolutions I'd been inclined to think the CRT deflection plates are on there way out.

---

### Post by Slimo on 2007-08-30
Thanks again for all your input.  The problem has been solved.
The fan on my ATI card had stopped working so after a few minutes of running the computer the card would overheat and fail, causing the lines down the screen.  This has been remedied by getting a new (nVidia) card and a bigger power supply  :-)

---

