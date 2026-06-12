---
title: "NVIDIA Drivers"
date: 2004-11-27
forum: Hardware &amp; Laptops
---

### Post by animalstyle on 2004-11-27
I'm having trouble installing Nvidia Drivers on my Ubuntu system.  I get to the installation screen, but it tells me I need to close X server.  Ive tried changing the init to level 3, but it didnt seem to do anything.  I also tried CTRL ALT BKSP, but that just takes me back to the ubuntu login screen.  What are my options to try at this point?

---

### Post by jiyuu0 on 2004-11-27
[http://kitech.com.my/ubuntu/4.10/index.html#installnvidiadriver](http://kitech.com.my/ubuntu/4.10/index.html#installnvidiadriver)

---

### Post by daniels on 2004-11-27
[QUOTE=animalstyle]I'm having trouble installing Nvidia Drivers on my Ubuntu system.  I get to the installation screen, but it tells me I need to close X server.  Ive tried changing the init to level 3, but it didnt seem to do anything.  I also tried CTRL ALT BKSP, but that just takes me back to the ubuntu login screen.  What are my options to try at this point?[/QUOTE]Just install linux-restricted-modules.

---

### Post by oddabe19 on 2004-11-27
[QUOTE=animalstyle]I'm having trouble installing Nvidia Drivers on my Ubuntu system.  I get to the installation screen, but it tells me I need to close X server.  Ive tried changing the init to level 3, but it didnt seem to do anything.  I also tried CTRL ALT BKSP, but that just takes me back to the ubuntu login screen.  What are my options to try at this point?[/QUOTE]
 actually, just do a 'sudo /etc/init.d/gdm stop'

then you install the drivers with 'sudo sh NVIDIA-whatever the file is'

then restart the X server with 'sudo /etc/init.d/gdm start'

or search in synaptic for NVIDIA and install what comes up (i think it's nvidia-glx and nvidia-drivers or something like that)

---

### Post by animalstyle on 2004-11-27
Thanks that worked

---

### Post by jdong on 2004-11-27
[QUOTE=daniels]Just install linux-restricted-modules.[/QUOTE]

Sorry, but you guys are a version out of date -- even in Hoary!


Not that I'm a version freak -- the new 6629 release actually *implemented* ACPI support -- both suspend and resume from ACPI working on my Athlon64 desktop! YAY

Now, if only my Toshiba laptop would be so cooperative...

---

### Post by Rancoras on 2004-11-27
jdong, check out my thread about the latest nvidia drivers over in hardware.  daniels pointed me to his development deb archive.  He's got the 6299 driver there, so far it's working great for me. (I needed it for my new 6600GT)

---

### Post by jdong on 2004-11-27
cool, thanks for letting me know!

I've been making home-brew kernels with swsusp2 recently, so haven't been keeping track of Ubuntu kernel's development.

---

### Post by daniels on 2004-11-28
[QUOTE=jdong]cool, thanks for letting me know!

I've been making home-brew kernels with swsusp2 recently, so haven't been keeping track of Ubuntu kernel's development.[/QUOTE]See also Matt Garrett's kernels (probably under srcf.ucam.org/~mjg59 somewhere), which have 2.6.9 + swsusp2.  And we patch in all the acpi.sf.net stuff anyway.

---

