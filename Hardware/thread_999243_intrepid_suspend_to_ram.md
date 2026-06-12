---
title: "intrepid suspend to ram"
date: 2008-12-01
forum: Hardware
---

### Post by steeler on 2008-12-01
suspend to ram works fine but on restore i get

[ 152.0366685] pm_op(): pci_pm_resume+0x0/0x80 returns -16
[ 152.0366685] PM: Device 0000:00:00.0 failed to resume: error -16

and then i am left with a blank screen
any assumptions what might be wrong?

---

### Post by steeler on 2008-12-02
ok i found it..it was the nvidia proprietary driver that caused the problem.
should i fill a bug report? is there any fix i might do?

---

### Post by KuBala on 2008-12-23
similar scenario here:

[131.474155]pm_op(): pci_pm_resume+0x0/0x80 returns -5
[131.474164]PM: Device 0000:01:07.0 failed to resume: error -5

And blank screen, l can only reset.

And it is caused by the nvidia proprietary for sure, because the suspend works fine with the open source driver. But since the latter does not support 3d acceleration compiz does not work.

Any suggestion or workaround?

geforce3 ti200 agp
abit nf7
ubuntu 8.10 2.6.27-9 generic
nvidia proprietary version: 96.43.09

---

### Post by Ben_H on 2009-01-12
abit nf7, nvidia mx440, same problem. Anyone? Please?

---

### Post by yther on 2009-01-17
No solution, but a little more info for anyone concerned.

This works for me using "Suspend to RAM" from the K menu.  Opening the lid or pushing Power gets me back to my desktop after a few seconds.  I also see some messages about devices that "failed to resume," but everything seems OK.

However, I just tried using the laptop's "sleep" button (it's really <Fn>+<F1> which has a little moon on it), and the machine suspended to RAM but now, when I try to resume by pushing the Power button, or closing and opening the lid again, I briefly see the device messages (three of them, I believe) and then...

**...the laptop goes back into suspend!!!**  If I do <Ctrl>+<Alt>+<Del> when I see the system messages, it does a proper shutdown and restart, but I can't resume.

So, it seems the suspends are handled in different ways.  Pushing the button seems to use the laptop-mode way, and using the K menu does it differently.

It also no longer resumes from "Suspend to Disk" (K menu again) now that I have the new NVIDIA driver.  Prior to installing that, hibernate worked properly.  Now, if I try it, the system ignores the hibernation and boots up as if I had done a normal shutdown.

Dell Inspiron 1520
Kubuntu 8.10
NVIDIA driver 177.82-0ubuntu0.1, installed with EnvyNG

---

### Post by alf on 2009-03-27
I was having the same problems with both my IBM desktop and my Lenovo notebook (T61) until I found this page:
[https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend](https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend)

After following the instructions on that page the resume on my computers became very reliable.

---

