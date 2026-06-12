---
title: "No /dev/hdc"
date: 2006-01-30
forum: Hardware &amp; Laptops
---

### Post by Lykurg on 2006-01-30
Hi,

after installing Kubuntu 5.10 from a cdrom to my Laptop (IBM Thinkpad R40) there is no /dev/hdc. That's the reason why I can't mount my cdrom.

Can you tell me how I get hdc unter /dev, so that I can use my cdrom?


Thanks,
Lykurg

---

### Post by Juergen on 2006-01-30
All I can google says it should work in Linux, and thanks to Ubuntu's udev the dev-entry should be created automatically.
If you're running Gnome, a CD should even be auto-mounted after you insert it.

So, do you have any 'special' hardware?
Not the usually builtin CD-drive or such?

Maybe just try a reboot...

---

### Post by Lykurg on 2006-01-31
Well,

udev is installed, and my hardware is just normal. (Never had that Problem in my Linux life.) The last years I had Gentoo on my Laptop, and my cdrom was accessable under /dev/hdc. And Yesterday I had SuSE istalled (I know that was a BIG mistake!), where my cdrom also works under /dev/hdc.

Maybe I need a higer kernel version? (2.6.12-10-386)

Thanks,
Lykurg

---

### Post by Lykurg on 2006-01-31
Ok,

now I have /dev/hdc! I made a BIOS flash, and works well.


Lykurg

---

