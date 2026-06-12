---
title: "X server working on external monitor but not on laptop's"
date: 2010-03-31
forum: Hardware
---

### Post by sillybilly on 2010-03-31
Hello everyone

I've recently bought a new laptop. It's an EliteBook 8440p. It has a nVidia NVS 3100 graphics card. I'm running the 64 bit version of Ubuntu 9.10.

My problem is the X server will not display on the laptop's screen. The first thing I noticed, was usplash cycling trough different display modes while the screen repeatedly went black for a few seconds before showing me text again. After removing usplash, the screen just goes black and comes back at the login prompt (this is for the `nv' driver). At some point I could log in in "low graphics mode" - don't know how I managed anymore - to see that the `nv' driver had given an error message like "/dev/fb0 not found" (I got the sme error message after setting `vga=975' in the grub.) When I installed the proprietary `nvidia' driver I get some weird colorful patterns on my screen, basically noise. Last but not least, I tried the `nouveau' driver. Here, the screen goes black as the X server is starting only to give up and display something like "couldn't fence channel 1: prepare for strangeness". Then the whole process starts again.

There is no /etc/X11/xorg.conf file on my system.

Strangely, all three drivers work fine for an external monitor...

Any hints?

Thanks

---

### Post by king-coder on 2010-04-28
Hi!

Did you solve your problem. I have the same laptop and the same problem.

CU

---

### Post by sillybilly on 2010-05-04
Hello

No, unfortunately, I didn't. Grudgingly resorted to using Windows for now. Have you had more luck in the meantime?

Cheers

---

### Post by krazyd on 2010-05-04
i have this notebook with integrated graphics and it works fine - have you tried with lucid?

---

### Post by sillybilly on 2010-05-06
I have now. But it didn't work either. I tried the 64-bit version. Which version are you running?

Regards

---

### Post by krazyd on 2010-05-10
> **sillybilly said:**
> I have now. But it didn't work either. I tried the 64-bit version. Which version are you running?

64-bit, but I think that's irrelevant. I never use the live-cd installs, only the alternative. Have you tried the vesa graphics driver? you should be able to at least log on to do some more troubleshooting.

---

### Post by sillybilly on 2010-05-11
> you should be  able to at least log on to do some more troubleshooting.Hmm, I'm not sure what you mean. I am able to login to an X session (in  so-called low graphics mode), it's just that the resolution is much less  than what the laptop's monitor would be able to actually support.


I don't really know what troubleshooting I could do. There isn't any Xorg.conf file on my system that I could tweak and I've  just about tried every possible driver I could find.

Cheers

---

### Post by krazyd on 2010-05-12
well I would try a newer kernel:
[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)

And if that still doesn't work, then try a bleeding-edge version of the nouveau driver:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by bmfurtado on 2010-05-28
I have this same laptop (HP EliteBook 8440p) with the Intel GMA HD and I've tried like 10 different combinations of kernel/drivers to get KMS to work... I've reached the conclusion that sometime between 2.6.31 and 2.6.32-22 KMS stopped working on this computer. It boots, I can hear the sound that the computer makes at the login screen but the screen stays black (with backlight on).

I attached a serial cable and sent the kernel output with the KMS debug mode enabled to the serial console and found no weird outputs.

I'd use Ubuntu 9.10 with 2.6.31-* however it seems that the wireless adapter that comes with this computer is only supported on 2.6.32+ so for now i'm forced to go with Windows 7...

Does anyone have any suggestions?

---

### Post by fh_scott on 2010-11-09
I got 10.04 64-bit installed on this unit and was able to work around the no display on the live cd issue if anyone still cares.

I'm stuck with power management issues, though. When the screen blanks or goes to standby it never comes alive again.

---

### Post by krazyd on 2010-11-09
resuming from standby didn't work for me in 10.04 but does now in 10.10.

---

### Post by fh_scott on 2010-11-14
To get the LiveCD to boot, choose the nomodeset option from the grub menu.

I just installed 10.10 clean on a 8440p with the 3100 Nvidia chip.

after the install I had to change line 9 of /etc/default/grub:

GRUB_CMDLINE_LINUX_DEFAULT="quiet nomodeset"

and run:


$ sudo grub-mkconfig -o /boot/grub/grub.cfg

that took care of the black screen on booting issues 

When power management blanks the screen I have to press Fn+F4 to get the screen to come back.

Bluetooth didn't come back after a suspend. Haven't tried to hibernate yet.

---

