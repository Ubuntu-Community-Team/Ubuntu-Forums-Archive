---
title: "backlight fixes for Samsung laptop w/ nVidia graphics card"
date: 2011-11-18
forum: Hardware
---

### Post by noblepylon on 2011-11-18
I've installed Xubuntu 11.10 on my Samsung R470 laptop.
Unfortunately, I couldn't adjust the brightness level. The display would stay at the brightest level, which would drain out the battery.
Installing samsung-backlight didn't work for me because apparently it doesn't work well with nVidia graphic cards (correct me if I'm wrong).

After some hours of work, I've finally found the fix. Here's what I did. I hope this helps.

1. Install samsung-tools

2. Edit /etc/default/grub
    add "acpi_backlight=vendor" to GRUB_CMDLINE_LINUX_DEFAULT and GRUB_CMDLINE_LINUX

3. Edit /etc/X11/xorg.conf
    add the following line right before EndSection:
        Option "RegistryDwords" "EnableBrightnessControl=1"

4. Install nvidia-bl-dkms and smartdimmer

5. Write shell scripts to change the brightness in some good interval.
   (By default, "smartdimmer -d" changes the brightness by 1, which is tedious.)
   We set the interval 17 so that there would be five steps between 15 and 100.
   
    bright-up.sh
   ```

#!/bin/bash
# raises brightness by some good interval
declare -i interval=17;
declare -i max=100;
declare -i current_brn=`smartdimmer -g | gawk '{ print $3 }'`;

declare -i new_brn=0;
(( new_brn = $current_brn + $interval ));
if (( $new_brn <= $max )); then # within the range (between 15 and 100)
    smartdimmer -s $new_brn;
fi

```bright-down.sh
        ```

#!/bin/bash
# lowers brightness by some good interval
declare -i interval=17;
declare -i min=15;
declare -i current_brn=`smartdimmer -g | gawk '{ print $3 }'`;

declare -i new_brn=0;
(( new_brn = $current_brn - $interval ));
if (( $new_brn >= $min )); then # within the range (between 15 and 100)
    smartdimmer -s $new_brn;
fi

```Save the scripts in, say, your home folder.

6. Associate the shell scripts to keyboard shortcuts.

---

### Post by max69im on 2012-04-03
Thanks a lot! You've saved my day!

It works on Samsung x460 under Ubuntu 10.10 even with external monitor attached.
(i put the "RegistryDwords" in Section "Monitor")

---

