---
title: "[SOLVED] After latest Kernel update today, usplash no longer works"
date: 2008-10-15
forum: General Help
---

### Post by JerecDrak2 on 2008-10-15
Hey Guys,
As stated in the thread title after today's updates usplash no longer works. There were some nVidia driver problems too (because I had used EnvyNG to update the drivers previously) but I sorted that out. I've tried using ```
sudo dpkg-reconfigure usplash
``` but that didn't work. Any ideas on how I could fix this?

---

### Post by Tanker Bob on 2008-10-15
I also encountered problems with the nVidia drivers after updating the kernel this morning. EnvyNG fixed it nicely as it usually does. Don't know how to fix your problem, but wanted to add my voice to the nVidia driver issue.

When running the recovery boot, I noticed that the nVidia driver installed by the update was a legacy driver set. I don't recall the number (it goes by fast), but I'm sure it had a 2-digit first number. All I got was a black screen with it until I asked the recovery boot to fix the xserver. I tried using the restricted driver setup in Kubuntu, but got the same result. After fixing the xserver again, I booted up normally then and used EnvyNG to fix it.

---

### Post by JerecDrak2 on 2008-10-15
It seems to be a resolution problem, when I edit /etc/usplash.conf and change the resolution to 640x480 I get the loading bar, but for some reason usplash refuses to display at my monitor's native resolution of 1280x1024 anymore. Instead I just get a blank screen where the loading bar would normally be. My resolution is set to 1280x1024 everywhere I can think of...any ideas?

---

### Post by Tanker Bob on 2008-10-15
Are you using the default splash screen for ubuntu or a custom one?

---

### Post by JerecDrak2 on 2008-10-15
It seems the problem was an errant "vga=769" line that the update added to my menu.lst, deleting that line solved my problem:KS

---

### Post by Tanker Bob on 2008-10-15
Cool. Glad that you found it.

---

