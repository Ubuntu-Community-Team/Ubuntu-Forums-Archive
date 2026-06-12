---
title: "Programs unexpectedly quitting"
date: 2008-09-16
forum: General Help
---

### Post by PharmaPhunk on 2008-09-16
I noticed a weird problem that just started happening today. Programs will quit unexpectedly, without any error message. This mostly happens with Firefox, but it happened to avast ant-virus while it was scanning. Weird problem, I don't think it could be a virus or anything. Google doesn't offer much help, although I remember reading somewhere that it could be bad refresh times in the BIOS? Help, suggestions?

---

### Post by Sef on 2008-09-16
What ubuntu version are you running?

---

### Post by PharmaPhunk on 2008-09-16
I'm running the latest version, 8.04 I think?

---

### Post by ryanhaigh on 2008-09-16
You can try running the application from the terminal which may give you more information about the crash that you can use to try and sort out the problem.

To start firefox from the terminal go to applications>accessories>terminal, once open just type firefox and press enter and wait for the crash.

You can do the same with avast although I don't know what the actual command used to launch avast. The easiest way to find out is to right click on the icon in the menu, add this launcher to desktop, then right click on the desktop icon, and go to properties>launcher, the command used to start the program should be given there and you can use this to start it from the terminal.

---

### Post by PharmaPhunk on 2008-09-19
I get "segmentation fault" right after it quits. Another weird thing happend, when I logged on today my desktop had completely been reverted back to the defualt one. I was using advanced desktop animation, and had a customized theme. I recently installed a new video card, and added some more RAM. They worked originally, could that be the cause of any of this?

---

### Post by PharmaPhunk on 2008-09-22
Its getting really bad now, programs are quitting left right and center. Would a full system re-install clear this? Or is this more of a hard ware issue?

---

### Post by Yannick Le Saint kyncani on 2008-09-22
> **PharmaPhunk said:**
> I get "segmentation fault" right after it quits. ... I recently installed a new video card, and added some more RAM. They worked originally, could that be the cause of any of this?

RAM ...

Install memtes86+, reboot and make it test your ram for an hour or two. If you get errors in the first five minutes, no need to look any further ... bad ram.

PS: Many different programs crashing all the time and having segfaults is characteristic of bad ram.

---

