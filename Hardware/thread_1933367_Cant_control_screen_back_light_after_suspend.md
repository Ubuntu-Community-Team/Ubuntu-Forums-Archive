---
title: "Cant control screen back light after suspend"
date: 2012-02-29
forum: Hardware
---

### Post by Kardel on 2012-02-29
HI guys any help with this one would be really appreciated. I have a Toshiba Z830/00G laptop what allows me to control the back light of the LCD screen. This all works fine when i first turn my computer on. 

The problem i am having is that when i suspend the computer and the start running it again i am no longer able to adjust the screen brightness. It shows in the GUI that i am adjusting it but does not actually dim or brighten the screen.

---

### Post by linux_one on 2012-04-03
answer from: [http://www.linlap.com/wiki/toshiba+portege+z830-10f](http://www.linlap.com/wiki/toshiba+portege+z830-10f)
Screen:
The fn keys that control the brighness work as long as the laptop does not get suspended. If the laptop is suspended then upon resumeing the fn keys no longer work. The fix is as follows:
add

acpi_backlight=vendor
to /etc/default/grub under GRUB_CMDLINE_LINUX_DEFAULT. This will remove the acpi_video0 from /sys/class/backlight/ leaving you just with intel_backlight and toshiba. Upon resuming with these settings the screen will be completely black with no means of making it brighter. To fix this one needs to create and add the following to /etc/pm/sleep.d/restore_brightness:

#!/bin/bash
case "$1" in
   suspend|hibernate)
      #do nothing
   ;;
   resume|thaw)
      echo 7 > /sys/class/backlight/toshiba/brightness
   ;;
   *)
      exit 1
   ;;
esac
exit 0

Don't forget to chmod +x the script. You should now have a trouble free laptop :)

---

### Post by Alex1770 on 2012-05-20
Thanks for that. Don't forget to run
```
sudo update-grub
```
after editing /etc/default/grub, and then reboot.

---

