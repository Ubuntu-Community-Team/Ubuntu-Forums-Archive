---
title: "compiz black screen on resume"
date: 2008-10-30
forum: General Help
---

### Post by screaminj3sus on 2008-10-30
I have an ati 2600 mobile. I am running ubuntu 8.10 64 bit. If I have compiz enabled when I resume from suspend I just get a black screen and I have to hold the power button to shut it off. I have tried turing sync to vblank off. It works fine with no compiz. Is there anyway I can get resume working with compiz enabled?

---

### Post by screaminj3sus on 2008-10-31
is there no solution for this??

---

### Post by screaminj3sus on 2008-10-31
anyone?

---

### Post by screaminj3sus on 2008-10-31
I just tried this:
[http://ubuntulinuxtipstricks.blogspot.com/2008/03/ati-nvidia-resume-good-news-bad-news.html](http://ubuntulinuxtipstricks.blogspot.com/2008/03/ati-nvidia-resume-good-news-bad-news.html)

but now I get a black screen with a couple garbled colors...

is there A way I can kill compiz on suspend and start it on resume?

---

### Post by screaminj3sus on 2008-10-31
damnit is there any way to fix this??

---

### Post by screaminj3sus on 2008-11-01
well, gee thanks for the help.

---

### Post by screaminj3sus on 2008-11-01
.....

---

### Post by robertyou on 2008-11-27
Disabling "Sync to VBlank" helped me with this problem.
For Compiz, it's under General Options -> Display Settings

There could be another Sync to VBlank option in your graphic card's setting panel.
Make sure to uncheck both.

Hope this helps :)

---

### Post by screaminj3sus on 2009-02-22
Yes I have vsync disabled everywhere because it doesnt work anyway but that is another issue. Vsync is def disabled in catalyst and compiz.

Is there still no workarounds for this still? I use software like awn that needs a compositer but whenever I have one enabled I can't use sleep.

Using latest ati drivers from ubuntu repo I get a mostly black screen with some garbled colors.

---

### Post by khamil8686 on 2009-03-08
i had a problem where i would suspend my system, come back and hit the power button, it would start up and then when i would finish and enter my password the desktop wallpaper would show, soon go black or it would just start up with a bunch of weird lines on the screen, but it would just hang, sometimes the mouse would move, other times not, was weird. i did some googling and found a post which said to disable visual effects
i have ubuntu 8.10 and goto system>preferences>appearance, click the visual effects tab and then i clicked the radio button next to none, then had no problem with the black screen when resuming, another thing that many people said worked for their particular machine was edit /etc/default/acpi-support and change POST_VIDEO to false, anyways hope this helps out :) i started using ubuntu within a few weeks ago and i had a hard time with this prob so i decided to help out in whatever small way i could :) another thread reply i found was to use Conpiz Config, goto general options>display settings and disable Sync to VBlank

---

