---
title: "laptop screen brightness"
date: 2012-11-11
forum: Hardware
---

### Post by cqc on 2012-11-11
i have a dell laptop, inspirion n5050 and every time i boot it screen brightness is set to max, while i want to be on the lowest settings. How can i make it to remember my last time settings? and can i make it to set brightness on max when it is pluged on charger and to set brightness on low when battery is present?
cheers
Core i3 and Intel hd 2000 using Ubuntu 12.10 unity

---

### Post by Toz on 2012-11-11
The first step is to determine what brightness values you want for "high" and for "low".

To identify which backlight interfaces you have (and their current settings), open a terminal window and run this command:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; cat $interface/actual_brightness; done
```
...this will list what backlight interfaces you have and the values of some of the settings.

As an example, my results are:
> $ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; cat $interface/actual_brightness; done
/sys/class/backlight/acpi_video0
24
24
24

...The interface name is **acpi_video0**, the brightness value is **24**, the max_brightness value is **24** and the actual_brightness value is **24**.

Run this command once when you have is set at "high" brightness and once when you have it set at "low" brightness. Save the results somewhere (feel free to post them back here if you need help interpreting the results).

To answer your questions:
> set brightness on max when it is pluged on charger
> set brightness on low when battery is present
Create a file called /etc/pm/power.d/zbattery_mode:
```
gksu leafpad /etc/pm/power.d/zbattery_mode
```
...with the following contents:
```

#!/bin/sh

. "${PM_FUNCTIONS}"

case $1 in
    true) #laptop_mode_battery 
        echo XX > /sys/class/backlight/YY/brightness
        ;;
    false) #laptop_mode_ac 
        echo ZZ > /sys/class/backlight/YY/brightness
        ;;
esac
```
...change XX to to the value of the lower brightness setting, ZZ to the value of the highest brightness setting, and YY to the value of the real backlight interface name (all obtained from the command you ran above).

Save the file and make it executable:
```
sudo chmod +x /etc/pm/power.d/zbattery_mode
```
Now when you plug and unplug the laptop, the brightness should change accordingly.

> How can i make it to remember my last time settings
There are two ways to do this. The easy way, is to have it permanently boot to the same brightness value. Once you have figured out the brightness value that you want, add to your /etc/rc.local file above the *exit 0* command:
```
gksu leafpad /etc/rc.local
```
...this:
```
echo XX > /sys/clas//backlight/YY/brightness
```
...where XX is the brightness value and YY is the backlight interface name.

Save the file. On every boot, the brightness should be set to this value.

The second option is more complicated and will require a script to be written that saves the current brightness value to a file and re-reads on boot.

---

### Post by cqc on 2012-11-12
> **Toz said:**
> The first step is to determine what brightness values you want for "high" and for "low".

To identify which backlight interfaces you have (and their current settings), open a terminal window and run this command:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; cat $interface/actual_brightness; done
```
...this will list what backlight interfaces you have and the values of some of the settings.

As an example, my results are:

...The interface name is **acpi_video0**, the brightness value is **24**, the max_brightness value is **24** and the actual_brightness value is **24**.

Run this command once when you have is set at "high" brightness and once when you have it set at "low" brightness. Save the results somewhere (feel free to post them back here if you need help interpreting the results).

To answer your questions:


Create a file called /etc/pm/power.d/zbattery_mode:
```
gksu leafpad /etc/pm/power.d/zbattery_mode
```
...with the following contents:
```

#!/bin/sh

. "${PM_FUNCTIONS}"

case $1 in
    true) #laptop_mode_battery 
        echo XX > /sys/class/backlight/YY/brightness
        ;;
    false) #laptop_mode_ac 
        echo ZZ > /sys/class/backlight/YY/brightness
        ;;
esac
```
...change XX to to the value of the lower brightness setting, ZZ to the value of the highest brightness setting, and YY to the value of the real backlight interface name (all obtained from the command you ran above).

Save the file and make it executable:
```
sudo chmod +x /etc/pm/power.d/zbattery_mode
```
Now when you plug and unplug the laptop, the brightness should change accordingly.

I tried and it did not work. Now this is the actual brightness command
```
~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; cat $interface/actual_brightness; done
/sys/class/backlight/acpi_video0
0
15
0
/sys/class/backlight/intel_backlight
306
4882
287
~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; cat $interface/actual_brightness; done
/sys/class/backlight/acpi_video0
15
15
15
/sys/class/backlight/intel_backlight
306
4882
4882

```
First out is for the lowest settings and the second one is for the highest. As you can see value is 15. So i changed settings accordingly
```
#!/bin/sh

. "${PM_FUNCTIONS}"

case $1 in
    true) #laptop_mode_battery 
        echo 0 > /sys/class/backlight/15/brightness
        ;;
    false) #laptop_mode_ac 
        echo 15 > /sys/class/backlight/0/brightness
        ;;
esac
```
Maybe i have written wrong values? and i used gedit for editing file.

---

### Post by Toz on 2012-11-12
The script should read:
```
#!/bin/sh

. "${PM_FUNCTIONS}"

case $1 in
    true) #laptop_mode_battery 
        echo 0 > /sys/class/backlight/**acpi_video0**/brightness
        ;;
    false) #laptop_mode_ac 
        echo 15 > /sys/class/backlight/**acpi_video0**/brightness
        ;;
esac
```

Do the following manual commands change the brightness for you?
```

echo 0 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

---

### Post by cqc on 2012-11-12
great it works! Thanks a lot! Its  to bad i could not do this from gui. There are very litle options in unity.

---

### Post by vwaj on 2013-01-03
Thank you!  This was helpful for me too.

---

