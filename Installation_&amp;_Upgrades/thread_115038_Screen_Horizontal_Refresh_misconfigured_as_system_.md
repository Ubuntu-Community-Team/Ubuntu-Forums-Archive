---
title: "Screen Horizontal Refresh misconfigured as system boots up"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by jrmint on 2006-01-09
Hi All: I've got an xorg issue on boot up. I'm running an IBM ThinkPad T43 and I've installed Breezy Badger. My problem is during the boot up.

When Grub is loading and services are starting (like network interfaces etc) the screen is scrolling out of control. Once X starts and i'm at the gnome sign on the screen is normal.

My question is how do I control the horizontal and vertical during that boot process?

Thanks for the help

---

### Post by southernman on 2006-01-09
[QUOTE=jrmint]Hi All: I've got an xorg issue on boot up. I'm running an IBM ThinkPad T43 and I've installed Breezy Badger. My problem is during the boot up.

When Grub is loading and services are starting (like network interfaces etc) the screen is scrolling out of control. Once X starts and i'm at the gnome sign on the screen is normal.

My question is how do I control the horizontal and vertical during that boot process?

Thanks for the help[/QUOTE]

I don't really see what problem your having. It sounds as if your laptop is just quick on the boot up sequence. If this is a problem for you, I'll send a call out ticket via fedex to have that laptop shipped to me... I'd gladly take it off your hands - free of charge! ;)

At any rate, have a look in /etc/X11/xorg.conf and see if your h & v refresh rates are present and correct. I don't think the refresh rates in your config file would effect the screen during bootup.

---

### Post by jrmint on 2006-01-10
I wish. It's probably around 1.5 to 2 mins to get to command prompt.

I've now changed the start up so that it does not boot into gnome by default but sits at the comman prompt waiting for a text only login.

The screen still scrolls like crazy to the point where it is virtually unreadable.

Any ideas? Does boot loader have a separate monitor config than X?

---

### Post by escape on 2006-03-08
Not to derail, but I also have a similar problem; coincidentally I have a T43, but my issues is when I try to boot with an external LCD display, the refresh rate is at >60Hz until I get to the login screen.  Might this be because I have only one monitor listed in my xorg.conf file?

---

