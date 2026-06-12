---
title: "Reduce Brightness on asus eepc 1001ha"
date: 2010-10-05
forum: Hardware
---

### Post by _El_Chojin_ on 2010-10-05
Hi:
Through usb i have installed Ubuntu 10.04 on my laptop asus eee pc 1001ha and all works fine except that special keys don't work, so i cant reduce brightness of the screen.

Is there any way to reduce it? (i don't want to use the other ubuntu version for this laptops, i prefer this one because is what i have used always).

Thanks in advance.

---

### Post by Griffiss on 2010-10-06
I had a similar problem, and eventually found a workaround, though not a full solution, by using the following command:```
sudo setpci -s 00:02.0 F4.B=e0
```where B=x can be set with values from 00 to FF in hexadecimal notation which corresponds from complete blackness to full brightness. And 00:02.0 is the address of my VGA controller given by the command```
lspci
```

Discussion of my problem can be found here, with links to the fix in post #15: [http://ubuntuforums.org/showthread.php?t=1588980](http://ubuntuforums.org/showthread.php?t=1588980)

---

### Post by MarkieB on 2010-10-06
no longer participating in ubuntuforums.org

---

### Post by _El_Chojin_ on 2010-10-07
> **Griffiss said:**
> I had a similar problem, and eventually found a workaround, though not a full solution, by using the following command:```
sudo setpci -s 00:02.0 F4.B=e0
```where B=x can be set with values from 00 to FF in hexadecimal notation which corresponds from complete blackness to full brightness. And 00:02.0 is the address of my VGA controller given by the command```
lspci
```

Discussion of my problem can be found here, with links to the fix in post #15: [http://ubuntuforums.org/showthread.php?t=1588980](http://ubuntuforums.org/showthread.php?t=1588980)


Sorry but this dont work for me :S
 [QUOTE=MarkieB]
for asus Eeepc you need to add acpi_osi=Linux acpi_backlight=vendor to

— GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub [grub2 – then sudo update-grub]

— kernel boot description in /boot/grub/menu.lst [grub1]

then you could need eee-control .deb from [http://greg.geekmind.org/eee-control/](http://greg.geekmind.org/eee-control/) to allow gui control of some more eeepc configuration settings

funny though that for most people the brightness keys are the only ones that work before the changes

Best 
[/QUOTE]
Hi:
Thanks i have installed it and works but fails a lot, if you give more brightness only let you to execute down brightness 1 time, after that don't reduce brightness more.
Sound key don't works.

Thanks in advance for all replies.

---

