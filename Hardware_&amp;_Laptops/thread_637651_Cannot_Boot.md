---
title: "Cannot Boot"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by prodigalson666 on 2007-12-11
Installed gutsy on my acer 5520, after reboot the bar freezes on the usplash and doesnt go any where. I rebooted and pressed alt-f2 to go into verbose mode, the reboot freezes at the reboot usplash screen resolution, it fails on the first 2 choices, then freezes on the third 1 1280x1024. Is this because its selecting resolutions out of the alptops range? Rebooting into safe mode has the boot freeze up as well, it gets as far as the sata hard drive then stops. Any ideas, thanks.

---

### Post by rockin_goliath on 2007-12-11
At the grub menu, press "e" to edit the normal boot entry, scroll down to the line that begins with "kernel" and press "e" again. Remove the words "quiet splash" from the end, press enter to save, and "b" to boot. This will give you a no nonsense verbose mode. Is it hanging up in the same places, if at all? If it boots just fine, it is probably a known issue with your usplash resolution, check out the attached link.

[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

---

### Post by prodigalson666 on 2007-12-11
Thanks but pressing e does nothing, I cant get to a terminal or anything, this is bad.

---

### Post by prodigalson666 on 2007-12-11
ok after 3 min I get this screen

busy box v1.1.3 (debian 1:1.1.3-5ubuntu7) built ion shell (ash)
enter help for a list of built in commands

(initramfs)

---

### Post by rockin_goliath on 2007-12-12
I had the exact same message when I realized that I had a broken hard drive. It was an IDE drive, and I realized that I had bent one of the pins. After fixing the pin, the drive worked fine. If this is a new laptop, I would return it ASAP.

---

### Post by prodigalson666 on 2007-12-12
Thanks but its not the hard drive, open suse and sabayon both work fine.

---

### Post by prodigalson666 on 2007-12-19
BUMP, any help guys or gals?

---

