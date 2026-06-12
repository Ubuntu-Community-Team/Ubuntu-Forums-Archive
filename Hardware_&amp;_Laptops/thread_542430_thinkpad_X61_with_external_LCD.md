---
title: "thinkpad X61 with external LCD?"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by zeus77 on 2007-09-03
i'm curious if anyone has succeeded in getting the (relatively new) Thinkpad X61 working with an external LCD under Feisty?

Out of the box, it is well-documented that the installer selects the vesa driver, as the X61 uses the newish Intel 965GM/X3100 graphics card which is not supported under Feisty.  There have been some success stories reported in getting the latest Intel graphics drivers to run under Feisty, however these solutions require running the Gutsy kernel... and I'm a little leery of using a kernel from a distro that's in alpha, as this is my primary system.  

Does anyone know of a way to get an external display to work with the vesa driver?  Or some other method that doesn't rely on the Gutsy kernel?  It does sort of work on the external monitor, but I can't get it to display the right resolution of 1680x1050.  Even though I've added those resolutions to /etc/X11/xorg.conf, it only loads up in 1280x1024.

Any help would be much appreciated!
Thanks,
zeus77

---

### Post by mrmikerich on 2007-09-04
I have a very similar problem with a T61 under Gutsy, so I don't think moving to Gutsy is the answer.

---

### Post by zeus77 on 2007-09-04
doesn't seem possible with the vesa driver.  thus, i installed the intel driver available here
  [http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)
and it worked fine (after i put the appropriate resolutions in xorg.conf).

---

### Post by victorgreen on 2007-10-16
how did you edit xorg.conf to get it working?

I have the right drivers already backported from Gutsy but for the life of me couldnt get an external lcd working!!

---

### Post by SorryGoFish on 2008-03-23
I'm also hoping to get this working. I have the latest Gutsy Kernel but need some xorg.conf help or something to get 2nd screen to work.

---

