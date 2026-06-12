---
title: "Cannot get brightness to change."
date: 2014-03-12
forum: Hardware
---

### Post by jlh68 on 2014-03-12
I have an Acer Aspire One 750 with Ubuntu12.04LTS install and the [Fn] + [brightness down] or [brightness up] do not change the brigthness.  I have tried a couple of fixes wihich have not worked.

Today I used Boot-Repair-Disk on this computer and it was using lubuntuOS and the Fn + B-up or B-down worked.  It also worked when I dual booted into Win7. Now I can't boot Win and that is another story.

How do I get the brightness to work, obviously what ever is in lubuntu works.

---

### Post by varunendra on 2014-03-14
Might help if you could post what fixes you tried so far. In any of the contexts, did you also blacklist any drivers or loaded any boot parameters?

Let's see -
```
lsb_release -d
uname -mr
lsmod
lspci -nnk | grep -iA3 vga
grep '^blacklist' /etc/modprobe.d/blacklist.conf
cat /proc/cmdline
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```

---

