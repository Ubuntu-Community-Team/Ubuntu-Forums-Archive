---
title: "Wakeup capability of Components beeing disabled at boot"
date: 2012-02-19
forum: Hardware
---

### Post by gumsh on 2012-02-19
I want to wake up my Ubuntu 11.10 system from Suspend.
It works fine on a 10.x distro but i can't get it to work flawlessly und 11.10.

After googling i managed to get a script, that sets the devices i want to wake up the Computer with (USB Remote/Keyboard/LAN), as Wakeup capable.

[PHP]

status=`cat /proc/acpi/wakeup | grep "USB0" | awk {'print $3}'`
 if [ "$status" = "disabled" -o "$status" = "*disabled" ]; then
 echo "USB0" > /proc/acpi/wakeup
 fi
status=`cat /proc/acpi/wakeup | grep "USB1" | awk {'print $3}'`
 if [ "$status" = "disabled" -o "$status" = "*disabled" ]; then
 echo "USB1" > /proc/acpi/wakeup
fi
 fistatus=`cat /proc/acpi/wakeup | grep "USB2" | awk {'print $3}'`
 if [ "$status" = "disabled" -o "$status" = "*disabled" ]; then
 echo "USB2" > /proc/acpi/wakeup
fi
 fistatus=`cat /proc/acpi/wakeup | grep "USB3" | awk {'print $3}'`
 if [ "$status" = "disabled" -o "$status" = "*disabled" ]; then
 echo "USB3" > /proc/acpi/wakeup
 fi
status=`cat /proc/acpi/wakeup | grep "P0P6" | awk {'print $3}'`
 if [ "$status" = "disabled" -o "$status" = "*disabled" ]; then
 echo "P0P6" > /proc/acpi/wakeup
 fi
status=`cat /proc/acpi/wakeup | grep "P0P5" | awk {'print $3}'`
 if [ "$status" = "disabled" -o "$status" = "*disabled" ]; then
 echo "P0P5" > /proc/acpi/wakeup
fi
 fistatus=`cat /proc/acpi/wakeup | grep "P0P4" | awk {'print $3}'`
 if [ "$status" = "disabled" -o "$status" = "*disabled" ]; then
 echo "P0P4" > /proc/acpi/wakeup
fi
 fistatus=`cat /proc/acpi/wakeup | grep "P0P1" | awk {'print $3}'`
 if [ "$status" = "disabled" -o "$status" = "*disabled" ]; then
 echo "P0P1" > /proc/acpi/wakeup
 fi
[/PHP]

after i run these lines as root, everything works fine.

However, the settings don't stay permanent. So i wrote the script into rc.local so that they are executed every boot.

However... Still every device is set to *disabled.

I wondered if there is be a possibility to run the script on SUSPEND to make sure i will be able to wake up the Computer.

2. I would as well like to run a script on wakeup, to make sure certain programs are running (Volumes mounted, pyload)

In addiditon, i'm running XBMCbuntu, which comes with a minimal 11.10 on a Zotac ZBOX ID-41, using it as a HTPC and Media/Download Server. 

Need WOL to wake it when somebody wants to watch media from remote.
And USB to wake it up from remote in HTPC use.

---

