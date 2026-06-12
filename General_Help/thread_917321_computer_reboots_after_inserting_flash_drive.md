---
title: "computer reboots after inserting flash drive"
date: 2008-09-11
forum: General Help
---

### Post by alxlabs on 2008-09-11
Ubuntu 8.04. Computer reboots after inserting flash drive _sometimes_ without any message. Flashdrive itself contains pictures and I can download them if machine does not reboot. It may reboot immidiately after removing flash drive as well. 
What can I do to nail down the reason? Any particular log file to check?

---

### Post by milasch on 2008-09-11
You might have a problem with your usb port or your pendrive... if you short-circuit the usb port your computer can reboot... Does it work 100% perfectly under other environments?

---

### Post by y@w on 2008-09-11
Do other flash drives do the same thing to your machine? Sounds like you've got a short somewhere and it's causing the machine to reset.

---

### Post by alxlabs on 2008-09-11
Short was a first thing I thought about...but same drive works perfectly fine on other machines. Sometimes it resets in the middle of copying files... :(
Any system log to check?

---

### Post by y@w on 2008-09-11
Does it happen with other drives in your machine? This really can only be either a short or *maybe* something weird in your power supply or motherboard. The logs files you could check would be /var/log/messages, /var/log/syslog or dmesg, but I'm guessing you're not going to find anything there except 'running, running, system rebooting'.

---

### Post by alxlabs on 2008-09-11
I checked those log files - nothing conclusive...Must be an unstable hardware in some way....Strange thing that same usb drive is ok in another pc and another usb drive is ok with pc in question...

---

### Post by alxlabs on 2008-09-11
I've got an Idea! I have a usb hub with external power supply - this should rule out (or confirm) power surge part of the issue

---

### Post by y@w on 2008-09-12
That oughta do it. How old is your PC? I had an older PC once that consistently burned up flash drives when you plugged them in to certain slots.. That was a fun one to test ("Hey, my flash drive doesn't seem to work, can I borrow yours?") :)

---

### Post by alxlabs on 2008-09-12
PC - brand new...nothing is made good these days :(
It did not crash with externally powered USB hub, however it didn't crash after that if plug pen drive directly....

---

