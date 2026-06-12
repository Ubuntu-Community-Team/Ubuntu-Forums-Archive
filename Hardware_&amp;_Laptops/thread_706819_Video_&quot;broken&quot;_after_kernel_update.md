---
title: "Video &quot;broken&quot; after kernel update"
date: 2008-02-24
forum: Hardware &amp; Laptops
---

### Post by AMegapode on 2008-02-24
HI all,

After a recent kernel update, I have discovered that video is "broken". I am running an Nvidia GeForce MX 4000 video card and had been using the "Nvidia-glx" drivers. Had everything setup and workig fine(Compiz, 3D effects, etc). After the kernel update, I get no video at all following the splash screen. The only way I could get back into the machine was to start in recovery mode, mount the root partition and edit the xorg.conf, changing "nvidia" to "nv" in the video driver section. I have tried reinstalling the Nvidia-glx drivers, but if I re-enable it and restart, then I am back to no video again. Any help would be greatly appreciated.

Cheers,

AMegapode

---

### Post by mivo on 2008-02-24
Did you get the splash screen or did the screen just go blank? I had that problem and worked around it by doing the following:

After successfully logging in, press Alt+F2 and type:

**gksu gedit /boot/grub/menu.lst**

This will open the text editor (with root access). Scroll down to where it says, "## ## End Default Options ##". In the next paragraph, look for the line that starts with "kernel". Here, replace "quiet" with "nosplash". The paragraph will look similar to this:

```

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=68f63350-fb5a-44b2-bb11-681324d9e6fa ro irqpoll nosplash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

It may not look exactly like this. Don't try to make it match exactly, it's only a sample. Just make sure that it does say "noplash" instead of "quiet". Save the file and reboot. Instead of the blank screen you should see a lot of system messages, and then the login screen. :) If this does not work, repeat the above process and also add "irqpoll" (as shown above).

Note also that the kernel updates overwrite unique boot options unless you fixate them in  the "# defoptions=" line.

---

