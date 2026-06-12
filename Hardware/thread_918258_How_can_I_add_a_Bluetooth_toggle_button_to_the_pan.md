---
title: "How can I add a Bluetooth toggle button to the panel?"
date: 2008-09-12
forum: Hardware
---

### Post by lklk on 2008-09-12
I have a Thinkpad x61t and I can toggle wifi and bluetooth with Fn+F5. This cycles through a few different modes and turns of wifi, which annoys me. I want to add a bluetooth toggle button to the Gnome panel. I need help setting up the script and linking it to an icon.

---

### Post by lklk on 2008-09-16
I found this code on thinkwiki.org but I don't know how to make it work. It would be nice to have an icon on the desktop or panel that executes this code.
> 
# cat /etc/acpi/actions/bluetooth
#!/bin/bash
# Bluetooth enable/disable script

/etc/init.d/bluetooth status

if [ "$?" -ne 0 ]; then
        /etc/init.d/bluetooth start > /dev/null
        echo enabled > /proc/acpi/ibm/bluetooth
        echo "Bluetooth enabled"
else
        /etc/init.d/bluetooth stop > /dev/null
        echo disabled > /proc/acpi/ibm/bluetooth
        echo "Bluetooth disabled"
fi

This code is to make the code above execute when Fn+F5 is hit. I can use the key combination but it cycles through different combinations of Wifi on/off and Bluetooth on/off.

> # cat /etc/acpi/events/bluetooth
event=ibm/hotkey HKEY 00000080 00001005
action=/etc/acpi/actions/bluetooth

---

### Post by lklk on 2008-09-16
I figured it out but I had to make separate on/off files.

---

### Post by matjaz on 2008-09-19
Hi,
I am having the same problem ( trying to desable bluetooth / wifi separately ) and i would like to know how you managed to turn off wifi / bluetooth in a script ( i would appreciate if you could post the scripts ).

Does your solution just disable the bluetooth for one session or it stays disabled even after you restart your computer?

I have a Fujitsu v5505 laptop, and i haven't yet figured out how to turn off either bluetooth or wifi, as my wireless swich that was supposed to turn them both off doesn't work in ubuntu.
So what i would like to know if your script can permanently ( until you enable it again ) disable bluetooth - so that you can use your laptop on an aeroplane (where wireless sensors must be shut down)?

---

