---
title: "my Compal CL56 won't come out of suspend"
date: 2005-05-09
forum: Hardware &amp; Laptops
---

### Post by epb613 on 2005-05-09
Hi:

I'm trying to suspend to RAM on my cl56. I have tried doing it by typing sudo /etc/acpi/sleep.sh and by typing echo 3 > /proc/acpi/sleep and by trying a bunch of other commands I have seen posted. Everytime, it goes into suspend fine, but when I hit space bar to wake it up, I hear everything spin up but nothing displays on the screen. Same thing happens when I press the power button to come out of suspend - I hear the harddrive spin up but the screen stays blank.

I'm running the newest version of ubuntu and also I'm using the fglrx ATI drivers if that makes a difference.

If anyone has any advice I would appreciate it. Thanks, Pinny.

---

### Post by epb613 on 2005-05-10
anyone have any clue?

---

### Post by epb613 on 2005-05-12
anyone?

I actually made some progress by installing Klaptop. Using klaptop I can get it too resume by pressing the power button. However this causes it to reboot as soon as it comes out of suspend. I tried disabling the powerbutton from rebooting (by renaming /etc/acpi/powerbtn.sh to something else) but after doing that, it made the power button behave like any other button - pressing it makes everything spin up again but nothing displays on the screen.

Also with klaptop, when I resume from hibernation, the screen reappears but I can't move my mouse or type anything.

---

### Post by circussideshow on 2005-05-16
I just tried that command to sleep my CL56, and it just went to the next line and did nothing... I'm not much help I guess. :?

---

### Post by hyperboloid on 2005-06-06
I'm having similar problems with my Thinkpad.

Ubuntu is great for a desktop, but suspend/resume sucks, it seems.

---

