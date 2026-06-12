---
title: "A Few Teething Problems on a Samsung X15plus"
date: 2005-02-08
forum: Hardware &amp; Laptops
---

### Post by lerrup on 2005-02-08
I have just installed Ubuntu on by Samsung and now need some help. If you can tell me where TFM is I'll be happy, but any help would be very useful.
    
  
 

[list=1]
[*]Firstly, the battery hasn't been recognised by the system and the power management doesn't seem to work. I tried the ACPI installation as per the How-to but it doesn't seem to work.  I really want to be able to see how the battery is doing.   Do I need to install anything else.
[*]The screen is very dark and I can't control the brightness at all, which makes things very difficult. Is this a graphics board thing? Its a nVIDIA card just in case it is, but I suspect it may be BIOS based.
[*]It boots very slowly as it stops for ages to configure the network interfaces. My guess is that it is trying to make a connection on the ethernet connection (which isn't connected as the WLAN worked out of the box - bloody brilliant). I have turned it off using the gnome controls, but it keeps turning itself on.  Is there a config file somewhere that needs editing?
[*]How can I get the scroll wheel working on my synaptics touch pad?  Everything else about it works fine.
[*]Finally, a weird one. When I log out to close down the screen goes wonky and seems to be out of sync as it is flickering unreadably.  At some concievable point I might need to close down X and carry on with Linux - how can I stop it?
[/list]Your thoughts would be great on how I can sort this so I can use it more than windows!

---

### Post by jerome bettis on 2005-02-08
1.  type ls -lR /etc/acpi and post up what it says

2.  pretty sure that's a bios thing.  some of my fn keys work, some don't.  i can't figure out why.

3.  you can press control c to stop that.  edit /etc/network/interfaces and remove the line that says auto eth0 (or eth1).  also if you haven't added your wep key and essid in this file that's a good reason why it's not working.

4.  try putting the following in your /etc/X11/XF86Config-4

(backup the file and remove the old touchpad section first)

Section "InputDevice"
        Driver      "synaptics"
        Identifier  "Touchpad"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "LeftEdge" "1700"
        Option      "RightEdge" "5300"
        Option      "TopEdge" "1700"
        Option      "BottomEdge" "4200"
        Option      "FingerLow" "25"
        Option      "FingerHigh" "30"
        Option      "MaxTapTime" "180"
        Option      "MaxTapMove" "220"
        Option      "VertScrollDelta" "100"
        Option      "MinSpeed" "0.06"
        Option      "MaxSpeed" "0.10"
        Option      "AccelFactor" "0.0010"
        Option      "SHMConfig" "on"
        Option      "UpDownScrolling" "on"
        Option      "CircularScrolling" "off"
        Option      "LockedDrags" "off"
        Option      "TouchpadOff" "off"
        #Option      "Repeater" "/dev/ps2mouse"
EndSection


5.  no idea on that one sorry.  something in that XFconfig file isn't right probably.

good luck let us know what happens.

---

### Post by lerrup on 2005-02-09
Thanks for your help.

The output for /etc/acpi is:

total 0
drwxr-xr-x    2 root     root          208 2004-10-23 19:24 actions
drwxr-xr-x    2 root     root           72 2005-02-08 06:53 buttons
drwxr-xr-x    2 root     root          184 2004-10-23 19:16 events

/etc/acpi/actions:
total 20
-rwxr-xr-x    1 root     root          197 2004-10-23 19:31 hibernate.sh
-rwxr-xr-x    1 root     root          112 2004-09-04 21:59 lm_ac_adapter.sh
-rwxr-xr-x    1 root     root         1373 2004-09-04 21:59 lm_battery.sh
-rwxr-xr-x    1 root     root          291 2004-10-23 19:29 shutdown.sh
-rwxr-xr-x    1 root     root          190 2004-10-23 19:29 suspend.sh

/etc/acpi/buttons:
total 0
lrwxrwxrwx    1 root     root           22 2005-02-08 06:41 power.sh -> ../actions/shutdown.sh

/etc/acpi/events:
total 20
-rw-r--r--    1 root     root          183 2004-10-23 19:25 lid
-rw-r--r--    1 root     root           62 2004-09-04 21:59 lm_ac_adapter
-rw-r--r--    1 root     root           58 2004-09-04 21:59 lm_battery
-rw-r--r--    1 root     root          201 2004-10-23 19:24 power
-rw-r--r--    1 root     root          201 2004-10-23 19:25 sleep


I've tried the other stuff, I'll put up a post when I reboot.

---

