---
title: "Incomplete shutdown on Toshiba M50-113"
date: 2005-11-16
forum: Hardware &amp; Laptops
---

### Post by Daniele Di Pietro on 2005-11-16
Hallo everybody,

  I've installed Ubuntu "Breezy" on my Toshiba M50-113 laptop. I managed to fix all the issues I had also thanks to
[http://www0.org/toshiba/m50_130.html](http://www0.org/toshiba/m50_130.html) 

  The only problem left is that the shutdown is incomplete and I have to switch the laptop off manually by pressing the power button.

  I suspect that this may be due to the fact that toshiba_acpi module is not loaded. However, when I try to load it with
sudo modprobe toshiba_acpi
I get the following error message:
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.12-9-386/kernel/drivers/acpi/toshiba_acpi.ko): No such device

  Any clue?

Thanks for the help,
Daniele

---

### Post by Daniele Di Pietro on 2005-11-27
Hi.

  After some testing and web-surfing I realised that:

1. the shutdown is incomplete ONLY when a USB peripheral is attached to any USB port

2. the toshiba_acpi module doesn't actually fit my laptop, so it is correct not to have it loaded

Still, I haven't found any solution yet.

---

### Post by TwiceOver on 2005-11-27
I also have a Toshiba laptop.  I was about to post a similar problem when I saw your post.  After switching to Breezy my ACPI features do not seem to be working properly.

I have a Toshiba A15 series laptop.  I can shutdown just fine (wasn't always the case) however I cannot restart.  When I choose restart Ubuntu goes through its shutdown/restart sequence then the screen just goes black all power still on.  I have to hold the power button to shutdown then again to start up.

As I said earlier, the shutdown feature didn't always work for me.  Being a complete Linux newbie, after hosing my system once I just decided to reinstall.  After that reinstall I am at where I am now.  Shutdown works fine, restart doesn't.

Any help?

---

### Post by Daniele Di Pietro on 2005-11-27
Hallo.

  Have you already tried to determine whether the problem only occours when a USB peripheral is attached to your computer? If this is the case, my guess is that something with hotplug just doesn't work fine.

  Another possibility, which didn't work in my case, is to disable some ACPI-handled events by adding "nolapic" to the booting options. You may try this, but beware: simply adding "nolapic" to your GRUB line may be dangerous. You'd better make a trial copy so as to preserve the original settings and be sure to be able to reboot again.

Hope it helps. Bye,
D

---

### Post by TwiceOver on 2005-11-27
[QUOTE=Daniele Di Pietro]Hallo.

  Have you already tried to determine whether the problem only occours when a USB peripheral is attached to your computer? If this is the case, my guess is that something with hotplug just doesn't work fine.

  Another possibility, which didn't work in my case, is to disable some ACPI-handled events by adding "nolapic" to the booting options. You may try this, but beware: simply adding "nolapic" to your GRUB line may be dangerous. You'd better make a trial copy so as to preserve the original settings and be sure to be able to reboot again.

Hope it helps. Bye,
D[/QUOTE]

Even with a USB device (USB Key) attached, my system acts the same way.  I have also removed my Wireless Card and still the same.  The "nolapic" thing sounds a little risky for my skill level, so I didn't try that.

---

### Post by Daniele Di Pietro on 2005-11-28
Hallo.

Don't be scared of trying. It's just a matter of **appending** the following lines to your /boot/grub/menu.lst file

title           Ubuntu, kernel 2.6.12-9-686 (nolapic)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-686 root=/dev/sda1 ro quiet splash nolapic
initrd          /boot/initrd.img-2.6.12-9-686
savedefault
boot

Of course, if you haven't installed the 686-kernel, replace it with the correct architecture. If the boot fails, you can restart and reboot with your old kernel options by just selecting the proper line from the menu.

Let me know if you succeed. Bests,
Daniele

---

