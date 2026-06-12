---
title: "An error occurred: Invalid argument [Errno 22] while installing inside Windows. Ubunt"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by meouy on 2009-05-02
WinXP: While installing Ubuntu 9.04 Jaunty Jackalope Release i386 from CD and choosing to install it "inside Windows" I get > An error occurred: Invalid argument. For more information, please see the log file:The error in the log file seems to be ERROR  TaskList: [Errno 22] Invalid argument; that's just the first error I see in the file so I'm assuming it's the relevant error. I've tried installing on both my C and D drive and as Administrator. Can anyone help? Screen shot of error and system specs [here]("http://imgur.com/2SL4b.png"). Log file [here]("http://pastebin.com/m542221b9")

edit: It works fine if I copy the wubi.exe (rev 128 ) from the CD onto the hard drive and run ```
wubi ubuntu-9.04-desktop-i386.iso
``` from the hard drive. Perhaps it downloads newer scripts when run from the hard drive rather then using the scripts on the CD and that fixed the problem.

---

