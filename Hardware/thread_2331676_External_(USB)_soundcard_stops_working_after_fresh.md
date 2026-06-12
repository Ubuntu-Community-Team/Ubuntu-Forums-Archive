---
title: "External (USB) soundcard stops working after fresh installation and restart"
date: 2016-07-24
forum: Hardware
---

### Post by ocellot2 on 2016-07-24
Hello,
I've been trying for some days to install and configure my Sony Vaio Laptop either with Ubuntu or UbuntuStudio last version (16.04, Xenial Xerus). Installations process finishes without errors, and all hardware seems to work, even my external USB soundcard (Focusrite Scarlett 6i6). External soundcard is properly recognized by system, and it's even possible to get sound out of it. Unfortunately, USB external soundcard stops working after restart, even if no system upgrade is performed and no additional packages are installed. After restart, soundcard is still being recognized by system, but I'm not able to get any sound out of it (I've selected the proper sound interface in volume control, but no sound comes out). Built-in sound card is also recognized by system, and works fine when selected in volume control.

I've reinstalled about 20 times, without success. I'm having no ideas. Any hints are wellcome.

Thanks,
Ocellot

---

### Post by Bucky Ball on 2016-07-24
Welcome. Your install is fine. It has nothing to do with your issue so install, if it works fine stay with it so we can try and troubleshoot what's happening. There may be a LOT of stuff in Ubuntu Studio that you will never use, so try that and Ubuntu in a live session to see which you like best before installing. You can install anything from Ubuntu Studio in Ubuntu later if you like.

Ubuntu Studio uses the xfce4 desktop environment. Ubuntu uses Unity. If you'd rather use the xfce4 desktop, install Xubuntu (more lightweight) and same applies. You can install what you like from Ubuntu Studio later. 

Is it a self-powered external card or getting power from the laptop? When you say it stops working after restart, do you mean when you close and open the lid (suspend) or when you restart or shut down the machine? 

This is a matter of tweaking the OS rather than reinstalling to the same issue so get to a stable install for starters.

(PS: If your install is fine (please confirm), and if you don't mind, I might move the thread to Hardware as it is about your hardware rather than install and you will get better support there.)

---

### Post by ocellot2 on 2016-07-26
Thanks for your reply.
First of all, I confirm that my installation is fine (UbuntuStudio 16.04). I'd like to move current thread to "Hardware", but don't know how to do it yet... :S

Second, my USB-soundcard is self-powered. When I say "it stops working after restart", I'm not meaning "suspend", I'm really meaning either restart or shutdown/start. I'd like to start troubleshooting, so I will keep waiting for further instructions...

---

### Post by Bucky Ball on 2016-07-26
*Thread moved to **Hardware***.

Sorry if this seem like silly questions, but ...

Just to confirm, you boot the computer, plug in the soundcard and it is picked up and functions fine? You reboot or switch the computer off and on again *with the soundcard still plugged in and switched on* and when you get back to a desktop, no soundcard?

As this is happening when your reboot or switch on the computer, how is it working when it does? You are plugging it in when the computer is on? The problem is that the soundcard is not picked up if it is plugged in and switched on when you switch the computer on?

If the above is the case you might try looking in the BIOS and switching the internal audio off. There should be a setting there somewhere, but not in all BIOS(es!). The machine (before Ubuntu) may be ignoring any external sound cards if your internal is on. I know this is the case with my desktop setup (I have an external audio interface also).

If it is not there at boot, Ubuntu may be picking it up fine if it is plugged in and switched on while you are running a desktop. :-k

---

### Post by ocellot2 on 2016-07-27
After fresh install, USB soundcard is properly recognized by system and functions fine. When I restart my computer (or shut it down/start) it doesn't work anymore. It still gets recognized/picked up by system, but no sound comes out of it. I've also tried to boot computer after a while, plug in the soundcard (after booting) and same behaviour: soundcard is recognized/picked up by system, but doesn't work. Besides, my USB soundcard was working in a previous UbuntuStudio 14.04 installation, with same BIOS setup. And as I said, soundcard is being recognized at boot, the problem is that not sound comes out of it when selected in sound settings.

---

### Post by ocellot2 on 2016-08-12
Solved as stated in [https://ubuntuforums.org/showthread.php?t=2333735](https://ubuntuforums.org/showthread.php?t=2333735)

---

