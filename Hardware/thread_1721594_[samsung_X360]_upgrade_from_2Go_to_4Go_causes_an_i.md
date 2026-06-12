---
title: "[samsung X360] upgrade from 2Go to 4Go causes an infinite reboot...."
date: 2011-04-04
forum: Hardware
---

### Post by diabolo512 on 2011-04-04
Hi,
i've got a Samsung X360 laptop which runs on ubuntu 10.10 64 bits.

it has been shipped to me with 2Go of RAM (spec says DDR3). i've decided to add more RAM from 2Go to 4 Go with a 2Go DDR3 memory module.

the initial and new memory modules are detected in the bios.
mem86 in the grub menu does not detect any problem on the memory modules.

but when i boot with these two modules, the ubuntu graphical loading image display, and there are 3-4 seconds with a black screen, and a reboot....
i've tried to boot with the original memory module alone on the two different memory sockets with success.
i've tried the same thing with the new memory module with success.
but when these two memory modules are present simultaneously, it causes an infinite reboot after the ubuntu logo display...

which log files need to be inspected to know what makes the boot process crash?

have you any suggestions?
best regards,

Charles.

---

### Post by diabolo512 on 2011-04-05
any ideas about how to know what's wrong at startup?

thanks in advance,

Charles.

---

### Post by ppsp on 2011-08-12
Hi I am trying something similar.. I am trying to upgrade from 4gb to 8gb .. but can't figure out how to open the x360 to replace the RIMMS how did you do that?

Thanks
Piyush

---

### Post by diabolo512 on 2011-08-31
Hi,
the samsung x360 laptop has got a memory capacity limited to 4go....
so, the motherboard will not support this upgrade.
to have access to memory banks, (not useful in your situaton because you've got already the max memory capacity), you have to remove screws at the back of your laptop (with the 'KBD' label), to free your keyboard.
and you have to pull up your keyboard carefully, to have access to memory banks.

hope it helps,
Charles.
ps: i'm always stuck with my memory upgrade problem (infinite reboot...)

---

### Post by pmurk on 2012-05-07
The constant reboot could be solved on my Samsung X360, 4 GB with the boot parameter mem=4096M on 64 Bit 11.10 and 12.04

---

