---
title: "Can't adjust screen brightness on Macbook Pro 8.3, Oneiric"
date: 2011-12-26
forum: Hardware
---

### Post by kc600 on 2011-12-26
It's like this guy says: [http://askubuntu.com/questions/90640/screen-brightness-on-new-macbook-pro-8-3](http://askubuntu.com/questions/90640/screen-brightness-on-new-macbook-pro-8-3)

2011 8.3 MacBook Pro running 64bit 11.10.

The screen brightness keys seems to actually do things (i see the Ubuntu-style indicators in the top right part of the screen when a button is pressed), but nothing actually changes with regard to actual laptop screen brightness.

Is this a known issue? How can I adjust the screen brightness on my MacBook Pro?

I tried ```
sudo echo 4 > /sys/class/backlight/acpi_video0/brightness
``` but got ```
permission denied
```. Doing ```
echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness
``` doesn't give the permission error, but has no effect that i noticed. 

I installed pommed which also didn't change anything. (Or do i have to manually install key bindings after installing pommed?)

---

### Post by DocteurX on 2011-12-26
This is not only a problem for the Macbook Pro 8.3, I'm running Ubuntu 11.10 64bit on Macbook Pro 8.2 and I have the same problem.

---

### Post by DocteurX on 2012-03-27
Screen brightness now work on Macbook Pro 8.2. 

Probably because of some recent update, yesterday I rebooted and sceen brightness adjestment now works perfeclty.

---

### Post by DocteurX on 2012-06-13
Sorry about my previous message, brightness adjustment worked only for a day, it stopped working at the next reboot....

Nevertheless, here is a solution for Macbook Pro 8.2 :

( it's taken from [https://help.ubuntu.com/community/MacBookPro8-2/Oneiric](https://help.ubuntu.com/community/MacBookPro8-2/Oneiric) )

```

sudo add-apt-repository ppa:sforshee/apple-bl-gmux
sudo apt-get update
sudo apt-get install apple-gmux-dkms
sudo modprobe -r apple_gmux
sudo modprobe apple_gmux

```

Then in the file /etc/default/grub, add the following ligne 
```
acpi_backlight=vendor
```

Reboot and enjoy.

---

