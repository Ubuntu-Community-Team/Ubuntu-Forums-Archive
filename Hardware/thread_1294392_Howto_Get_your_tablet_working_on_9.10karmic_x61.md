---
title: "Howto: Get your tablet working on 9.10/karmic x61"
date: 2009-10-18
forum: Hardware
---

### Post by tatewaki on 2009-10-18
Well I upgraded to the newest ubuntu Karmic, and yes I know it's a beta, so I knew that my tablet function might be lost. And yes i lost it. But here is how you can get it to work! Also note this will work on 9.04 too.

First you need to install the wacom tools
```
sudo aptititude install wacom-tools
```

Next we would like to be able to rotate our tablet and the stylus should follow. You do this with the following scripts:

Make the following file here: /etc/acpi/events/lenovo-rotate-normal
```

# /etc/acpi/events/lenovo-rotate-normal
# This is called when the user rotates the screen to laptop mode

event=ibm/hotkey HKEY 00000080 0000500a
action=/etc/acpi/thinkpad-rotatescreen.sh right

```

Make the following file here: /etc/acpi/events/lenovo-rotate-tablet
```

# /etc/acpi/events/lenovo-rotate-tablet
# This is called when the user rotates the screen to tablet mode

event=ibm/hotkey HKEY 00000080 00005009
action=/etc/acpi/thinkpad-rotatescreen.sh normal

```

Now we need to find our stylus. You do that with the following command:
```

hal-device | grep Wac

```

You should get some tekst that looks like this:
```

info.product = 'Wacom Serial Tablet PC Pen Tablet/Digitizer'  (string)
info.product = 'Wacom Serial Tablet PC Pen Tablet/Digitizer eraser'  (string)
pnp.description = 'Wacom Serial Tablet PC Pen Tablet/Digitizer'  (string)
info.product = 'Wacom Serial Tablet PC Pen Tablet/Digitizer'  (string)

```

Now copy/write down the first product eg. 'Wacom Serial Tablet PC Pen Tablet/Digitizer'

And now you make the following file here: /etc/acpi/thinkpad-rotatescreen.sh
```

#!/bin/sh
#
# This script rotates the display in TabletPCs when screen is changed from
# laptop to tablet mode, or when rotation button is pressed

test -f /usr/share/acpi-support/key-constants || exit 0

. /usr/share/acpi-support/power-funcs

# i'm not trusting this ...
#if [ -f /var/lib/acpi-support/screen-rotation ] ; then
#  ROTATION=`cat /var/lib/acpi-support/screen-rotation`
#fi

# ... and thus calling this with a parameter
ROTATION="$1" # this should be called "ROTATION_FROM"

case "$ROTATION" in
	right)
	NEW_ROTATION="normal"
	NEW_WACOM="none"
	;;
	*)
	NEW_ROTATION="right"
	NEW_WACOM="cw"
	;;
esac

for x in /tmp/.X11-unix/*; do
	displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
	getXconsole;
	if [ x"$XAUTHORITY" != x"" ]; then
	    export DISPLAY=":$displaynum"           
	    /usr/bin/xrandr -o $NEW_ROTATION && echo $NEW_ROTATION > /var/lib/acpi-support/screen-rotation

	    # rotate the stylus
	    for type in stylus eraser cursor ; do
		/usr/bin/xsetwacom set 'Wacom Serial Tablet PC Pen Tablet/Digitizer'
 rotate $NEW_WACOM
	    done

	    # rotate the arrow keys
	    case "$NEW_ROTATION" in
		right)
			xmodmap - <<END
keycode 114 = Up NoSymbol Up NoSymbol Up
keycode 111 = Left NoSymbol Left NoSymbol Left
keycode 116 = Right NoSymbol Right NoSymbol Right
keycode 113 = Down NoSymbol Down NoSymbol Down
END
			;;
		*)
			xmodmap - <<END
keycode 111 = Up NoSymbol Up NoSymbol Up
keycode 113 = Left NoSymbol Left NoSymbol Left
keycode 114 = Right NoSymbol Right NoSymbol Right
keycode 116 = Down NoSymbol Down NoSymbol Down
END
			;;
	    esac
	fi
done

```

Remember to change the 'Wacom Serial Tablet PC Pen Tablet/Digitizer' to the one you got. 

Now the last thing you need to do is make the script executable.

```

chmod +x /etc/acpi/thinkpad-rotatescreen.sh

```

Now restart your tablet and your tablet should work.

This was tested on a Lenovo x61 but it should work for other tablets.

Credits for the scripts go to [http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_an_X61_Tablet]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_an_X61_Tablet")

---

