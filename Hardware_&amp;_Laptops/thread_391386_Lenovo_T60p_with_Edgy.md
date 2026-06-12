---
title: "Lenovo T60p with Edgy"
date: 2007-03-23
forum: Hardware &amp; Laptops
---

### Post by chiragjog on 2007-03-23
Hi
I installed ubunu Edgy from a DVD on my Lenovo thinkpad t60p.

The problem is that my brightness button seems to be giving problems

[fn]+[end] .....decrease brightness doesnt work
but
[fn]+[home]....increase brightness works.

Rest works as predicted , but this is only strange thing happening.

Brightness keys work on Windows XP.

Thanks a lot

---

### Post by flossgeek on 2007-03-23
See [http://www.thinkwiki.org/wiki/Problem_with_LCD_brightness_buttons](http://www.thinkwiki.org/wiki/Problem_with_LCD_brightness_buttons)

**Make a backup before you begin, always good practice.**

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bk
```

However the work around for fedora may not be the same as Ubuntu. Basically though you need to NOT load the ACPI video module. 

To do this you would open the menu.lst file:-

```
gksudo gedit /boot/grub/menu.lst
```

Now look for the most recent kernel line that should look something like this(it will probably be slighlty different):- 

*kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash*

At the end of this line above add **acpi=off** so it would look like:-

*kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash acpi=off*

---

### Post by nanophobic on 2007-03-23
But turning acpi=off would stop other power management functionality, won't it?

---

### Post by flossgeek on 2007-03-23
You could try it to see what happens, I read somewhere that the ACPI built into the laptops Bios will suffice.

---

### Post by chiragjog on 2007-03-26
Hi I booted the kernel with acpi=off .
What happened after that is as follows:

I could login into Edgy . But after login GNOME didnt load.
I got only a screen with a background....
Nothing else loaded no Menubars etc.

The brightness functions worked fine though !




So effectively the problem still exists

---

### Post by flossgeek on 2007-03-26
Okay so at least you know that it is something to do with the acpi, unfortuanately it has made your system unusable, simply turn it back on, and start exploring to find yourself a solution. You may want to try Feisty Beta LIVE CD to see if that works okay, you never know it may fix your issue.

---

### Post by neozen on 2007-03-27
hi there... I've had the same problem under edgy on my r60e with the 2.x series bios... I'm in the feisty livecd beta now and this issue STILL appears.... ARG

really frustrating that they haven't fixed this in the new kernels....

the beta livecd I'm using is based on 2.6.20-12 I believe... and the current highest image is 2.6.20-13... I'm going to open another bug report and see if I can get this handled by the time the final feisty is released

---

