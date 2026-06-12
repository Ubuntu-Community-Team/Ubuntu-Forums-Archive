---
title: "Mouse needs to be kick-started"
date: 2013-09-15
forum: Hardware
---

### Post by WB0HYQ on 2013-09-15
I have asked this before, but not with much success, so I'll try yet again.

About 50% of the time when I boot up Ubuntu (latest supported version), the mouse will refuse to move.  I am not at all familiar with the hardware commands that can be issued within a terminal window.  What I am looking for is a command I can enter after opening a terminal with Ctrl-Alt-T that will allow me to restart the mouse driver.

Previously, I did everything suggested, and some of them were pretty radical, but there has to be a simple LINUX command similar to the Windows Device Manager that allows a reload of the driver for the mouse.  I.E.: Uninstall, search for new hardware, reinstall driver.

Can anyone suggest such a command?

Bill

---

### Post by buzzingrobot on 2013-09-16
More information would be helpful.

What kind of hardware do use?

What kind of mouse?  How is it connected? Wired USB? Wireless?  Bluetooth?

---

### Post by ibjsb4 on 2013-09-16
Try restarting dbus next time it happens.

[http://ubuntuforums.org/showthread.php?t=2007349&p=12042161#post12042161](http://ubuntuforums.org/showthread.php?t=2007349&p=12042161#post12042161)

---

### Post by WB0HYQ on 2013-09-16
@Buzzingrobot:  Sorry about that.  I gave so much information on my first thread I forgot to add it here.

desktop running latest Ubuntu, with PS2 wheel mouse (M-S48).  As I said, sometimes it works, but it usually doesn't and I either keep rebooting until it does or give up and return to Windows.  EDIT:  The system is 64-bit, if that makes any difference.

@ibjsb4: I'll give that a try, but the thread you linked to shows problems with restarting dbus, so I will be prepared for that.

Thanks for the replies,

Bill

---

### Post by ibjsb4 on 2013-09-16
> **WB0HYQ said:**
> @ibjsb4: I'll give that a try, but the thread you linked to shows problems with restarting dbus, so I will be prepared for that.

Yep, for what its worth, it does work in 12o4.

---

### Post by WB0HYQ on 2013-09-16
In the manner of computers that I have become accustomed to in 50 years, I have rebooted six times and never once did the mouse fail.  Sigh.

I'll keep the advice in mind when/if it fails again.

Thanks,

Bill

---

