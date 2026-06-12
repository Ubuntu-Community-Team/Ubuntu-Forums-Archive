---
title: "Determing Dock Status with Dell E-Port"
date: 2012-08-22
forum: Hardware
---

### Post by thenanodude on 2012-08-22
I have a Dell Lattitude E6420 and a Dell E-Port docking station.  I had some trouble initially getting my external DVI monitors to work when the laptop was plugged into the E-Port, but I eventually figured out that I needed to disable the Optimus support in the BIOS.  Now, with Optimus support disabled, one of my external monitors is automatically detected when plugged in.  I can run nvidia-settings to enable the second monitor after I log in, but this is sort of a pain to do every time, and I'm thinking there must be an automatic way to enable this.  

The solution seems straightforward:  at some point in the boot up or login process, check to see if the laptop is docked, then if it is, run nvidia-settings or xrandr to enable both monitors.  The problem is this:  I cannot figure out how to determine whether the laptop is docked.  I have seen three solutions:

1.  look in /sys/devices/platform/ for "dock" files.  ([https://sites.google.com/site/moosyresearch/thinkpadt61x#TOC-Udev-dock-events](https://sites.google.com/site/moosyresearch/thinkpadt61x#TOC-Udev-dock-events))
However, these files do not exist in this folder or any others I can find.

2. look in /proc for devices that only exist when docked ([http://superuser.com/questions/90657/find-out-if-laptop-is-docked-in-linux](http://superuser.com/questions/90657/find-out-if-laptop-is-docked-in-linux)).  The suggested command to do this is `tail -1 /var/run/stab | cut -d ":" -f 1`

However, the file /var/run/stab does not exist.

3. use xrandr -q ([http://it-tactics.blogspot.com/2010/08/ubuntu-1004-with-docking-station.html](http://it-tactics.blogspot.com/2010/08/ubuntu-1004-with-docking-station.html)).

However, this does not seem to return the useful information as indicated in the blog post.

So, the question is:  how can I automatically determine whether my laptop is docked?!

With some poking, I can probably figure out the answer to the next question, but if anybody has a quick answer, I would appreciate it:  Once I determine the laptop is docked, how do I use nvidia-settings or xrandr to enable the second display?

incidentally, when docked, 'xrandr -q' returns:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1600 x 900, current 3200 x 900, maximum 3200 x 900
default connected 3200x900+0+0 0mm x 0mm
   1600x900       50.0     51.0  
   3200x900       51.0* 

```

also, after I use nvidia-settings to enable the second monitor, it will save an xorg.conf (I know this isn't used any more) configuration with the relevant sections:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "NVS 4200M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: NULL, DFP-1: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1600+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by djurny on 2013-07-11
although this is an ancient thread, i had the same question.. came up with the following relatively simple solution.. turns out the dell e-port replicator (or at least the one i'm using) can be spotted as a usb device:
```
ID 413c:2513 Dell Computer Corp. internal USB Hub of E-Port Replicator
```

then all you would have to do is choose where you want a "state"-like file and create a udev rule for it:
```
## ID 413c:2513 Dell Computer Corp. internal USB Hub of E-Port Replicator
SUBSYSTEM=="usb", ACTION=="add|remove", ENV{PRODUCT}=="413c/2513/*", RUN+="/usr/local/lib/udev/dock-action $env{ACTION}"
```

i chose to have a simple script (not the most elegant thus far) to handle the udev event:
```
#!/bin/bash

DOCK_BASE="/var/run/dock"
DOCK_STATE="${DOCK_BASE}/state"

case "${1}" in
"add") 
        STATE="docked"
        ;;
"remove")
        STATE="undocked"
        ;;
*)
        STATE="unknown"
        ;;
esac

mkdir -p "${DOCK_BASE}"
chmod 0755 "${DOCK_BASE}"

printf "state:\t%s\n" "${STATE}" > "${DOCK_STATE}"
chmod 0644 "${DOCK_STATE}"

# EOF
```

to enable the udev rule, copy it to /etc/udev/rules.d..

with the udev rule, you can simply cat /var/run/dock/state and check dock status..

alternatively, if this is a bit too much :) you can also simply use:
```
## snip
lsusb -d 413c:2513 >/dev/null 2>&1
if [ "$?" -eq '0' ]
then
[INDENT]echo "docked"[/INDENT]
else
[INDENT]echo "NOT docked"[/INDENT]
fi
## snip
```

for the monitor problem, bear in mind that you should both check for docked status and for "connected" status of your externally connected monitors.. when the dock appears, it's not guaranteed that the monitors have been detected already.. 

(look into udev rule for a "drm" subsystem "change" event, this one is specifically for the dell lattitude e5430 i'm currently using, your mileage may vary)

```
## KERNEL[4954.956080] change   /devices/pci0000:00/0000:00:02.0/drm/card0 (drm)
SUBSYSTEM=="drm", ACTION=="change", RUN+="/usr/local/lib/udev/monitor-action $env{ACTION}
```

hope this helps

---

