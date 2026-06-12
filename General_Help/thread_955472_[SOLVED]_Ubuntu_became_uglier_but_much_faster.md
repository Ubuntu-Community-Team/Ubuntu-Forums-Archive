---
title: "[SOLVED] Ubuntu became uglier but much faster"
date: 2008-10-22
forum: General Help
---

### Post by Maratonda on 2008-10-22
After some updates I was greeted by the following screen:
[[IMG]http://img233.imageshack.us/img233/5779/screenshottx7.th.png[/IMG]](http://img233.imageshack.us/my.php?image=screenshottx7.png)[[IMG]http://img233.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)
On the right, you may notice some icons which are different from the Dust theme I was using

When I click on appearance I get
```

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect.
This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager 
may already be active and conflicting with the GNOME settings manager.
```

BUT! now ubuntu is unbelievably fast...so the question is: why? What is this theme it is using instead of the dust theme?

---

### Post by Catalyst2Death on 2008-10-22
EDIT: Do you use KDE and GNOME or just GNOME?

Its not.  The screen shot looks like what happens after a kernel update, and you graphics card drivers need to be recompiled/reinstalled.  You can check that they're loaded/working by doing this:

```
$ lsmod | grep <nameofcard>

```
where nameofcard could be nvidia or ati, or an offbrand provider also check that you have direct rendering:

```
$ glxinfo | grep render
```

which should return something along the lines of:
```

direct rendering: Yes
OpenGL renderer string: GeForce 9600 GT/PCI/SSE2/3DNOW!
    GL_NV_depth_buffer_float, GL_NV_conditional_render, GL_NV_depth_clamp, 
    GL_NV_vertex_program3, GL_NVX_conditional_render, GL_SGIS_generate_mipmap, 
```

Basically this is what happens when you strip all of the eye-candy off of gnome, but its not generally considered a feature....

EDIT:  This may not be the solution, but you should check anyway because they recently released the 2.6.24.21 kernel, and I had problems with my graphics card.

---

### Post by Maratonda on 2008-10-22
I have an ATI Radeon 9200SE but > lsmod | grep ati did not return anything...

> alessandro@ubbu:~$ glxinfo | grep render
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa DRI R200 20060602 AGP 8x x86/MMX/SSE2 TCL

I am confused...

---

### Post by Peter09 on 2008-10-22
You have the base graphics card driver running (Mesa). Have a look in

System->Administration->Hardware Drivers.

See if it is asking to enable the third party driver that you need.

---

### Post by Maratonda on 2008-10-22
It says no proprietary drivers are installed...but my point is, how is it possible that with those drivers everything is 5 times faster than it used to be? Shouldn't the appropriate (open-source in my case) drivers for my ati radeon 9200 be BETTER and FASTER?

---

### Post by iheartubuntu on 2008-10-22
Im having the exact same problem. EXACT. I didnt see your post when I had made mine....

[http://ubuntuforums.org/showthread.php?p=6013250#post6013250](http://ubuntuforums.org/showthread.php?p=6013250#post6013250)

I have an nVidia card and in my hardware drivers list I have three nvidia drivers listed...

-version 173
-version 96
*version 177

With 177 activated and is the recommended choice. I had to manually activate after the reboot, then rebooted again and it didnt fix the prob. I'll try dropping back to the 173 driver and see what that does for me.

Ive had the drivers get deactivated after an update where I have to manually activate it again, but never this sort of prob.

---

### Post by iheartubuntu on 2008-10-22
fix can be found here... [http://ubuntuforums.org/showthread.php?t=955679&page=2](http://ubuntuforums.org/showthread.php?t=955679&page=2)

---

