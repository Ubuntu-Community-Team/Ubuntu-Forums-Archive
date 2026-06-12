---
title: "Xorg leaves the laptop unresponsive"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by Nexu on 2007-04-29
Ever since i updated my laptop running Edgy to Feisty. My laptop would 'crash' the moment i start Xorg (hourglass mouse icon forever); all keyboard input seems to be non-responsive, but mouse input still works just as the touchscreen and touchpad. My attempts to kill the X server (ctrl-alt-bcksp) or switching to a tty all failed.
I tried using vesa driver instead of the usual i810. But same symptoms: non responsive keyboard, but mouse input still working.

My laptop is a Panasonic Toughbook CF-18. It's a Centrino based laptop equipped with a Intel 915GM graphics chipset with wireless (which seems to be working fine as i'm using it to connect to the internet to post this atm).

I'm not sure how to proceed. Should i downgrade the X.org with all the dependency conflicts or try to debug it? Is the Xorg binary in Ubuntu even compiled with debugging symbols enabled?

---

### Post by tutomlin on 2007-05-01
Hi,
I'm having a similar problem.  If I boot with the keyboard attached everything goes fine, and the laptop's keyboard even works.  If I boot without the laptop attached,(even if I plug one in after the boot) I get nothing on the keyboard.    

I think the issue is that When I did the upgrade I had a USB keyboard attached, and the upgrade scripts set the USB keyboard to default or something.  I'm in the process of trying to find a way to update the xorg.conf file properly, I'll let you know if I get anywhere.

Cheers.

---

