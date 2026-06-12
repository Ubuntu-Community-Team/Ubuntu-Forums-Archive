---
title: "Karmic boots up twice not once.  How to fix double booting?"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by ubunny on 2009-11-03
Upon boot, I see the grub boot message hd(1,0) etc then the new ubuntu logo opens up, then there is some flash of text underneath which I can't either read nor find logged anywhere (where is it?).  Then instead of next moving to the login screen it decides to re-boot again, THEN it loads the login window.  Adds about twice the time for every boot up.

If I could view the splash screen message somewhere maybe that would help.  Any idea where that is?  

Why the double bootup?

Also I'd like to note that when I reboot it works quite fast, but if I shutdown it also takes about twice as long as a reboot.  I suppose I can just hit reboot, then on computer POST and before grub I can turn it off, but that's not the point.

*EDIT:
ran update-grub and removed a few older kernels and that got rid of the startup text that I cannot read.  However it still double boots.  Note that previous kernel 28.16 does not double boot but has the new splash screen etc.

---

### Post by jsradley on 2009-11-16
Hi,
Same with me after an upgrade from 9.4 to 9.10
First Grub message is "booting from hd(0,0) ....."
Then a full black screen with a white Ubuntu logo in centre
Then the "booting from hd(0,0) ..." message again.
Then a black screen and eventually a busy mouse icon, and the new graphics boot sequence

Did you fix yours?

Anyone else?

Thanks
John

---

### Post by jsradley on 2009-11-20
Hi,
I eventually fixed mine.
I have multiple hard disks, which previously had been used for booting other version. Seem Grub Legacy was attempting to boot another version first.
Anyway, I upgraded to Grub2 and fixed what HD needs to boot, and all is now fine.

Rgds
John

---

