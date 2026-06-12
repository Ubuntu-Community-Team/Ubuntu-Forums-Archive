---
title: "Machine just stops"
date: 2007-04-17
forum: Hardware &amp; Laptops
---

### Post by dday376 on 2007-04-17
I have a fresh install of Edgy on an old Compaq Presario.  I have used this machine on and off for various purposes over the years.  Anyhow, I did a fresh install last week, and I was out of town over the weekend.  When I returned, the machine was unresponsive - screen blank, nothing, but it was still powered up.

I've rebooted, but cannot find anything in the logs to indicate why it stopped.  I checked syslog, and can see the last message before my reboot was on Apr 16 @ 22:00 hrs (it was just the --MARK-- entry).  I grepped the other logs for that time, but nothing to show an error.  It's as if the machine were just shut off (but it wasn't).

No power failures while I was away either.  I have a second machine next to it running just fine, both are on battery.

I suspect a hardware problem - can anyone give me ideas on how to see if maybe the old video card in it is the culprit (short of replacing it, which I'll try if I can't figure anything else out).

Thanks!

---

### Post by earobinson on 2007-04-17
could you post your logs?

---

### Post by computerease on 2007-04-17
This is in no way a solution to your problem but useful if the problem is recurring and intransigent and likely useful for further diagnostics.  Will pressing Ctrl-Alt-F1 or F2 yield a prompt terminal?  I have had a similar problem after having done installs and other configurational modifications and then leaving the machine running over night (M$ will do the same thing, but with no viable solution but a reset boot).  If you get a prompt screen you can log in and then (with the same username and password as with the GUI)

sudo shutdown -h or -r now

to at least get an orderly shutdown and/or reboot.  The disorderly shutdown route seems to leave one with the possibility of a drive corruption or a Gnome corruption from which recovery can, at times, be difficult (particularly the latter).  If you CAN get the terminal screen, the issue is not that the machine has stopped but that the interface will not come out of its screensave or sleep mode.  I haven't a clue why that happens in a Linux distro but when it happens with M$ it is usually because there are too many screen saving and power saving mechanisms activated, namely the BIOS is doing power and screen saving and the OS is doing it as well.  With M$ one or the other of these "saviors" is intercepting the wake-up signal and the other never gets it so everything stays dormant.  With M$ one wakeup call is all you get.  Maybe it's that way with Linux as well.  If so, the M$ analog is of use.  If not ...good luck on a solution.

---

### Post by dday376 on 2007-04-18
computerease - the machine is completely dead.  cannot ssh into it, does not respond to a ping, nothing.   I appreciate the recommendations, though.

earobinson - log files attached.  I think I got the critical ones - let me know if I missed one.

Thanks!
- dday376

---

### Post by dday376 on 2007-04-21
I've figured out it is completely a hardware problem.  This machine is prone to freezes due to various reasons (overheating being the main culprit).  The machine is a compaq presario 5000 series (5WV254).  Old machine.  Googling showed me that people have problems with them as they get older regardless of OS.  I'm giving up on it.

If a moderator sees this, please feel free to close this thread.

---

