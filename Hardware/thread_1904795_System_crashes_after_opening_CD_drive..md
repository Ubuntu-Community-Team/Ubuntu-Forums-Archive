---
title: "System crashes after opening CD drive."
date: 2012-01-05
forum: Hardware
---

### Post by sjantz on 2012-01-05
Hi all,

I'm having the very odd problem of having a complete system hang whenever I open my CD/DVD drive on my laptop. I'm currently running Kubuntu, but I encounter the problem on any other linux distro. I get nothing when I press Ctrl, Alt, F1. I have a custom, generic Intel based laptop from AVA direct.

System Info:

CPU: Intel(R) Core(TM) i7-2720QM CPU @ 2.20GHz
RAM: 8 gigs
CD/DVD: Pioneer DVD-RW DVRTD10RS
Kernel: Ubuntu 11.10 (oneiric) 3.0.0-14-generic

---

### Post by 2F4U on 2012-01-05
Did you look into the system log files? Are there any errors reported?

---

### Post by Grenage on 2012-01-05
I'm curious as to whether it's a not a Linux problem, but a hardware problem.  Does it eject ok when you're in the BIOS, or other native config screen?

---

### Post by sjantz on 2012-01-05
I didn't notice any errors in the logs. I noted the time when I opened and shut the drive and there just seems to be a time gap between then and when I do a hard reboot of the system.

The computer does not lock up in the BIOS when I open and close the drive. I have found that if the drive is open before booting into ubuntu, I can insert a dvd or cd and it will work fine. However, when I eject the CD and then close the drive, it will hang.

---

### Post by sjantz on 2012-01-18
So one thing I did notice is that my DVD/CD drive is manufactured by COMPAL but linux identifies it as a Pioneer. Could it be that the wrong driver is being used?

---

### Post by sjantz on 2012-01-21
Problem solved. I re-seated the CD drive and it's working fine now.

---

