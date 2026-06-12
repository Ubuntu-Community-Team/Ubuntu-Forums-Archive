---
title: "Backlight stays on on DPMS"
date: 2005-08-01
forum: Hardware &amp; Laptops
---

### Post by nocturn on 2005-08-01
I have a HP Pavilion zv5474EA laptop with Ubuntu Hoary (and an Nvidia GO graphics card)

When my display blanks using the DPMS timeouts (or manually with xset), the backlight stays on.  No matter if the DPMS state is stanby or off.

Any ideas on what is causing this?  It's a minor, but annoying problem.

---

### Post by dave9191 on 2005-08-01
Have you tried 

```
xset dpms force off
```

Dave

---

### Post by nocturn on 2005-08-01
[QUOTE=dave9191]Have you tried 

```
xset dpms force off
```

Dave[/QUOTE]

Yes, it blanks the screen but the backlight stays on.

---

### Post by dave9191 on 2005-08-01
Thats the command to turn the screen off, maybe you screen doesnt support dpms power mamgment features ? 

Dave

---

### Post by nocturn on 2005-08-01
[QUOTE=dave9191]Thats the command to turn the screen off, maybe you screen doesnt support dpms power mamgment features ? 

Dave[/QUOTE]

I'm still googling for this and a number of laptop users seem to have this probelm (though I have not found a solution).
Most users report that the backlight gets turned of in Windows though.  Some have luck with certain version of ATI or Nvidia drivers...

---

### Post by bobby555 on 2005-08-02
I partly have the same problem. After editing my xorg conf file to enable the various monitor sleep and off modes the screen blanks but the backlight stays on.

However, trying ```
xset dpms force off
``` works for me. How do I incorporate this into my xorg conf file?

AM

---

### Post by nocturn on 2005-08-02
[QUOTE=bobby555]I partly have the same problem. After editing my xorg conf file to enable the various monitor sleep and off modes the screen blanks but the backlight stays on.

However, trying ```
xset dpms force off
``` works for me. How do I incorporate this into my xorg conf file?

AM[/QUOTE]

This does not work for me either...
For you, I think setting the off timeout will do it (it goes through standby and suspend first).  Maybe you can try this in xscreensaver.

---

### Post by dave9191 on 2005-08-02
[QUOTE=bobby555]I partly have the same problem. After editing my xorg conf file to enable the various monitor sleep and off modes the screen blanks but the backlight stays on.

However, trying ```
xset dpms force off
``` works for me. How do I incorporate this into my xorg conf file?

AM[/QUOTE]

Hey, 

you dont put this into your xorg.conf file. You can either setup xscreensaver using their GUI interface to enable power managment features, or add it to your acpi config files in /etc/acpi/

Dave

---

### Post by bobby555 on 2005-08-02
I got it working now. I checked my scripts in the folder suggested, but they referred to some other scripts (ACPI). One of those had the ```
xset dpms force off
``` line in it.

So I just enabled monitor off in the GUI for xscreensaver and set it to the same time I entered in my xorg conf file (1 minute).

AM

---

### Post by nocturn on 2005-08-03
I have filed a bugreport about this:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=13163](http://bugzilla.ubuntu.com/show_bug.cgi?id=13163)

---

### Post by nocturn on 2005-08-10
bump

---

### Post by nocturn on 2005-08-23
bump

---

### Post by Delvien on 2005-11-26
bump

---

### Post by dave9191 on 2005-11-26
Hey, 

I came accross this problem when I switched to gentoo (Im back to ubuntu now :) ). In the /etc/X11/xorg.conf file under your monitor section you need to have the DPMS option. So that you should have something like this. 

```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

```

Check that you have Option "DPMS" in there, and if you don't, add it and restart your xserver. With any luck this is it. 

Dave

---

