---
title: "Jaunty won't suspend more than once"
date: 2009-05-21
forum: Hardware
---

### Post by boba23 on 2009-05-21
Hey folks,

I am trying to get suspend/hibernate to work on my ubuntu 9.04 machine. 

Here are my specs:

GA-73PVM-S2H Mainboard
Intel E8400
Nvidia 9400GT (latest Nvidia driver 1.85.18.10)
Samsung SATA 250GB

As others with e.g. notebooks also experienced my first try on suspend works fine, machine goes to sleep and I can wake it up fine.
Then on second try, it stops X I see a console window ... and after a few seconds it comes back to the Desktop.
After a reboot, I can reproduce the problem, first suspend works, then NADA ... :-(
I already installed uswsusp and tried s2ram etc. same behavior :-(
Is there any reliable way to get suspend working? I really need this, since this is a HTPC and I don't want to keep it running or fully shut down all the time.

Thanks,

boba

---

### Post by markoid8 on 2009-06-12
i have the same problem on all 3 of my ubuntu computers. they all run clean installs of ubuntu 9.04, but this problem has always existed, since 7.04.

one is a toshiba satellite pro 6000
the other is a compaq c762nr
the other is a custom desktop:
asus p5ple mobo, 2GB ram, intel core 2 duo e6300

anyone have any ideas?

---

### Post by markoid8 on 2009-06-12
i installed the new 2.6.30 kernel from the ubuntu kernel ppa mainline, and it solved the problem for me.

try and see if it works for you too.

---

