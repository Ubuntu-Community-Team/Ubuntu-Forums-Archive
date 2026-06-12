---
title: "Replacing Graphics Card"
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by renzokuken on 2006-03-01
OK, so my new nVidia card just arrived (wahey!!) and just want to make sure of the following before i go poking around inside my PC.

do i just ....

"sudo dpkg-reconfigure xserver-xorg" and select a generic driver, **vesa** i guess is the one (???), (currently using the fglrx ATI driver).

power down and take my old Radeon card, put in the new nvidia one then power back up and follow one of the guides in here to install the nVidia drivers????

thanks, any advice would be really helpful...

---

### Post by encompass on 2006-03-01
Actually if you just put that card in I think you should be fine... it will error out or work, somehow.  Then select the driver from there.  Vesa is a fall back driver... but I should try automatix or some howto to get the driver working with the correct drivers.  Hope that helps...
If you try to book and it doesn't error out to console but crashes out... boot into single user (recovery) mode to set up the driver there with that command you said.

---

### Post by taurus on 2006-03-01
Edit your /etc/X11/xorg.conf and replace whatever driver that you use for your ATI with "nv."  Shutdown your machine.  Remove ATI and put in nVidia.  Reboot and hopefully, X would be happy with it.  Otherwise, run "sudo dpkg-reconfigure xserver-xorg" to configure X again...

---

