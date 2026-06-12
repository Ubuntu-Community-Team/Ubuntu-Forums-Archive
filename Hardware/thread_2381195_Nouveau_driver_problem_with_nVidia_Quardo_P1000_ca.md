---
title: "Nouveau driver problem with nVidia Quardo P1000 card"
date: 2017-12-28
forum: Hardware
---

### Post by Nick Payne on 2017-12-28
Running 17.10 on a PC with an nVidia Quadro P1000 video card, Nouveau driver, and Wayland. Ubuntu is current with all updates as of today. The PC is dual boot via grub with Windows 10. If I cold boot into Ubuntu from poweroff, shortly after I enter my userid and password at the GUI login screen, the login stops at a console screen saying 
```
nouveau 0000:01:00.0: secboot: error during falcon reset: -110
nouveau 0000:01:00.0: gr: init failed, -110
...[etc]
```
and the only recourse at that point is the power button or reset button on the PC. Photo that I took of the screen here, as I had no other way of capturing the output:

[IMG]https://lh3.googleusercontent.com/_fNSclEiGF7PkOsDarEEbw3CNyr_t9oPkcpivrjrgA2p9oMU96mu0f5UIZp1yyHZfkd5pU3gW8I7ANcRJaWddzJRgoKd_cN28lho5PE_pIUT7Dao7XtaN8Q3FnEnebdek0kagkTq-w[/IMG]

If, from a cold boot, I boot into Windows first, login, and then reboot into Ubuntu without powering off, the problem does not happen. The problem is 100% reproducible when cold booting directly in Ubuntu, and hasn't yet happened when I boot Windows first.

This looks like a strange error in the Nouveau driver where it can't initialise something in the hardware, but if Windows is booted first, the nVidia driver there initialises whatever is needed on the card and that persists through a warm boot. I don't want to run the nVidia blob driver instead, as I can't get per-monitor scaling to work with it, and I need that to get GUI elements to be the same size on both monitors.

---

### Post by mörgæs on 2017-12-30
Is there any difference if you boot into Xorg mode?

---

### Post by Yellow Pasque on 2017-12-31
Similar complaint here: [https://bugzilla.redhat.com/show_bug.cgi?id=1508088](https://bugzilla.redhat.com/show_bug.cgi?id=1508088)
Have you tried the latest upstream kernel to see if the bug is fixed?

---

### Post by Nick Payne on 2017-12-31
I installed 4.14.9 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.9/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.14.9/"), but the problem is the same. I might install the nVidia blob and see if it fixes the problem.

---

