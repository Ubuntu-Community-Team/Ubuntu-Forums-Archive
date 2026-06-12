---
title: "Touchpad issue - must load modules in right order"
date: 2005-07-20
forum: Hardware &amp; Laptops
---

### Post by flyvholm on 2005-07-20
I'm running the AMD64 version of Ubuntu (kernel 2.6.10) on a Presario R3000Z, just installed a couple of days ago. Most hardware detection/configuration has been smooth, but the Alps touchpad has been giving me a headache. Installed the Synaptics driver and applied the Alps patch, touchpad remained dead.

I finally managed to Google my way to the source of the trouble: Modules have to be loaded in a different order. Specifically, module psmouse has to be loaded after any usb modules (see [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)). Doing
# modprobe -r psmouse
# modprobe psmouse
magically brings the touchpad alive. However, the settings (speed, scroll etc.) are messed up - I assume this is because the Alps-specific options I entered in /etc/X11/xorg.conf failed to load during startup.

So, I need to fix the order in which the modules are loaded during startup. I'm a newbie and don't know which file to edit. I found a post and a repost asking this same question, no replies. Surely, somebody out there must know in which file the module loading order is determined?

Thanks in advance.

---

### Post by s_p_a_r_k_y on 2005-07-20
[QUOTE=flyvholm]I'm running the AMD64 version of Ubuntu (kernel 2.6.10) on a Presario R3000Z, just installed a couple of days ago. Most hardware detection/configuration has been smooth, but the Alps touchpad has been giving me a headache. Installed the Synaptics driver and applied the Alps patch, touchpad remained dead.

I finally managed to Google my way to the source of the trouble: Modules have to be loaded in a different order. Specifically, module psmouse has to be loaded after any usb modules (see [http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)](http://gentoo-wiki.com/HARDWARE_Synaptics_Touchpad)). Doing
# modprobe -r psmouse
# modprobe psmouse
magically brings the touchpad alive. However, the settings (speed, scroll etc.) are messed up - I assume this is because the Alps-specific options I entered in /etc/X11/xorg.conf failed to load during startup.

So, I need to fix the order in which the modules are loaded during startup. I'm a newbie and don't know which file to edit. I found a post and a repost asking this same question, no replies. Surely, somebody out there must know in which file the module loading order is determined?

Thanks in advance.[/QUOTE]

Modules are usually put in /etc/modules and each module is loaded sequentially. However, if modules can be loaded by the hotplug service and by hald and udev, so one of them might be loading it at boot up.

---

### Post by flyvholm on 2005-07-21
Thank you, s_p_a_r_k_y. I edited /etc/modules and put psmouse at the very end, but unfortunately to no avail. So it appears USB modules are loaded after the ones in /etc/modules by some other file.

Anybody know which other files to look in? Besides /etc/modules II've been looking in /etc/X11/xorg.conf and /boot/config-'uname -r' to compare to what is going on in the boot log /var/log/Xorg.0.log, and there's something (probably a lot) I'm missing. The module names from /etc/modules don't appear in the boot log, but I do recognize some of the stuff from the xorg.conf file. However, there are also lots of modules I don't know where  come from. None of it says anything with USB, but I assume it is some of the NVidia chipset stuff.  I've attached part of the boot log and /etc/modules in case somebody wants to take a closer look at what I'm talking about.

Any input highly appreciated, thanks in advance.

EDIT: Taking a closer look at /etc/X11/xorg.conf I've realized that this is what governs the order in which things appear in the boot log. However, I have no clue how/when the modules from /etc/modules such as psmouse are loaded? No signs in the boot log.

I am not quite as eager to find out though since my touchpad is now working (except scroll). The solution turned out to be adding "i8042.nomux" to the end of the kernel line in /boot/grub/menu.lst as advised in the article linked in the original post above. So the problem was not what I thought, but at least now it's solved. Except for the scroll which I read requires a newer kernel to work - not sure I feel courageous enough to get into that...

---

### Post by flyvholm on 2005-07-28
Okay, since I appreciate clear instructions myself I figured I should clarify to others how to check for the issue I was having and how to resolve it if present.

Search the output of "dmesg" for the string "i8042", like this:

dmesg | grep i8042

If nothing is returned, your problem lies elsewhere. But if grep returns a line like
i8042.c: Detected active multiplexing controller, rev 1.1.
you may eliminate the touchpad issue by doing one of the following:

1. Open the file
/boot/grub/menu.lst
and look in the automagic kernels list for lines beginning with "kernel". Add the parameter "i8042.nomux" to these lines, like this:

kernel		/boot/vmlinuz root=/dev/hda2 ro console=tty0 quiet splash i8042.nomux

You probably don't want to do this for the "recovery mode" sections - I'm a newbie myself and don't know if it makes any difference whatsoever, but I did not want to mess with the recovery modes and did not see any reason to either since they give me a command line prompt.

Reboot and hopefully the touchpad will work! It did for me.

2. This method did not work for me, but maybe it will for you, so I'll post it anyway:
Open the file
/etc/modules
Move the line "psmouse" to the end and add option "i8042_nomux=1", like this:

psmouse i8042_nomux=1

Reboot to see if it works.

Good luck!

---

### Post by Pablo J. on 2005-07-29
[QUOTE=flyvholm]Good luck![/QUOTE]
*"Alea iacta est"* :D

¡¡It's a miracle!!

¡¡One year heading the wall!! ](*,)

Thank you.

It happens the same to me: The solution #1 works fine, but not the #2.

---

### Post by orawax on 2007-03-26
I added

kernel		/boot/vmlinuz root=/dev/hda2 ro console=tty0 quiet splash **i8042.nomux**

to /boot/grub/menu.lst -

now *dmesg | grep i8042*  produces:

> [    0.000000] Bootdata ok (command line is root=/dev/sda1 ro quiet splash i8042.nomux)
[    0.000000] Kernel command line: root=/dev/sda1 ro quiet splash i8042.nomux
[   20.898179] serio: i8042 AUX port at 0x60,0x64 irq 12
[   20.898479] serio: i8042 KBD port at 0x60,0x64 irq 1

but touchpad is still broken...

EDIT: 
Followed the instructions at Wiki's Community Doc:
[https://help.ubuntu.com/community/Peripherals#head-88ab01e09b1f8cb66733b224268e3aa1d30722ec](https://help.ubuntu.com/community/Peripherals#head-88ab01e09b1f8cb66733b224268e3aa1d30722ec)

Now touchpad seems to be somewhat working, and I'm also able to use qsynaptics to configure it. But still some random symptoms, let's see if it's getting back to chaotic or is this a real solution...

---

