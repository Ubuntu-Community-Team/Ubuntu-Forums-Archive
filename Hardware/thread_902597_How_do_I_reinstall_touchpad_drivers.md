---
title: "How do I reinstall touchpad drivers?"
date: 2008-08-27
forum: Hardware
---

### Post by Corpsemayer on 2008-08-27
I have been using ubuntu 8.04 for almost a year now and I love it.
I have never had any problems until recently. I installed frets on fire on my computer had a couple problems with so i then decided to uninstall it. But when I uninstalled it the touch pad became unresponsive.I can still control the cursor with a usb mouse. When I installed the os the touch pad work with out a problem,so i belive if I reinstall the driver it should work agian.

Please help

---

### Post by Corpsemayer on 2008-08-29
The touchpad buttons work but the pad dosen't. I know it's not broken becasue it works in windows.

---

### Post by jasonkirk2006 on 2008-08-29
I had a similar problem. After BIOS upgrade, my ALPS touchpad got out of control. The solution i found was to use i8042.nomux=1 kernel option.

To add it, open your grub configuration file /boot/grub/menu.lst and add this option to the end of the kernel line. You need to be root to do that.

Here are the steps:

1. Press Alt+F2 to open Run dialog. Write 

```
gksu gedit /boot/grub/menu.lst
```

Enter your password afterwards.

2. Your menu.lst file may be a complicated one with several lines starting with "kernel". Determine your choice and add i8042.nomux=1 to the end of the line. For example

```
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=f06e6522-5087-4163-940e-a615509f018f ro quiet splash [COLOR="Red"]i8042.nomux=1[/COLOR]
```

3. Then restart you X server by pressing Ctrl+Alt+BACKSPACE. You should have no unsaved work prior to this operation.

---

