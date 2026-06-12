---
title: "Nvidia drivers / resolution problems"
date: 2009-03-21
forum: Hardware
---

### Post by dn* on 2009-03-21
I've been running Intrepid for a while at 1280x1024. My monitor supports it as does my 8600 GT graphics card.

This morning I turned on Ubuntu to find that the resolution was stuck at 1024x768. The 'Screen Resolution' application doesn't list anything higher than 1024x768.

I'm using the 180 nvidia driver.

Any help GREATLY appreciated.

EDIT:

I would also like to mention that as a solution I was going to install Alpha 6 of Jaunty but the problem is in there too. I'm not sure exactly what that means in terms of sourcing this bug.

---

### Post by dox_drum on 2009-03-21
I have the same problem.

If I go to **System --> Administration --> Nvidia X Server Settings**, the resolution can be changed, but once I log out... the configuration is lost.

When I thy to do **Save to X Configuration File**, it says **Unable to remove old X config backup file '/etc/X11/xorg.conf.backup'.**

Any Ideas?

Thank you very much.

---

### Post by dn* on 2009-03-21
I get the same error as you in the nvidia settings gui but I have been able to temporarily get the resolution up to 1152x864 (but I need 1280x1024).

---

### Post by MartijnV on 2009-03-21
You have to start nvidia-settings with administrator privileges to save your settings.
Open a terminal and type: sudo nvidia-settings (press enter)

---

### Post by dn* on 2009-03-21
Yep I worked that out a minute ago.

I still have the problem that nvidia-settings does not list the resolution I need.

Any thoughts?

---

