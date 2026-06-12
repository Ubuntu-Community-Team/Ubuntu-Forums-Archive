---
title: "Ubuntu 7.04 laptop install problem - no environment after user login"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by asutic on 2007-06-20
Hi.

I successfully installed Ubuntu 7.04 on an HP Pavilion ZX5078CL laptop. However, after user login, I don't get anything except empty desktop screen. There are no icons, nor start menu. The screen is completely empty and only mouse cursor is available.

I tried different login sessions, but only 'Failsafe Terminal' is working, of course.

Did anybody have similar issue with this laptop or any other laptop? LiveCD booting went as expected and no issues existed. I installed Ubuntu 7.04 on an HP desktop machine without a single problem. It seems that laptop installation a\can cause problems. 

Thanks in advance for any help. I'm novice to Ubuntu distro (Fedora user).

---

### Post by scrooge_74 on 2007-06-21
Maybe try another window manager to see if that helps

---

### Post by asutic on 2007-06-21
Hi.

It looks like the problem is identical to [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/40176](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/40176). However, from this thread I didn't figure out how to fix the issue. Could anybody comment on this?

In case I plug the A/C power supply, everything works correctly. The issue exists for battery mode only. In case esd is turned off, GNOME starts properly.

KDE session can be initialized for both A/C and battery modes.

Regards.

---

### Post by scrooge_74 on 2007-06-21
But it is a bug mostly for Dapper, which version you have at this time?

---

### Post by asutic on 2007-06-22
> **scrooge_74 said:**
> But it is a bug mostly for Dapper, which version you have at this time?

I've installed Feisty Fawn, with the latest software updates. The existence of the issue is quite strange since I expected that this sound-battery conflict has been fixed.

---

### Post by FrancoNero on 2007-06-22
[http://ubuntuforums.org/showthread.php?t=480841&highlight=login+no+gnome](http://ubuntuforums.org/showthread.php?t=480841&highlight=login+no+gnome)

does that help?

---

