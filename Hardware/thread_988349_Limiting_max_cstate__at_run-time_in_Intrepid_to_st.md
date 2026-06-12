---
title: "Limiting max_cstate  at run-time in Intrepid to stop CPU whining noise?"
date: 2008-11-20
forum: Hardware
---

### Post by Joshua66 on 2008-11-20
Hi all,
Is there a way to limit max_cstate in Intrepid at run-time?  It used to be possible to write to /sys/module/processor/parameters/max_state which changed max_cstate at run-time, but that file does not exist in Intrepid.
It seems like in Intrepid the only way is to reboot, either reconfiguring the kernel, or changing the CPU power management BIOS setting, which is pretty inconvenient.

I sometimes need to limit max_state to prevent the CPU from entering C4, which causes a high-pitched whining noise on my Lenovo T500.  Basically, when I'm in a noisy area, like on a plane, I want to allow C4 to extend battery life, but when I'm in a quiet area, like at home, I want to disable it because of the noise.  It's annoying to have to reboot every time I wish to make this transition (I usually suspend rather than shutdown my laptop).

Thanks for any suggestions!
Josh

---

