---
title: "Mouse suspend on laptop"
date: 2010-10-20
forum: Hardware
---

### Post by Dimon8211 on 2010-10-20
Hi 

Couple of days ago I made new installation of Ubuntu 10.10 on my laptop Samsung R700. All hardware works fine, exept mouse. When laptop works on battery, usb mouse stops working after 2-3 seconds when idle (no red light on optic sensor), I need to press any button on mouse to activate it again. I tried another mouse also. No such problem when laptop on power supply. So looks like some power-management feature of Ubuntu to reduce power consumption. No such prbm with USB flash drives. There wasn't such issue on 10.04
Do anybody know how to switch off this feature?

Thanks for help

---

### Post by P4man on 2010-10-20
Try this; open a terminal and type

```
sudo -i
echo 'options usbcore autosuspend=-1' > /etc/modprobe.d/disable_usb_suspend

```

---

### Post by Dimon8211 on 2010-10-21
No help, still the same.
I tried modprobe disable_usb_suspend, but it says no such module.
Anything else can I do? By the way, I have flash disk with led, led doesn't switch off on it even when no data is transfering.

---

### Post by P4man on 2010-10-21
It doesnt create a loadable module, if my instructions worked it should just create a config file 

/etc/modprobe.d/disable_usb_suspend

which contains

options usbcore autosuspend=-1


Can you verify that was created? You can also try that as kernel option, either by manually adding it in grub, or adding it to /etc/default/grub default options (dont forget to run update-grub after that).

As for the led, thats how most of my sticks behave. LED on when its inserted, and blinking on activity.

---

### Post by Dimon8211 on 2010-10-21
Yes, file had been created. As I understand there should be some module loading for this config file, how to check?

---

### Post by P4man on 2010-10-21
the module is usbcore and it will be loaded or usb wouldnt work. That file ought to pass a parameter to it to disable suspending USB devices, but that doesnt seem to work or help, and im not sure how to check that :(

I just tried

```
sudo modprobe usbcore
```

And I got a warning about that file we created needing a .conf extension. So it does read it here. You could try heading the advice and renaming it
```

sudo mv /etc/modprobe.d/disable_usb_suspend /etc/modprobe.d/disable_usb_suspend.conf
```

and try again. The warning will be gone now, but I doubt it will change anything. 
Perhaps change the -1 to 0 ?

---

### Post by Dimon8211 on 2010-10-21
Thanks for mentioning usb suspend FUNCTION. I searched and found thread in Voria forum regarding it.
http://www.voria.org/forum/viewtopic.php?f=3&t=553"
I installed samsung-tools to make my Fn buttons work. So I simply deleted script from /etc/pm/power.d responsible for usb auto suspend and everything is allright on 10.10

---

### Post by P4man on 2010-10-21
Excellent, well done :)
Dont forget to mark the thread as solved (in thread tools) that may help others find your solution.

---

