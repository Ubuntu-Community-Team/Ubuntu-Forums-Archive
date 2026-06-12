---
title: "Strange Graphical Error On Laptop"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by Ademan on 2007-01-11
Let me first preface this with some information.  My laptop has been dropped before, nothing has ever come of it.  A few weeks ago i dropped my laptop, since then I have had a graphical error i will describe in a bit.  It's possible that this error coincides with my installing a new driver (NVIDIA 9746), that's what i hope, but unfortunately i'm rather sure this is just broken hardware.

So this is the error:

[[IMG]http://img239.imageshack.us/img239/6868/dscf0940mb8.th.jpg[/IMG]](http://img239.imageshack.us/my.php?image=dscf0940mb8.jpg)

[[IMG]http://img234.imageshack.us/img234/6656/dscf0939ur4.th.jpg[/IMG]](http://img234.imageshack.us/my.php?image=dscf0939ur4.jpg)

[[IMG]http://img184.imageshack.us/img184/2756/dscf0938hu3.th.jpg[/IMG]](http://img184.imageshack.us/my.php?image=dscf0938hu3.jpg)

[[IMG]http://img231.imageshack.us/img231/7170/dscf0937db2.th.jpg[/IMG]](http://img231.imageshack.us/my.php?image=dscf0937db2.jpg)

It occurs when:

I ctrl+alt+f1 to enter a virtual terminal.  Where I can still type, but all i see is what you see above.  I've successfully restarted my computer from there.  I can ctrl+alt+f7 to return to GNOME successfully.

The screensaver comes up

I attempt to play a fullscreen game (i've tried both wolfenstein: enemy territory, and true combat: elite, both of which previously worked)

Those screenshots were all taken at the gdm login, but I can get that "wonderful" effect at any time.

So my question is this:  could it possibly be the new NVIDIA drivers?  Has anyone else had this?  Am i just utterly screwed?  This is a laptop so replacing the video card is out of the question.  Is there any way i could check for and possibly re-sodder a connection?

For the record my laptop is a Sager (sagernotebook.com i believe) which has been sturdy and resisted a few other falls, it's got a pentium M 2.0ghz with 2gb of ram, and a geforce go 6600.  I spent one heck of a lot on this laptop and it's out of warranty, but i do a lot of OpenGL + C++ programming and i NEED a working graphics card (windowed mode works, and is actually better for debugging, but you know what I mean)  So is there any way to fix this?

Thanks a ton,
Dan

---

### Post by Ademan on 2007-01-12
On another note, i just noticed that this occurs whenever an OpenGL context is created as well, this includes WINE, i'm about to try glxgears, which i assume will have the same results.  Any help would be greatly appreciated.

Thanks,
Dan

---

### Post by Ademan on 2007-01-13
I hate to bump myself but this is driving me nuts.  I do programming with OpenGL, but i can't use openGL because it causes this problem.  I'm going to try rolling back my drivers.  But if anyone has any input it would be GREATLY appreciated, i'm dying here.

Thank you,
Dan

---

