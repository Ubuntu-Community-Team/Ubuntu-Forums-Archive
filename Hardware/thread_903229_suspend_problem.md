---
title: "suspend problem"
date: 2008-08-28
forum: Hardware
---

### Post by vitas on 2008-08-28
I have installed ubuntu 8.04 on my new MSI MegaBook VR201x notebook, but suspend/resume doesnot work. After suspend notebook sleep happily (power led is blinking), but when trying resume, notebook is powered off after 3 sec.
I tried acpi=off and noapic kernel options, but no improvement. Problem may be coused by some kernel modules, but I don't know how to determine which makes the problem. 
Any sugestions?

---

### Post by vitas on 2008-08-29
I found hint
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend).

I tryed suspend by this method several times with these non sence result (magic number was increasing) and matched device was ttyvf, ttyq8, ttyue ... and system time was correct. I guess kernel never gets proc after resume.

I also tryed set password in bios, but af resume it does not ask me for password (normaly at boottime it beeps twice and waits for password).

---

