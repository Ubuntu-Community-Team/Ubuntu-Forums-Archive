---
title: "LCD brightness low after suspend"
date: 2009-03-04
forum: Hardware
---

### Post by m4lte on 2009-03-04
Hi there!

When I return from suspend or when entering or exiting a WINE application that changes the screen resolution, the LCD brightness is set to some rather low level. It also happens when I switch to another tty.
However, when I activate the Brightness Applet in the panel, it shows that brightness is still at maximum (where it should be). If I press the keyboard short cut to lower the brightness, brightness is set to the second highest level, as if it had been max before.

This happens when the computer is on AC.
Using gconf-editor I said the brightness for all situations to 100%.

Any ideas how I can avoid these changes in brightness?

p.s.
I run Intrepid 2.6.27-11 on a lenovo thinkpad R400.

---

### Post by mperry on 2009-03-04
This happens to me too on a T500 Lenovo Thinkpad. I don't run Wine applications so for me its when the backlight goes off after awhile on AC power or after suspending. I'd love to know the script or handler to edit to make it come back at 100% on AC. Now I just always hit the Fn-HOME key after those events.

Its one of the few irks in my otherwise zenlike existance :) Wireless could be but I just blast the wifi card every so often with a script I wrote.

Any hints out there on which script is run and where when the laptop comes out of suspend or when the backlight ticks off and I bring it back by striking a key or so?

---

### Post by m4lte on 2009-03-20
I had a look at /proc/acpi/video/VGA/LCD/brightness, which should contains the current LCD brightness value. 
However when I have my display at 100%, set the display to sleep (using /etc/acpi/screenblank.sh) and wake up again, the display is notably darker while the /proc/acpi/video/VGA/LCD/brightness still states 100%!

Since the display returns to it's original brightness once I press the brightness-up/-down buttons on the keyboard, I believe an automated brightness-up command could also solve the problem. So I was thinking to include a script in /etc/acpi/resume.d, which executes something like a brightness-up command. However I don't know how to do 'brightness-up' from the command line. Neither the script /etc/acpi/thinkpad-brightness-up.sh nor /etc/acpi/video_brightnessup.sh. Setting /proc/acpi/video/VGA/LCD/brightness ([http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/](http://www.linuxscrew.com/2007/10/25/ajust-lcd-brightness-from-command-line-works-at-dell-1501/)) also didn't help.

**Which script is executed when I press brightness-up/-down buttons on the keyboard?**

---

