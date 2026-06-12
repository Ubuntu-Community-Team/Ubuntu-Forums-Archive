---
title: "USB Ports on Monitor Are Non-responsive"
date: 2011-05-18
forum: Hardware
---

### Post by charliemagiera on 2011-05-18
As the title states, I have USB ports on the side of my monitor that are non-responsive.  The display on my monitor is fine, and the NVIDIA X Server detects the monitor and resolution flawlessly; however, I can't seem to find any drivers or packages to correct this issue.  My monitor is a Dell 1704FPV.  

My installed programs are up-to-date.  Am I missing something?  Is there a package from the repositories I may need to install?  Please let me know.

BTW, I am running Maverick from a clean install from a disk.

Thank you all.

---

### Post by Joe of loath on 2011-05-18
The USB ports are simply a hub, is there an extra wire that needs to be plugged in?

If that wire is plugged in, does lsusb find it?

---

### Post by Gelatinous Yam on 2011-05-18
Are you sure it's not the monitor's problem? I have a monitor on a basic windows vista computer where the USB ports don't work, just because of bad wiring. If you have any non-buntu computers you may as well test to make sure that the problem isn't in the monitor itself.

---

### Post by charliemagiera on 2011-05-18
Both questions are of valid looking into.  I haven't checked to see if the monitor requires a "jumper", and until I do that, I cannot ascertain whether or not it's a wiring problem.  But I will check both.  Thank you for a place to start looking.  Other replies are still welcome.

---

### Post by charliemagiera on 2011-05-18
OK, I feel stupid now.  I found the documentation for this monitor online, and found I need an upstream cable to get the downstream ports to work.  I just need that cable before going any further in the diagnosis.  I just didn't think simply enough.  Time to start employing the KISS method for troubleshooting.

---

