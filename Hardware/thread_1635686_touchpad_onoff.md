---
title: "touchpad on/off"
date: 2010-12-02
forum: Hardware
---

### Post by cobra11 on 2010-12-02
I have problem, this script works if i run it with terminal, but why it wont run if i use button keys fn+f9?

```
#!/bin/sh
#find the current state of the touchpad
state=`gconftool-2 --get "/desktop/gnome/peripherals/touchpad/touchpad_enabled"`

#if touchpad enabled, turn it off
if [ $state = "true" ]; then
gconftool-2 --type=bool --set "/desktop/gnome/peripherals/touchpad/touchpad_enabled" "false"
echo "vgasjeno"
fi

#if touchpad not enabled, turn it on
if [ $state = "false" ]; then
gconftool-2 --type=bool --set "/desktop/gnome/peripherals/touchpad/touchpad_enabled" "true"
echo "vklopleno"
fi

```

---

### Post by cobra11 on 2010-12-02
I find solution:

sudo gedit /etc/acpi/asus-touchpad.sh 
and copy:
```
#!/bin/sh
[ -f /usr/share/acpi-support/state-funcs ] || exit 0 

. /usr/share/acpi-support/power-funcs

getXconsole

DEVICE_ID=`xinput -list | grep -i touchpad | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi
```

than
sudo gedit  /usr/share/acpi-support/power-funcs
and delete this:
```
  if [ x"$user" != x"" ]; then
               userhome=`getent passwd $user | cut -d: -f6`
            export XAUTHORITY=$userhome/.Xauthority
    else
        export XAUTHORITY=""
    fi
```
and paste this:
```
export XAUTHORITY=`ps a | grep -v grep | grep X | sed -n 's/.*-auth \(.*\)/\1/p' | cut -f 1 -d ' '`
```

Now i can turn On/Off touchpad on Asus UL30VT in Ubuntu 10.10 :)

---

### Post by CrowMagnumb on 2010-12-02
Thank you, thank you, thank you!!!!

I have tried everything else I could find on the web to new avail.  This finally got rid of my touchpad problem!

My touchpad however was being reported as a wheel mouse ...

```

ken@cuervonido:~/bin$ xinput -list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Macintosh mouse button emulation        	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB-PS/2 Optical Mouse         	id=15	[slave  pointer  (2)]
&#9116;   &#8627; ImPS/2 Logitech Wheel Mouse             	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB 2.0 UVC 0.3M Webcam                 	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
    &#8627; Asus Laptop extra buttons               	id=14	[slave  keyboard (3)]

```
... and so I had to change your script to reflect that.  But I also found I didn't need to mess with the /usr/share/acpi-support folder.  I simply created a script called touchpad.sh that looks like this ...


```

#!/bin/sh

#
#    My touchpad for some reason is being reported as a wheel mouse instead of a touchpad so
#    that is the string I search for to get the deviceid
#
DEVICE_ID=`xinput -list | grep -i "wheel mouse" | grep id= | sed 's/.*id=\([0-9]*\).*/\1/' `

if xinput -list-props $DEVICE_ID | grep "Device Enabled" | grep "1$" > /dev/null
then
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 0
else
    xinput set-int-prop $DEVICE_ID "Device Enabled" 8 1
fi

```

... and then assigned a key to it under System --> Preferences --> Keyboard Shortcuts

Only, I wasn't able to assign the windows key to it as that interface won't let you do that.  So I have the F7 toggle my touchpad and that works fine.

Anyone know how to assign a shortcut key to the windows key?

---

