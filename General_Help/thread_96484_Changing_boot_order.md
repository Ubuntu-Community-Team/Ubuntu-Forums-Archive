---
title: "Changing boot order"
date: 2005-11-29
forum: General Help
---

### Post by niallabrown on 2005-11-29
How do I change the order of operating systems in the grub boot loader so I can define the default os to load?  Gurb is already installed and pointing by default to ubuntu, I need windows to be the primary os.

Thanks

---

### Post by linkunderscore on 2005-11-29
i was just about to make a thread about a similar question. Maybe someone could also answer my question.

How can I "clean-up" my grub menu? I recently installed a new kernel and then updated it (and coincidentally updated my old kernel as well). This in-turn added several more entries to my grub menu. I just want to display the most recent kernel and its recovery counrterpart. 



[I don't want to hijack this thread, so answer his question first if you can. I just figured i would ask in here since its the same topic]

---

### Post by aysiu on 2005-11-29
Assuming Windows is the fourth boot option and that you have a title right above it that says "other operating systems":

Open a terminal (Applications > Accessories > Terminal). Copy and paste these commands ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
``` Look for a line that says *default 0*. Change it to say *default 4*.

---

### Post by aysiu on 2005-11-29
[QUOTE=linkunderscore]
How can I "clean-up" my grub menu? I recently installed a new kernel and then updated it (and coincidentally updated my old kernel as well). This in-turn added several more entries to my grub menu. I just want to display the most recent kernel and its recovery counrterpart.[/QUOTE] If you put a # sign in front of a line, it's no longer there (as far as Ubuntu's concerned--you'll still see it in the /boot/grub/menu.lst file, but you won't see it in the boot menu any more).

You have to put a # sign in front of every line in an entry.

As an example, this is what a commented out entry looks like: ```
#title          Ubuntu, kernel 2.6.12-9-386
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
#initrd         /boot/initrd.img-2.6.12-9-386
#savedefault
#boot
```

---

### Post by linkunderscore on 2005-11-29
[QUOTE=aysiu]If you put a # sign in front of a line, it's no longer there (as far as Ubuntu's concerned--you'll still see it in the /boot/grub/menu.lst file, but you won't see it in the boot menu any more).

You have to put a # sign in front of every line in an entry.

As an example, this is what a commented out entry looks like: ```
#title          Ubuntu, kernel 2.6.12-9-386
#root           (hd0,2)
#kernel         /boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
#initrd         /boot/initrd.img-2.6.12-9-386
#savedefault
#boot
```[/QUOTE]
Thats exactly what I was looking for. Thank you VERY much :)

---

