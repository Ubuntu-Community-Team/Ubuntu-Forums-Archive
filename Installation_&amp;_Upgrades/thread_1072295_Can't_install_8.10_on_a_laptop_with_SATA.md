---
title: "Can't install 8.10 on a laptop with SATA"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by bunnny on 2009-02-17
Hi

The bad news: I've been away from linux for a year now.

The good news: I have once again decided to go with linux.

The bad news part 2: I can't install it.

I'm trying to install ubuntu 8.10 server on a laptop with a SATA HD. I burned the iso to a cd-r checked the MD5 sum. Reboot and the boot menu appear, but when I choose "install" the screen goes black except a flashing underline in the topleft corner.

So... I tried all combinations of settings available in the menu, aka. noacpi, nolacpi, and so on. Then I got an error about pnpbios, after that an continues disk read error.

I tried with the boot command pnpbios=off, but then I got an error about an USB driver (USB-hub?). The bios doesn't allow me to do any advanced configurations (USB-settings, SATA-settings).

Any ideas?

---

### Post by albandy on 2009-02-17
why are you using ubuntu server in a laptop?
There's no graphical environment and the kernel is designed to run in servers (ECC memory, hw raid, ....)

Try 8.04 server but you should use desktop edition.

---

### Post by bunnny on 2009-02-17
> **albandy said:**
> why are you using ubuntu server in a laptop?
There's no graphical environment and the kernel is designed to run in servers (ECC memory, hw raid, ....)

Try 8.04 server but you should use desktop edition.

I will use it as an server (the monitor is broken). I have tried xubuntu 8.04 alternate with the same result.

I forgot to write that I have also tried to start the installation from an USB-stick

---

### Post by TonyFordz on 2009-02-18
I found a way around the SATA installing problem as a main drive all you need to do is whipped out your partition table & leave it blank & Ubuntu will find your SATA device. I about went nuts trying to figure out how the hell to get it to show up when I first swapped out to SATA but yeah I just used my Windows XP Pro CD to boot up wiped out the partition table then put the Ubuntu disk in & had no problems with having it find my SATA.

As for the installing of 8.10 no idea I can get 32-bit or 64-bit to install on my PC but 7.10 installs just fine go figure... 8,10 32-bit did well on my Intel PCs but not on my AMD Quad Core 9550.

Hope your able to sort it all out there, and I hope that the SATA information is useful to you also.

---

