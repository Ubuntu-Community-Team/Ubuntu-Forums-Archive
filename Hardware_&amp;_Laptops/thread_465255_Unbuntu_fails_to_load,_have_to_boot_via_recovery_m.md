---
title: "Unbuntu fails to load, have to boot via recovery mode"
date: 2007-06-05
forum: Hardware &amp; Laptops
---

### Post by macmichael01 on 2007-06-05
Hello all.  I have a problem with my ubuntu not loading correctly and having to use recovery mode to run it.  I think it has to do with the crappy graphics card that is in this box.  i have a dell optiplex gx260 and in order to get a better resolution then 640X480 I followed the steps that were located here to fix the problem: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto).  But I cant get it to boot up with out running it is recovery mode.  any suggestions?

---

### Post by syko21 on 2007-06-05
what happens when you try to boot normally?

---

### Post by macmichael01 on 2007-06-05
It freezes.  I think it comes to the Ubuntu splash screen and it does not know how to handle it so it decides to crash Ubuntu.

---

### Post by syko21 on 2007-06-05
when the splash screen comes up hit alt+f1 to see a descriptive output and see if you can catch the error message.

---

### Post by macmichael01 on 2007-06-05
Ok so apparently I was not waiting long enough for ubuntu to load.  When I installed the intel driver fix it said that I would correct the problem of not displaying the boot screen which is not that big of a deal anyways.  I tried alt-f1 but no display comes up which I am assuming b/c the intel driver fix is not loaded until the x server is loaded.

I do have another problem if you would be so kind as to help me out with it.  when I first installed ubuntu I kept getting this error that Hal failed to initialize or something.  Which what I read about, this library helps to load hardware related things and mount things like cd roms, flash drives, and so on... so I tried to uninstall hal and reinstall and nothing happened. next I uninstalled gnome and reinstalled and it seemed to prevent the error message from displaying but I can't get anything to mount such as my cd-rom. Do you know what I can do to fix this and why is this happening?

Thanks for your assistance.

---

