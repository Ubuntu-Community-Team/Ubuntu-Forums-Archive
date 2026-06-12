---
title: "Dell c540/c640 Fn keys unresponsive under 8.04 LTS"
date: 2009-04-14
forum: Hardware
---

### Post by Cordate on 2009-04-14
Hello helpful Ubuntu folks!

After several years of working with the Ubuntu environment, this is my first foray into working with the OS installed upon a laptop, and I am trying to get a few helpful things working. 

Notably, the Fn keys do not seem to be doing anything in most cases, and my first focus would be the F8 CRT/LCD toggle, as I'd prefer to use a larger screen and toggle off the laptop screen to both conserve energy and screen life.

I have perused several thread on related topics and so have been able to trace something of what happens when this key is pushed, and hope to hook up the correct details at the end of that thread.

Using cat /var/log/acpid, I was able to determine that this Fn-F8 key combination calls  /etc/acpi/video_brightnessdown.sh

The contents of this script are as follows:

```
#!/bin/bash
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_VIDEOOUT
```

And running this only seems able to wake up a monitor I have connected after the OS has fully booted, the screens will not toggle back and forth after I have logged in. They -do- toggle if I push the buttons before the login window appears, however. So it seems the functionality is present but something related to GDM perhaps goofs things up.

I also would like to get the brightness keys working as well, but I suspect those are having a different issue, as there is no sign of a response to those using acpi_listen or cat /var/log/acpid

This machine is a Dell C540/C640 with a tiny lil 32Mb Ati Radeon card in it and it is using the radeon driver.

---

### Post by Cordate on 2009-04-25
Here is a small addition in assistanceto anyone else who may be having similar issues- I am able to get the laptop LCD screen brightness and contrast keys (Fn+Arrow Keys) to work from the first console (CTRL+ALT+F1). Upon returning to the desktop via CTRL+ALT+F7 the screen retains the new settings. This also works under 8.10 Intrepid Ibex, to which I upgraded just this morning.

---

