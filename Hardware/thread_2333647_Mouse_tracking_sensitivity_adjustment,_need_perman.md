---
title: "Mouse tracking sensitivity adjustment, need permanent fix"
date: 2016-08-11
forum: Hardware
---

### Post by john_ladasky on 2016-08-11
I love Ubuntu, but one issue has bugged me for years.  In *System Settings > Mouse & Touchpad*, there is no provision for adjusting the mouse sensitivity.  Invariably, I find that the cursor moves much farther than I intend when I slide the mouse.  I am currently using 16.04, but my experience with this problem goes back to at least 12.04.  It exists on multiple computers.

Today, I finally found this (somewhat misnamed) discussion: [http://askubuntu.com/questions/255890/how-can-i-adjust-the-mouse-scroll-speed](http://askubuntu.com/questions/255890/how-can-i-adjust-the-mouse-scroll-speed).  Using the *xinput* shell command, I was able to identify my mouse, and adjust a "Deceleration" parameter to improve the tracking.  It worked!  Until I rebooted.  The excessive sensitivity came right back.

In the short term, I would like to know how I might be able to modify a config file which holds data about the mouse behavior.

In the longer term, I would REALLY like to see Ubuntu's Mouse & Touchpad page include a slider or two to adjust the mouse behavior without having to edit a config file.  This is a significant oversight.

Thanks for any help you can provide.

---

### Post by CatKiller on 2016-08-11
You can put xinput parameters into xorg.conf.

Edit: some info here: https://wiki.archlinux.org/index.php/Mouse_acceleration

---

