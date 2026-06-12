---
title: "Splash/framebuffer on a Dell D600 with Radeon 9000"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by MadEgg on 2008-01-18
I recently bought a second hand Dell Latitude D600 laptop with a Radeon Mobility 9000 on it.
Mostly worked fine but there is one problem and that is that it doesn't show the framebuffer/splashscreen while booting. This means that I get a blank screen for about 1 minute, then the X display comes up and everything is fine. If I manually switch to a VT (Ctrl+Alt+F1) I get visual but it is with extremely huge letters(like only about 20 fit on the screen).

It isn't that disturbing normally(but would be when the time comes to perform a full periodic check on the harddisk), but I really would like it to work. I tried adding vesafb to /etc/initramfs-tools/modules and running update-initramfs and adding vga=769 (640x480@256 colors) or vga=791(1024x768@16-bit colors) to /boot/grub/menu.lst. This results in a completely blank screen, and the screen stays blank in text-mode(so no more huge letters).

Any way to get the splash screen during bootup?

And by the way: I also tried installing fglrx from ati.com (newest)(using the official ubuntu-guide) but once that's installed X doesn't start anymore, says something about no device detected in xorg.0.log.  Is the radeon 9000 not supported by this driver? Is the 900 FPS in glxgears I get from the default driver the best I can get out this card?

Any help appreciated!

---

### Post by MadEgg on 2008-01-18
*bump*?

---

### Post by MadEgg on 2008-01-20
Has noone got the bootsplash working on a Dell D600? Or maybe Radeon (Mobility) 9000?

---

### Post by MadEgg on 2008-02-11
I still haven't solved this problem, still no one able to help me?

---

### Post by Yellow Pasque on 2008-02-11
FYI, recent relases of fglrx only support the Radeon 9500 and later, so don't use that. Have you tried booting with the nosplash option, so that you can st least see text while booting?

---

