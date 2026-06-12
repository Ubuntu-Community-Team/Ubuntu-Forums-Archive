---
title: "Lost USB ports"
date: 2013-12-16
forum: Hardware
---

### Post by newb85 on 2013-12-16
I have a desktop machine that doubles as a file and print server.  (Actually, it mostly just serves as a server, but occasionally is used as a workstation, too.)  It's running Saucy.  It's set up so that I can ssh in to control it, too.

Tonight I noticed that the server was unresponsive, so I rebooted it.  Since then, it seems the system isn't communicating with any USB peripherals, including the mouse, the keyboard, and the wireless adaptor.  (Probably the printer, too, but that's a moot point.)  I don't think it can be a hardware issue, because I can still use the keyboard to arrow up and down on the GRUB screen, but once Ubuntu boots, all I get is an unresponsive login screen with a blinking cursor and a message that my wireless is not connected (and the wireless adaptor isn't lighting up like normal).  All I can do from there is push the power button on the machine, which shuts it back down.  Eerily, the Ubuntu splash when it's shutting down is turquoise.

I'm guessing that the only solution will involve creating a Live USB and booting from that to make repairs.  (The machine is too old/stripped down for a DVD drive.)  But I'm not sure what repairs should be made.  Any help would be appreciated.

---

### Post by coldraven on 2013-12-17
I guess that after booting from a Live USB you should check the drive(s) and the memory.
Do the drives first because the memcheck will take a long time.

---

### Post by newb85 on 2013-12-17
I'm not exactly sure what you expect me to find by checking the drive and memory.  I can boot into a live session just fine, and the SMART data for the drive looks okay.

I did however follow a hunch: I booted from the HDD and selected Ubuntu Advanced Options, and selected the second newest kernel.  Presto, I have a functional system back up and running.  Apparently, the latest kernel for Saucy doesn't play nice with my hardware.

I would prefer not to have to select the kernel each time I boot up.  What are my options?

---

### Post by newb85 on 2013-12-23
*Bump* how do I prevent my system from booting 3.11.0-14 (which disables my USB ports)?

I noticed something:
```
$ dpkg --get-selections | grep -v deinstall | grep linux-image
linux-image-3.11.0-13-generic            install
linux-image-3.11.0-14-generic            install
linux-image-3.5.0-27-generic            install
linux-image-3.8.0-32-generic            install
linux-image-extra-3.11.0-13-generic        install
linux-image-extra-3.5.0-27-generic        install
linux-image-extra-3.8.0-32-generic        install
linux-image-generic                install

```

3.11.0-14 (the problematic kernel) is the only one that doesn't have a corresponding linux-image-extra package.

Meanwhile, my system keeps "holding back" the package linux-image-generic.

I switched to the main repository, just to make sure it isn't the mirror I'm using, but still no change.

---

### Post by newb85 on 2013-12-23
Doh! Solved my own problem.  What I pointed out in my last post was the root of the problem: the kernel wouldn't use the USB ports because the extras for the kernel weren't installed.  All I had to do was install the package linux-image-extra-3.11.0-14-generic, and presto, the latest kernel worked properly and the linux-image-generic package was no longer held back.

Not really sure why the extra package wasn't installed for 3.11.0-14 automatically like it was for previous kernels, but anyways, the problem is solved.  Hope this helps someone else.

---

