---
title: "[SOLVED] Ubuntu and my VGA switch"
date: 2009-01-09
forum: Hardware
---

### Post by MarcelloSav on 2009-01-09
Hello Guys,
I have a problem and I hope we will be able to solve it.
I recently bought a VGA switch for my PC and Xbox.
Xbox works very well, and my father's windows too.
Only Ubuntu gives me a strange problem.
If I turn on my pc with the vga cable connected directly to the monitor there is no problem, but if it is connected to the switch, ubuntu starts with a resolution of 640x480.
There is no way of choosing another resolution. It's blocked, even if I try to restart X.
But now, if I try to link the vga cable directly to the monitor and then I restart X, it works normally, at 1920x1080. Then, I tried to re-connect the vga to the switch, and 1920x1080 works!
Considering that Windows works normally, Xbox too, I don't think it's a problem of my switch.
How can I force gnome to work at 1920x1080?

I've got and old Nvidia 5200, Ubuntu 8.10.

I hope you will help me because it's really boring...
Thanks (and forgive my English)
Marcello

PS: Even if I turn on my PC without any cable connected to the vga, it's the same problem...

PPS: I attach you my .xsession-errors when i start connected to the switch. gnome is unable to add my monitor, it's not supported O.o

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=it_IT.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (640x480) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
x-session-manager[5792]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
Failed to play sound: Sounds disabled
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:5959): WARNING **: Unable to add monitor: Non supportato

(gnome-panel:5957): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -12 and height 26
Nautilus-Share-Message: unknown format for key 'sp-sc/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only
x-session-manager[5792]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
Failure: Module initalization failed
```

---

### Post by cariboo on 2009-01-09
It is a problem with the cable, I've run into a similar problem when hooking my Media PC to my 32 inch Samsung LCD. If I use one vga extension cable to connect, it doesn't detect the monitor properly and   it defaults to 1024X768, if I connect two vga extension cable together, the TV gets detected as a 40" Samsung and I get 1368X768 resolution. Try a different vga cable.

Jim

---

### Post by MarcelloSav on 2009-01-09
OK thanks Jim,
I'll try...

---

### Post by MarcelloSav on 2009-01-10
Ok, I changed two vga cables and the problem is still here.
However this is my actual .xsession-errors (i actually turned it on directly connected to the monitor)

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=it_IT.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1080) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Starting gtk-window-decorator
x-session-manager[6106]: WARNING: Application 'gnome-wm.desktop' failed to register before timeout
Failed to play sound: Sounds disabled
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:6275): WARNING **: Unable to add monitor: Non supportato
Nautilus-Share-Message: unknown format for key 'sp-sc/usershare_acl' as it contains 'Everyone:F,'.  Assuming that the share is read-only
x-session-manager[6106]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
Failure: Module initalization failed

```

As you can see there's no change, except for:
```

Comparing resolution (1920x1080) to maximum 3D texture size (4096): Passed.

```
that in the other .xsession-errors was:

```
Comparing resolution (640x480) to maximum 3D texture size (4096): Passed.
```

How can I disable monitor dection and force the resolution?

Thanks guys :)

---

### Post by MarcelloSav on 2009-01-10
I solved following this post:

[http://forums.nvidia.com/index.php?showtopic=73027&st=0&p=414085&#entry414085](http://forums.nvidia.com/index.php?showtopic=73027&st=0&p=414085&#entry414085)

Thanks you ;)

---

### Post by Duber on 2012-09-11
> **MarcelloSav said:**
> I solved following this post:

[http://forums.nvidia.com/index.php?showtopic=73027&st=0&p=414085&#entry414085](http://forums.nvidia.com/index.php?showtopic=73027&st=0&p=414085&#entry414085)

Thanks you ;)
Could you explain how did you solve it ? Nvidia forums are closed right now for security reasons.

Thanks in advance

---

