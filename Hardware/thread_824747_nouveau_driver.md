---
title: "nouveau driver"
date: 2008-06-10
forum: Hardware
---

### Post by drascus on 2008-06-10
I am trying to install the nouveau driver for my nvidia card. I am following this method. [http://nouveau.freedesktop.org/wiki/UbuntuPackages](http://nouveau.freedesktop.org/wiki/UbuntuPackages)
after running this command > sudo module-assistant auto-install drm-modules I get this response in terminal >  debian/rules:12: /usr/share/quilt/quilt.make: No such file or directory    &#8593;
 &#9474; make: *** No rule to make target `/usr/share/quilt/quilt.make'.  Stop.  any idea how to resolve this because the driver won't work unless you have the assistant modules properly installed and configured first.

---

### Post by sdennie on 2008-06-10
I'm not sure how to fix your problem but, have you tried installing the drivers from here: [https://launchpad.net/~raof/+archive](https://launchpad.net/~raof/+archive).  It looks like they are kept up to date and it's a simple matter of adding those repos to apt.

Edit:
Oops.  I actually clicked through your link and they point to the exact thing I posted.  ;)

---

### Post by Tibco on 2008-06-18
I keep getting the same problem...does anyone know what to do? I have my sources.list set the right way, but i keep getting the same error...

---

### Post by Tibco on 2008-06-18
figured it out, you also need to install the "quilt" package.

---

### Post by drascus on 2008-06-19
So what is you experiance after installing this package? does this enchance video rendering quite a bit? did you get any 3d support? did you get any bugs? just wanted to know before I went through with it myself.

---

### Post by hopelessone on 2008-06-27
Me too.. How did it go?

i recently signed the petition for closed source nvidia drivers at:
[http://www.petitiononline.com/nvfoss/petition.html](http://www.petitiononline.com/nvfoss/petition.html)

---

### Post by drascus on 2008-08-05
the quilt package?? you mean the one in the Repos??

---

### Post by NightwishFan on 2009-05-09
I have tried Nouveau on Fedora 11 Preview. There is no 3D support yet, but I hear it is expected. As for what it actually "does" it gave me the correct resolution and refresh rate by default, no glare on the display like NV, has fairly good 2d rendering, faster than NV, and happily broke suspend and hibernate on my machine.

Sounds promising though.

---

### Post by Hakimio on 2009-06-24
> **NightwishFan said:**
> I have tried Nouveau on Fedora 11 Preview. There is no 3D support yet, but I hear it is expected. As for what it actually "does" it gave me the correct resolution and refresh rate by default, no glare on the display like NV, has fairly good 2d rendering, faster than NV, and happily broke suspend and hibernate on my machine.
3D support is work in progress and it works pretty well with some VGAs (and with some it doesn't work at all). I tested it with 6600GT and it did a decent job (no compiz yet, but xfce and gnome builtin compositing works and high resolution video plays perfectly well when using xv video output).

---

### Post by NightwishFan on 2009-06-24
I think XFCE compositing works with NV. (I think).

---

