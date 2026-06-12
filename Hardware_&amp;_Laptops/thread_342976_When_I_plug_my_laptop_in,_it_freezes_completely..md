---
title: "When I plug my laptop in, it freezes completely."
date: 2007-01-20
forum: Hardware &amp; Laptops
---

### Post by AlucardZero on 2007-01-20
Four times now I have had my laptop unplugged, plugged it into the wall, and it has frozen completely.  No response to any keypresses, including ctrl+alt+f1 and ctrl+alt+bksp.  I have to turn it off by holding down the power button.  This has begun happening every time I plug it in while the system is running; booting up plugged in seems to be ok.

I'm using 6.10, XFCE, and gnome-power-manager.  Kernel version is 2.6.17-10, and it's a Thinkpad R60.  It used to work just fine, and I haven't changed any power-related settings since well before it stopped working.  I don't have any special acpi parameters passed on boot.

There's nothing in /var/log/syslog, just a notice that cron.hourly was running, then 14mins later (when I turned it back on) a mark that Ubuntu is restarting.

Anywhere else to look for error messages?  Anything to try to prevent this from happening again?  Any more information needed?

Thanks for your time.

---

