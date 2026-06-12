---
title: "Installation on a external USB HDD"
date: 2009-04-29
forum: Installation &amp; Upgrades
---

### Post by joseraeiro on 2009-04-29
Hello,

I've installed ubuntu 9.04 on a external USB HDD on my laptop, but it was meant for trying to rescue the data on another computer. Now when I try to boot on my laptop without the USB HDD connected I get a error 21 on GRUB. How do I fix this? I do not want to use the installation from the USB HDD on this computer.

Worst of all, on the other computer (the one the installation was meant for) gives me a "No operating system" error when I try to boot from the USB HDD...

Please help!

Thanks in advance.

---

### Post by dandnsmith on 2009-04-29
First step is to provide more info - what was on the PC before the installation to the external HDD?
It's obvious that the boot setup has been 'corrupted', but you need to supply more info for advice about recovery.

---

### Post by ndefontenay on 2009-04-29
Hi. With the HD still pluggeed, could you try to access Grub config file?
See if you can remove linux OS from there.

---

### Post by dandnsmith on 2009-04-29
Just been checking location for [boot info script](http://sourceforge.net/projects/bootinfoscript/) which you could download and run from the PC when booted into the 9.04 on external HDD.

The non-ability to boot on the other PC has to be
**either** it has no ability to boot from the external HDD
**or** there is no grub install on the external HDD

That boot script should supply info about that stuff - you could post back for further advice.

---

### Post by joseraeiro on 2009-04-29
Hi. I've managed to fix it running grub from within ubuntu with the external HDD plugged off.

Grub reconfigured itself without the external partition.

But I still can't boot with the external HDD on the other laptop.

Thanks!

---

