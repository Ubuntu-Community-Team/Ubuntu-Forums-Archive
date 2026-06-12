---
title: "Toshiba Satellite takes ages to boot and BIOS error"
date: 2008-05-25
forum: Hardware
---

### Post by Hozza on 2008-05-25
Hi,

I have a Toshiba satellite laptop and it has issues.

It will only accept BootCD's/LiveCD's when all of the planets align(lol), however It did decide to read the ubuntu bootCD and I managed to install Gusty Gibbon, I have since upgraded to Hardy Heron.

But when I tried to boot it for the fist time it said BIOS Error: 8254 timer not connected to 10-APIC or something along those lines.
Then it takes about 5mins (with a blank, black screen) to load. This problem still persists even with Hardy Heron.

It does this every time it’s turned on, it’s not affecting the actual OS but its very annoying.

Also when it is shutting down the normal shut down blurb (the white writing on the black background) is unusually large - is this normal

Apart from this I am loving Hardy and Ubuntu is the best Linux about.

Can anyone help?
:(

---

### Post by r.masters on 2009-02-08
I am having similar problems, also on a Toshiba Satellite laptop.

While I was installing some updated packages the laptop ran out of battery (the power cable had fallen out the back - d'oh!) and since then I get similar errors after GRUB tries to boot Ubuntu. Interestingly I don't get these if I choose the .7 version (rather than the .11) from the GRUB menu.

As for shutdown, it just takes a very long time (as I write this it's actually taking quite a while to boot up as well).

---

### Post by Hozza on 2009-02-08
this post is really old now but ok, i sorted the issue ages ago.

if you install boot up editor or something like :s that you can edit the start up screen resolution settings and replace the shutdown text with a graphical shutdown thing, which seems to speed it up.

sorry im in a bit of a rush atm and i dont think that is the correct name for the "boot up editor" app so ill post deatals when i get some time :D

---

### Post by Ericyzfr1 on 2009-02-09
On my wife's toshiba Sat, this message appeared during Ubuntu 8.10 install.
I wiped out everything....reinstalled 8.04.. No problems.

This morning I reinstalled 8.10 and after the upgrades, during the boot there was 2 kernel versions 2.6.27.11 at the top which was causing the fault, below was 2.6.27.23 which works without a glitch.

I reversed the order in the /boo/grub/menu.lst to have 2.6.27.23 to boot as default.

---

### Post by Ericyzfr1 on 2009-02-09
Actually, what I stated earlier is incorrect, I upgraded from 8.04 to 8.10 and I guess during the upgrade the kernel 2.6.xx.23 is still listed. This kernel does not show the bios bug 8254

---

### Post by Ericyzfr1 on 2009-02-09
2.6.24.23-generic to be precise. I don't know if there is going to be any issues with it.

---

