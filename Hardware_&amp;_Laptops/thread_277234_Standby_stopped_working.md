---
title: "Standby stopped working"
date: 2006-10-14
forum: Hardware &amp; Laptops
---

### Post by mbvlist on 2006-10-14
Some time ago, I installed updates, and standby suddenly stopped working. I didn't have time left to investigate, so I went back to windows. Unfortunately some trojan got in and never went out, so I need Linux again ;) 

September 24 was the last day my laptop went to standby smoothly. At that date I did 2 things (which i'll never combine anymore ](*,) ): ran the usual updates, and installed the 686 kernel instead of 386. From that point on, I never got it to work again. My laptop turns of the screen (after showing the screen-saver like it always did), but keeps the fan running.

I'd like to debug this issue a bit. Which log-files do I need, where can I check where the acpi-deamon or so crashes? user.log doesn't tell me anything...

My laptop is a NEC versa P550, in case someone else fixed it last few weeks :)

---

### Post by mbvlist on 2006-10-14
Just to lay the emphasis right: I want to debug this problem, but I don't know where to start. Is there anybody who can point me in the right direction for debugging standby-problems? If all else fails, at code level?

---

### Post by cptnapalm on 2006-10-14
This probably won't be it, but I figured I would toss it out.  Do you have GRUB set the framebuffer?  I ask because (and I'm working off memory) there was some odd conflict between framebuffer and suspend.  Don't ask me why.

For this (which is probably not your problem) check /boot/grub/menu.lst.  Do a search for vga=  That would be the line where it sets the framebuffer.

---

### Post by mbvlist on 2006-10-16
That's unfortunately not the problem. 

I also noticed something else (slightly less annoying): the button in the notification area which showed the battery state, now only shows the logo for 'plugged in', but says 'running on battery'  or so when not plugged in :S When I browse /proc/acpi/battery/BAT0/... I find the right info.

---

### Post by mbvlist on 2006-10-16
Suppose ACPI had some form of meltdown, I can't even read my battery status anymore:mad: . Wasn't linux the OS that never needed a reinstall? ](*,)

---

### Post by mbvlist on 2006-10-20
Nobody who can give me tips on debugging ACPI? 

I found out that my laptop gives the right battery information after changing something to the power configuration: unplug external power, disconnect battery, that sort of thing. 
Is it possible that this has something to do with the DSDT? It just seems strange to me, because it always worked...

[edit]Hmm, that is a common linux 2.6.15 kernel-problem :( [http://bugzilla.kernel.org/show_bug.cgi?id=7200](http://bugzilla.kernel.org/show_bug.cgi?id=7200)
Still no clue about the standby...

---

### Post by mbvlist on 2006-10-24
All right, the fix was easy:
```
$ sudo rmmod fglrx
```
Probably the installation of the 686 kernel installed fglrx in my /etc/modules. This package broke the standby function :mad: 
Now I don't have a problem with the battery anymore: I can boot at home, unplug and replug the power, and see my battery state. 

Now find out why gnome takes ages to boot :(

---

