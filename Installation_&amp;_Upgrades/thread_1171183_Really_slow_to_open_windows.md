---
title: "Really slow to open windows"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by timswait on 2009-05-27
I've just upgraded to Jaunty from Intrepid. Had initial problems with my older ATi card not being supported but am now using the open source drivers and it seems OK. 
The problem I'm getting now is that opening a file browser window from most applications (for example Open/Save As, Export, etc in GIMP or Open Office, or where to upload a file from in Firefox) is really really slow, as in nearly a minute. I don't have any visual effects enabled. Odd applications which have their own style file browser windows, not the standard Ubuntu type one, for example Lyx open it almost instantly. What's wrong here, it was fine on Intrepid?

---

### Post by hal8000 on 2009-05-27
Do you have a copy of your old Intrpid xorg.conf file?

It may be a different option or module in the conig file that Intrpid was using.

Another suggestion:
Try boooting with the live jaunty CD, is it still slow at opening windows? If it works ok copy the /etc/X11/xorg.conf and compare it with your existing one for comparison.

---

### Post by timswait on 2009-05-27
I didn't intentionally keep my Intrepid xorg.conf file, but I did find what I think from the file name and modified date is a backed up version from when I was running Intrepid. I've attached it and my current one below. I can't boot Jaunty from Live CD as my ATi graphics card is not supported so I get a scrambled mess on the screen after the splash screen.
Cheers

---

### Post by timswait on 2009-05-28
I think Tracker may have been causing the problem. I also kept getting a dialog box up from Tracker saying the index was corrupt, which wouldn't go away whichever box I clicked. Anyway I uninstalled tracker and it's made things much faster, although I'm still not sure it's as fast as it was under Intrepid. Would a fault with Tracker be likely to cause this?

---

