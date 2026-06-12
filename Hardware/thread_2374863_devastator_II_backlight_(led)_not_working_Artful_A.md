---
title: "devastator II backlight (led) not working Artful Aardvark"
date: 2017-10-19
forum: Hardware
---

### Post by oliveriod on 2017-10-19
Hi!

I'm sort of new to Ubuntu (got previous experience with non graphical unix flavors) and prepared a custom PC to run Ubuntu with KVM to test new technologies. Since most work is at night I got a backlit keyboard. It is a Devastator II. Too bad I did not do my homework before buying. The keyboard backlight does not work by default on Zesty Zapus.

After some googling I found  this script and the led was working:

#!/bin/bash

FLAGS=$(xset -q | awk 'NR==2' | awk '{ print $10 }')

if [ "$FLAGS" = ffffe7fe ]; then
    xset -led 3
else
    xset led 3
fi


Now with Artful Aardvark the script is not useful.

This is the error:

Invalid MIT-MAGIC-COOKIE-1 keyxset:  unable to open display ":0"
Invalid MIT-MAGIC-COOKIE-1 keyxset:  unable to open display ":0"

Sure this is related to the adoption of Wayland and could be solved installing the old Xorg but that's not an option (is it?).

Any ideas?

Thanks in advance

Oliverio

---

