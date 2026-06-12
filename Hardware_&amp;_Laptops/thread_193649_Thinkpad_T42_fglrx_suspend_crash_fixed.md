---
title: "Thinkpad T42 fglrx suspend crash fixed"
date: 2006-06-10
forum: Hardware &amp; Laptops
---

### Post by sarcaman on 2006-06-10
My T42p worked almost perfectly under a Dapper release clean install with fglrx added. (well, after uncommenting ACPI_SLEEP=true in /etc/default/acpi-support). Suspend, Hibernate, wireless, 3D. Best I've ever had from any Linux distro ever!

 But two  niggling problems remained:

 1. when returning from sleep, the display did a multicolour flash thing, even though it eventually came back

 2. restarting the X server (eg ctrl-alt-backspace) AFTER a suspend  froze the machine requiring a hard reset (although it worked fine immediately after power up).

Both of these problems went away by changing my  /boot/grub/menu.lst kernel line to look like:
[B]
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet video=mtrr,vesafb:1400x1050 vga=834[/B]

And as an added benefit, I also have full display resolution in console mode.

---

### Post by Patsoe on 2006-06-10
Interesting stuff! I may need something like that, too. Do you have a link that explains about the mtrr and other options perhaps? Thanks in advance.

---

### Post by sherlock-holmes on 2006-06-10
[QUOTE=sarcaman]My T42p worked almost perfectly under a Dapper release clean install with fglrx added. (well, after uncommenting ACPI_SLEEP=true in /etc/default/acpi-support). Suspend, Hibernate, wireless, 3D. Best I've ever had from any Linux distro ever!

 But two  niggling problems remained:

 1. when returning from sleep, the display did a multicolour flash thing, even though it eventually came back

 2. restarting the X server (eg ctrl-alt-backspace) AFTER a suspend  froze the machine requiring a hard reset (although it worked fine immediately after power up).

Both of these problems went away by changing my  /boot/grub/menu.lst kernel line to look like:
[B]
kernel          /boot/vmlinuz-2.6.15-23-686 root=/dev/hda1 ro quiet video=mtrr,vesafb:1400x1050 vga=834[/B]

And as an added benefit, I also have full display resolution in console mode.[/QUOTE]

good..that gave me a text mode login too... but it flashes several times when it loads tty's i guess....and it takes a lot of time to connect to the network too....may be these things are quite different....thanks anyway

---

### Post by dngpng on 2006-06-15
Actually here on my T43, everything works well (sleep, hibernate) with the fglrx driver in the official repository only if I dont add any "vga" thing to the kernel parameters. But when I add "vga=835", the laptop will sleep but will frozen when waking up :( I dont know why and I really miss the full resolution CLI.

Anyone knows a solution?

---

### Post by shizow on 2006-06-16
i have a T43 too, and since i upgraded from breezy to dapper suspend does not work again, nothing happens when i press fn+f4

any suggestions

---

### Post by dngpng on 2006-06-18
[QUOTE=shizow]i have a T43 too, and since i upgraded from breezy to dapper suspend does not work again, nothing happens when i press fn+f4

any suggestions[/QUOTE]

dont know what happens when uprading. I alwasys reinstall the system to avoid problems. But one thing maybe infomative is, if you just update recently, please notice there is bug after the recently kernel upgrade: [https://launchpad.net/distros/ubuntu/+bug/50031](https://launchpad.net/distros/ubuntu/+bug/50031), which will make both hibernate and suspend broken on a thinkpad laptop.

---

### Post by gpierce on 2006-06-18
I'm glad to have found this thread. It's good in a way that I am not alone. My thinkpad t43p won't sleep or hibernate. I thought it was something I had done. But now, I see it's a much deeper problem. I hope this gets fixed soon.

Greg

---

### Post by shizow on 2006-07-08
> **shizow said:**
> i have a T43 too, and since i upgraded from breezy to dapper suspend does not work again, nothing happens when i press fn+f4

any suggestions

now it works when i click on the battery icon and then go on suspend!
but it does not work when i press Fn+F4, hwo do i get this working again?

---

