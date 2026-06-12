---
title: "Docked Resolutions"
date: 2006-03-03
forum: Hardware &amp; Laptops
---

### Post by marcantonio on 2006-03-03
Hey all,

I just got a docking station for my laptop.  My problem is, the laptop LCD runs at 1600x1200 and the external monitor only runs at 1280x1024.  Does anyone know of a good way to get the correct resolution in both situations?

I'm thinking I'll put a new boot option in grub with something like "DOCKED" at the end and run a script to look for that at startup and use a different xorg.conf file.  I don't like this though, I'd like it to work automagically.

Any thoughts?

Marc

---

### Post by nam.rover on 2006-03-07
[QUOTE=marcantonio]Hey all,

I just got a docking station for my laptop.  My problem is, the laptop LCD runs at 1600x1200 and the external monitor only runs at 1280x1024.  Does anyone know of a good way to get the correct resolution in both situations?

I'm thinking I'll put a new boot option in grub with something like "DOCKED" at the end and run a script to look for that at startup and use a different xorg.conf file.  I don't like this though, I'd like it to work automagically.

Any thoughts?

Marc[/QUOTE]
Marc,

I'm interested in such a solution as well. Did you find a way to choose the different resolutions in the meantime?

I found the following (german) howto. But it's focussing KDE and I did not manage to transfer it on GNOME.

[http://www.hinzke.de/x.org_Config_100_0_0.html](http://www.hinzke.de/x.org_Config_100_0_0.html)

So far

CJ

---

### Post by fireburns on 2006-03-09
This helped me...you need to modify your xorg.conf to denote a dual head environment with two different displays...

[http://gentoo-wiki.com/HOWTO_Dual_Monitors#TwinView](http://gentoo-wiki.com/HOWTO_Dual_Monitors#TwinView)

---

### Post by marcantonio on 2006-03-14
Sorry, I haven't checked my threads in a while...

I got the idea for this from another post, can't find the link though...  Basically, the docking station has a USB hub builtin, so based on the presence of that I set one resolution or another:

Docked:
```

$ lsusb
Bus 004 Device 006: ID 046d:c016 Logitech, Inc. Optical Mouse
Bus 004 Device 005: ID 03f0:0024 Hewlett-Packard
Bus 004 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 049f:0086 Compaq Computer Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

Undocked:
```
$ lsusb
Bus 004 Device 006: ID 046d:c016 Logitech, Inc. Optical Mouse
Bus 004 Device 005: ID 03f0:0024 Hewlett-Packard
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 049f:0086 Compaq Computer Corp.
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

On boot I run this script:

/etc/init.d/xorg-resolution
```

#!/bin/sh -e

set -e

PATH=/sbin:/bin:/usr/sbin:/usr/bin
. /lib/lsb/init-functions
. /etc/default/rcS

DOCKED="no"

docked() {
    if lsusb | grep "NEC Corp. HighSpeed Hub" 2>&1 > /dev/null; then
        DOCKED="yes"
    fi
}

set_x_res() {
    if [ "$DOCKED" = "yes" ]; then
        cp -f /etc/X11/xorg.conf.docked /etc/X11/xorg.conf
    else
        cp -f /etc/X11/xorg.conf.undocked /etc/X11/xorg.conf
    fi
}

set_gnome_res() {
    if [ "$DOCKED" = "yes" ]; then
        cp -f /home/marc/.gconf/desktop/gnome/screen/default/0/docked.xml /home/marc/.gconf/desktop/gnome/screen/default/0/%gconf.xml
    else
        cp -f /home/marc/.gconf/desktop/gnome/screen/default/0/undocked.xml /home/marc/.gconf/desktop/gnome/screen/default/0/%gconf.xml
    fi
}

case "$1" in
    start)
        log_begin_msg "Setting X resolution..."
        docked
        set_x_res
        set_gnome_res
        log_end_msg 0
        ;;
    stop)
        ;;
    *)
    echo "Usage: $0 start"
    exit 1
    ;;
esac

exit 0

```

My two xorg.conf files differ only in the screen section:

/etc/X11/xorg.conf.docked
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection
```

/etc/X11/xorg.conf.undocked
```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200"
	EndSubSection
EndSection

```

Notice that the startup script changes the resolution in Gnome as well.  That's important, but there's probably a better place to do it than on boot.

It's a hack but I works.

Marc

---

