---
title: "LCD backlight not turning off during screensaver on Dell laptop"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by WebDrake on 2007-05-05
I've got a rather worrying problem with Ubuntu on my Dell Inspiron 8600.  This occurs both with 7.04 and 6.10: the LCD backlight will not turn off during a blank-screen screensaver.

I have set  Option "DPMS" "true" in the Monitor section of xorg.conf, and in /etc/default/acpi-support the options USE_DPMS and RADEON_LIGHT are both set to true.

Can anyone advise on further measures to take?  I remember trying xscreensaver but this did not work.

---

### Post by huygens on 2007-05-16
There is a known problem with the Dell LCD backlight and Ubuntu.
I have tried to explain it and solve it in an article. You can find my blog post [presenting the article on Ubuntu and Dell LCD backlight]("http://www.berthon.eu/ice_and_fire/?p=84").
I hope this can help you solving your problem.

In short, this guide will solve the problem that Ubuntu cannot control properly the LCD brightness on Dell laptop. I propose at the end to remove the screensaver blank screen and dim the screen instead.

---

### Post by robbie75 on 2007-07-11
Hi huygens,
I've tried your patch and everything seemed ok (I wrote my
experience on launchpad too) but now I've found something
that's wrong: after a suspend to ram my backlight dosn't
turn off anymore :-(
I'm on a dell 500m...

---

### Post by robbie75 on 2007-07-21
Ok, after some days keeping eys on that, I've found
a workaround: actually, the problem is not the dell lcd
support in hal but the lidswitch, in fact if I suspend/hibernate
through gnome-power-manager or my Fn keys everything
works ok.
Moreover, sometime, I've experienced weird behaviors while
suspending/resuming and one time i've found my notebook resumed
while it's still in the bag! :-|

So, i've changed the lidswitch event not to hibernate/suspend and
choosing suspend/hibernate by fn keys or gpm now it's reliable.

Cheers
Roberto

---

### Post by huygens on 2007-07-23
I cannot investigate this issue anymore as I do not have my Del Laptop anymore. Actually, I do not have a laptop any longer...
I'm sorry that I cannot help you further :-(

---

