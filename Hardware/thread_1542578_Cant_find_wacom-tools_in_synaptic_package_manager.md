---
title: "Cant find wacom-tools in synaptic package manager"
date: 2010-07-30
forum: Hardware
---

### Post by 5BallJuggler on 2010-07-30
I wonder if someone can help.

I'm trying to install a wacom volito2 on my Acer aspire. I'm looking for the package "wacom-tools" does anyone know which repository I need to add to allow me to get it?

---

### Post by Favux on 2010-07-30
Hi 5BallJuggler,

There is no wacom-tools for Lucid.  The xsetwacom commands are included in xf86-input-wacom (the new xserver-xorg-input-wacom package) and there is no wacomcpl.  Best thing to do is to set up a xsetwacom startup script like wacomcpl's .xinitrc.

---

### Post by 5BallJuggler on 2010-07-31
> **Favux said:**
> Hi 5BallJuggler,

There is no wacom-tools for Lucid.  The xsetwacom commands are included in xf86-input-wacom (the new xserver-xorg-input-wacom package) and there is no wacomcpl.  Best thing to do is to set up a xsetwacom startup script like wacomcpl's .xinitrc.

Thanks for the info, I'm new to wacom tablets, and never tried to set one up before, is it straight forward? I've read a couple of howto's on this site, but I don't really know what info I'm looking and what is specific to lucid.

Any info would be greatly recieved

Thanks

---

### Post by Favux on 2010-07-31
It depends on what devices the wacom volito2 has.  Stylus, stylus buttons (how many?), eraser, wacom tablet mouse, buttons on the the tablet?

Some sample scripts and how to install them are at the [Bamboo HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

