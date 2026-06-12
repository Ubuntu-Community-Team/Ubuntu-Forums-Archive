---
title: "ASUS G51J - HOW to enable hot-keys to change keyboard back-light brightness"
date: 2010-08-05
forum: Hardware
---

### Post by gecka on 2010-08-05
For Lucid only and ASUS MODEL G51J (MB VER.: G60JX - G51JX-SZ050V)

Download attached archive, uncompress and cd to the extracted directory then:

To install: 

```
./install.sh
```

To uninstall:

```
./uninstall.sh
```

**NOTE:** To have the notification of the brightness level, you need [libnotify-bin]("apt://libnotify-bin")

---

### Post by brocktice on 2010-08-20
Thanks, works great on my G51JX-A1. Did you write this up yourself? I tried briefly to write some scripts to link to the hotkeys, which worked fine from the command line, but I ran into setuid issues.

---

### Post by brocktice on 2010-08-20
Also, here's a little script I made for suspending/resuming from RAM. I noticed that the keyboard backlight was staying on. This is a quick hack that's compatible with your scripts here, but it could surely be improved to be a little more polished:

The file is /etc/pm/sleep.d/20_custom-kbd-backlight

```

#!/bin/sh
# File: "/etc/pm/sleep.d/20_custom-kbd-backlight".
BRIGHTNESSFILE=/tmp/kbd-brightness

case "${1}" in
        hibernate|suspend)
    STATUS="`cat /sys/devices/platform/asus_laptop/leds/asus::kbd_backlight/brightness`"
    STATUS=$(($STATUS-128))
    echo $STATUS > $BRIGHTNESSFILE
    for i in `seq 0 $STATUS`; do
        /etc/acpi/asus-kb-brightness-down.sh
    done
        ;;
        resume|thaw)
    if [ -f $BRIGHTNESSFILE ]; then
        STATUS=`cat $BRIGHTNESSFILE`
    else
        STATUS=2
    fi

    for i in `seq 0 $STATUS`; do
        /etc/acpi/asus-kb-bright
    done
        ;;
esac

```

---

### Post by grwilmoth on 2010-10-01
The script worked for me in Mint. Thank you very much.

---

### Post by jhash on 2010-10-11
Omg i love you

---

### Post by rsansores on 2010-10-16
THANKS!!!!! I was waiting a lot for this fix. Anyone have the front mic of this asus working? Is the last thing that I need to fix to have a flawlessly ubuntu instllation in my ASUS.

---

### Post by zephyr707 on 2011-04-06
awesome, thanks.  just spent the whole day trying to fix the suspend/hibernate issue and these flashing lights were driving me insane.  thanks!

---

