---
title: "Canon S750 printer problems"
date: 2012-08-02
forum: Hardware
---

### Post by shvman on 2012-08-02
I had been using a Canon s750 printer with Ubuntu 11.10 32 bit.  Since there was no s750 driver, I used the s800 (CUPS+Gutenprint v5.2.7 Simplified).  All was well.

Then I loaded Ubuntu 12.04 on a desktop (64 bit version).  A driver for the s750 was shown in the printer setup so I thought all would be well.  The driver, CUPS+Gutenprint v5.2.8-pre1) did not work BUT the Canon s630 Foomatic/bj8XXYYZ.upp worked fine.  Great.

Everything is going along great, but then yesterday (8/1/12) I got several updates.  I noticed that one update said something about CUPS.  Not thinking much about it, I clicked "install updates".  Well, every since then, my s750 is broken.  It feeds the page about half way, backs up the page slightly, then feeds the page through the printer without printing.  None of the drivers work this time, not even the s630 Foomatic.  

I'm at a loss.  I'd really like to get my printer function back soon.  Any help will be most appreciated. 

Thanks.
This is what I see in my CUPS error log:
W [02/Aug/2012:07:59:18 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'S750-Gray..' already exists
W [02/Aug/2012:07:59:18 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'S750-RGB..' already exists
W [02/Aug/2012:07:59:18 -0500] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-S750' already exists
W [02/Aug/2012:08:22:05 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'S750-Gray..' already exists
W [02/Aug/2012:08:22:05 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'S750-RGB..' already exists
W [02/Aug/2012:08:22:05 -0500] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-S750' already exists
W [02/Aug/2012:08:22:05 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'S750-Gray..' already exists
W [02/Aug/2012:08:22:05 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'S750-RGB..' already exists
W [02/Aug/2012:08:22:05 -0500] failed to CreateDevice: org.freedesktop.ColorManager.AlreadyExists:device id 'cups-S750' already exists
W [02/Aug/2012:08:23:21 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'S750-Gray..' already exists
W [02/Aug/2012:08:23:21 -0500] failed to CreateProfile: org.freedesktop.ColorManager.AlreadyExists:profile id 'S750-RGB..' already exists

---

### Post by shvman on 2012-08-06
The most recent update fixed this.....thank you to all responsible....

---

