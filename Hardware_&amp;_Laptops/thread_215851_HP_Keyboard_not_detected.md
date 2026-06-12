---
title: "HP Keyboard not detected?"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by RobbieT on 2006-07-14
I have an HP xw4300 workstation with a very plain-jane 104-key keyboard. Every other distro I've tried on it works with the keyboard fine - no reason not to, it's a very generic 104-key keyboard. PS2 connector, not a USB. However, Ubuntu stops seeing it as soon as it boots up. It's not a multimedia keyboard or anything like that, just a very plain 104-key keyboard with a PS2 connector.

Anybody have any ideas?

---

### Post by RobbieT on 2006-07-15
bump

---

### Post by RobbieT on 2006-07-17
Found the answer to this on a Mepis forum after trying a Mepis LiveCD and finding that it couldn't access the keyboard, either. Adding Linux acpi=off to the boot options allowed it to see the keyboard and run normally, so I did this with the Ubuntu CD and it worked, too. So - if you're having problems with your keyboard, there's an option to try.

---

### Post by lahelahe on 2006-08-08
Same problem, HP keyboard model # 9109 but when using the live acpi=off option I get the Kernal panic - not syncing: attempted to kill init   This an Edubuntu install on an HP dc 7600 for a computer lab for a small school. Thank you for any help that may come our way.

---

### Post by lahelahe on 2006-08-11
Was able to resolve by switching to a ps/2 to usb adapter for the keyboard.

---

### Post by Rulas on 2006-08-30
I have the same hardware, HP xw4300 Workstation, and the same problem: PS/2 keyboard not work with USB mouse pluged.

These seems a kernel incompatibility with acpi features, I solve this problem disabling it on grub startup kernel instructions.

Edit: /boot/grub/menu.lst, and append **acpi=off**

```
title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-686 root=/dev/sda2 ro quiet splash **acpi=off**
initrd          /boot/initrd.img-2.6.15-26-686
savedefault
boot

```

This work for me !

---

### Post by deepclutch on 2007-06-30
another guy with feisty and edgy with an old hp kbd says that he got it working well with boot option "apm" appended to kernel line in GRUB.hope someone
acpi=off apm=on in /boot/menu.lst
see the thread:
[http://ubuntuforums.org/showthread.php?t=359190&page=2](http://ubuntuforums.org/showthread.php?t=359190&page=2)

---

