---
title: "HAL, ACPI and hibernate"
date: 2008-02-12
forum: Hardware &amp; Laptops
---

### Post by ehula on 2008-02-12
I am trying to set up suspend2/tuxonice on my Thinkpad T43p running Gutsy with the Zen kernel and would like to understand the hibernation process better. I am trying to figure out the roles that HAL, ACPI and the hibernate package play, specifically, the role these files play and when:

/etc/acpi/hibernate.sh
/etc/acpi/prepare.d/*
/etc/acpi/resume.d/*
/usr/lib/hal/scripts/*
/etc/hibernate/*.conf

What exactly runs when I do the following:

Select "Hibernate" from the Gnome shutdown?

Select "Hibernate" from the Power Manager button?

Hit Fn-F12 (my laptop's suspend key sequence)?

Is there a good tutorial for this stuff (there should be)? I have been looking but have not been able to piece together all the various bits of information on this topic into a coherent picture.

---

### Post by JonathanRRogers on 2008-02-17
I've been wondering exactly this recently and I don't have a good answer. [This article]("http://www.linux.com/feature/114220") may be a good place to start:


When you run the command "hibernate", various things may happen, such as shutting down services and unloading kernel modules. This can all be configured in various files under /etc/hibernate. Once all the prep work has been done, the command to the kernel to do the actual hibernation is simply writing a value to a file somewhere under /sys.

I suspect that your laptop's suspend key sequence creates an ACPI event similar to power buttons and screen lid switches. Those events are handled by HAL somehow I believe and probably activate gnome-power-manager in a similar way to clicking one of the suspend or hibernate buttons in the GNOME GUI. You can configure those behaviors to some extent in System -> Preferences -> Power Management. I don't know what gnome-power manager does to make the hibernate happen, but I suspect it's similar to what the hibernate script does.

---

### Post by blumagic on 2008-02-19
I have been having problems with my two(2) Dell laptops getting them to suspend and/or hibernate. I have a Dell Latitude D800 and Precision M65. I found this web site very helpful with getting my laptops to suspned/hibernate.

[http://people.freedesktop.org/~hughsient/quirk/index.html](http://people.freedesktop.org/~hughsient/quirk/index.html)

Good luck with your issues.

blu.....

---

