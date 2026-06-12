---
title: "tablet functions"
date: 2010-09-13
forum: Hardware
---

### Post by DreamPhysix on 2010-09-13
I used Wubi to install Ubuntu 10.04 on my tablet pc.  The installation worked and the OS runs smoothly, but I can't use the touch screen on my tablet.  I have the xorg wacom package installed.  Anyone suggestions?  I have a Fujitsu Lifebook T900

---

### Post by GotDiesel on 2011-01-22
I wish I could help.  I'm having the same problem.  Pen input works fine with 10.10 out of the box.  No multi-touch.  Back to the drawing board...

---

### Post by Favux on 2011-01-22
Hi GotDiesel,

That tutorial you found in a blog didn't work?

If not why don't you start your own thread on the Fujitsu Lifebook T900 and let's see if we can figure it out.

---

### Post by GotDiesel on 2011-02-24
FAVUX, MEGA KUDOS!!!

I followed your post here: [http://ubuntuforums.org/showpost.php?p=6546012&postcount=1](http://ubuntuforums.org/showpost.php?p=6546012&postcount=1) and it worked flawlessly (almost) for a Fujitsu T900 with the multi-touch display.  

The only thing that I had to do was make the xorg.conf file in the etc/x11/ folder.  For some reason I did not have the file at all???
I copied and pasted the xorg.conf text that you posted to create the file and SHAZAAM!!  

Multi-touch Works after re-boot!!

I got the display buttons working with this post: [http://ubuntuforums.org/showthread.php?t=1116103](http://ubuntuforums.org/showthread.php?t=1116103)   with the information provided by sirajperson.

On a side note, the multi-touch with stylus works natively on the upcoming 11.04 Natty release for the T730 and the T900 Lifebook series.  I don't know if I will use that release when it is officially released only because I really don't like the Unity interface.  As of writing this, 11.04 is VERY buggy and highly unstable. (which has to be expected this early in the development)  I will try it again when it is officially released, but I may stick with 10.10 for the time being.

Thanks again UBUNTU community!!

---

