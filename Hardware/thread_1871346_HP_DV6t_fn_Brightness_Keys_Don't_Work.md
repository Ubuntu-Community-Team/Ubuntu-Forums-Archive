---
title: "HP DV6t fn Brightness Keys Don't Work"
date: 2011-10-28
forum: Hardware
---

### Post by erikschmitz on 2011-10-28
Hello,

I have an HP DV6t-6000 Quad Edition with switchable intel sandy bridge / radeon 6770m graphics. Recently upgraded to 11.10 with no issues... I use vgaswitcheroo to turn off the radeon graphics, and everything worked fine except the brightness function keys.

After some research, I've found that adding the following to /etc/default/grub gets the brightness keys working in both Gnome Shell and Unity.

in the file, find the line 
```
GRUB_CMDLINE_LINUX=""
```
and set it to
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```
then, in a terminal, run
```
sudo update-grub
```

Hope this saves you all some time.

-Erik

---

### Post by Bordee on 2011-11-03
Thanks for posting this solution. I can confirm that it also works on Kubuntu 11.10 on an HP dv6t.

---

### Post by ricaldi on 2012-06-08
:lolflag: GRACIAS!. thanks you so much. you save my eyes. I found this "acpi_backlight=vendor" in other post BUT, it never said into GRUB_CMDLINE_LINUX="" . Other thing. I cant down my screen brightness just 90% I said that, because when I pressed "f2" one more time the screen turn off, but no problem with "f3" i cant up it. I forgot it . I have a Hp Dv6t Quad Edition with Ubuntu 12.04.):P

---

