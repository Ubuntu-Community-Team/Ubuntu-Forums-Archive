---
title: "No Terminal using ctl+alt+F1"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by Astro96 on 2006-10-09
Hi,
I have a Dell D620 running Dapper and it is working great except for a few hitches.  When I try to get a terminal by pressing ctrl+alt+F1-F6 the screen turns off (backlight and everything is off).  Going back to the X server (F7) gets my display back, but I never get a terminal.  I tried booting without the splash screen by editing my grub menu.lst, and that allowed me to get a terminal, but it stopped me from going to suspend.

Also, with a splash screen bootup, I don't have a shutdown splash screen.  The display turns off (backlight is off).  Any ideas?

Thanks!
Andy

---

### Post by MWAAAHAAA on 2006-10-09
Are you using the DVI connector to connect your monitor to your video card? If so, try using the VGA connector instead.

---

### Post by Astro96 on 2006-10-10
I'm not using an external monitor.  The D620 is a Latitude laptop so I'm just using the built in (wide) screen.

---

### Post by jede on 2006-10-10
Hi Andy,

I've also had this problem, I think you also have a NVIDIA graphic card, right?

You need to add the option "vga=791" to the booted kernel, so the line in the  file /boot/grub/menu.lst looks like this:

kernel  /boot/vmlinuz-2.6.15-27-686 root=/dev/sda6 ro quiet splash vga=791

Then it works, you have then the console resolution "1024x768".
Unfortunately this option will be removed when you updating the kernel the next time :-(

HTH,
Stefan

---

### Post by Astro96 on 2006-10-18
That worked!  Thanks so much!  It looks a little funny on my widescreen, but I only use it when X crashes, so no big deal.

Thanks again!
Andy

---

