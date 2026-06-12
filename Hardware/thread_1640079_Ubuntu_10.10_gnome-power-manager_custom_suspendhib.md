---
title: "Ubuntu 10.10 gnome-power-manager custom suspend/hibernation script."
date: 2010-12-07
forum: Hardware
---

### Post by kslen on 2010-12-07
Hello there.

My ASUS EEEPC 1201N netbook suffers from a strange bug which resets BIOS if the brightness isn't set to its maximum setting when rebooting.

What I need to achieve is to run the following command just before hibernation is initiated by gnome-power-manager:
```
/bin/echo -n 15 > /proc/acpi/video/IGPU/LCDD/brightness
```Using the solution proposed on [http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2F1201n.podrozomania.info%2Fcategory%2Fprogramy%2F](http://translate.google.com/translate?js=n&prev=_t&hl=en&ie=UTF-8&layout=2&eotf=1&sl=auto&tl=en&u=http%3A%2F%2F1201n.podrozomania.info%2Fcategory%2Fprogramy%2F) (polish page translated by google. * Original link can be found at the bottom of this post.) works beautifully when shutting down, but is completely ignored when gnome-power-manager suspends or hibernates the machine.

All help is greatly appreciated.

* [http://1201n.podrozomania.info/category/programy/]("http://1201n.podrozomania.info/category/programy/")

---

### Post by meijer.o on 2010-12-07
#!/bin/sh
#
# set brightness
# position /etc/pm/sleep.d/99_suspend

case "$1" in
        hibernate|suspend)
 /bin/echo -n 15 > /proc/acpi/video/IGPU/LCDD/brightness          ;;
thaw|resume)
# do nothing
                ;;
esac

# end script

Make this executable and it should work,

Best regards,

otto Meijer

---

### Post by kslen on 2010-12-07
Thanks a bunch, man. :D

---

