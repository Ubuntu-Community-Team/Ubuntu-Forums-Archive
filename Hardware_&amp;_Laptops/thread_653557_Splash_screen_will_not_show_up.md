---
title: "Splash screen will not show up"
date: 2007-12-30
forum: Hardware &amp; Laptops
---

### Post by bwang on 2007-12-30
I have a Dell Poweredge 400SC and after I installed a new graphics card, nothing shows up on the monitor until the login screen appears (the GRUB menus, BIOS screen, and progress bar don't appear). When I shut down, the progress bar does not appear; the monitor just goes black until my computer turns off. Does this have something to do with the fact that the AGP slot is not supported, or do I have to set some setting to make them show up?

---

### Post by staticvoid on 2007-12-30
this is just a glich with Usplash, i had the same problem, here is the fix:

1. run this command in a terminal: 
[B]sudo gedit /etc/usplash.conf
[/B]> 
# Usplash configuration file
xres=1024
yres=768

and change the values to the above.

2. now run this **sudo gedit /boot/grub/menu.lst**
and add *vga=791* to the kernel line. 

(before)
> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		             (hd0,6)
kernel		           /boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70 ro quiet splash
initrd		             /boot/initrd.img-2.6.22-14-generic
quiet
(after)
> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		     (hd0,6)
kernel		   /boot/vmlinuz-2.6.22-14-generic root=UUID=63d6696a-ee49-4735-ae70-c1fe14dfdf70 ro quiet splash
initrd		   /boot/initrd.img-2.6.22-14-generic
quiet             **vga=791**

3. then run this **sudo update-initramfs -u -k `uname -r**

hope that works :)



sv

---

### Post by staticvoid on 2007-12-30
and you might wanna check out [http://ubuntuforums.org/showthread.php?t=580903&highlight=black+splash](http://ubuntuforums.org/showthread.php?t=580903&highlight=black+splash)

basically all we did above is changed the resolution to 1024 by 768 vga=791 means this resolution.

sv

---

### Post by bwang on 2007-12-31
It doesn't work. Nothing shows up until the login screen; the monitor just says "No Signal"

---

### Post by zipperback on 2007-12-31
> **bwang said:**
> I have a Dell Poweredge 400SC and after I installed a new graphics card, nothing shows up on the monitor until the login screen appears (the GRUB menus, BIOS screen, and progress bar don't appear). When I shut down, the progress bar does not appear; the monitor just goes black until my computer turns off. Does this have something to do with the fact that the AGP slot is not supported, or do I have to set some setting to make them show up?


What kind of Video card did you previously have in the machine? If your previous video card was not AGP, and your new card is AGP, double check your bios to make sure your AGP slot is enabled.

I suspect however, that you are trying to use an incorrect video driver, since you installed a new graphics card, and it was probably a different type than the last one.

If that is the case then you should boot your system, when it gets to the grub menu, hit esc and select the recovery option, this should boot you to a root terminal.

You will need to reconfigure xorg.

Enter the following into a terminal window:
sudo dpkg-reconfigure xserver-xorg

You will then be able to reconfigure your xorg system.

Once you have done that, you should be able to boot into your system as normal.

Please let me know if that works.

- zipperback
:popcorn:

---

### Post by staticvoid on 2007-12-31
> **bwang said:**
> It doesn't work. Nothing shows up until the login scree; the monitor just says "No Signal"

Follow zipperbacks instructions then. It must be the card :) reconfigure everything.

so your on a desktop not a lappy..? ok..

sv

---

### Post by bwang on 2007-12-31
I can get into my system fine. Only the splash screen will not show up. My card is a nVidia GeForce 5200

---

### Post by zipperback on 2007-12-31
> **bwang said:**
> I can get into my system fine. Only the splash screen will not show up. My card is a nVidia GeForce 5200

I still say you should follow my instructions and reconfigure your xorg.

However.....

sudo apt-get install startupmanager

that is a utility you should be to use to manage your usplash screen.



- zipperback
:popcorn:

---

### Post by fcu423 on 2008-07-06
Hi, i was checking this topic and i was wondering if there is any way to change the splash image. I mean, it comes out a ubuntu logo, but i want to change it.
Can i???

Thanks!

---

