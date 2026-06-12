---
title: "Wacom Drivers"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by x02flash on 2008-01-14
Hey, I'm trying to install the drivers for my Wacom Graphire 4, and am really confused

I followed the setup to the ./install point and I keep getting this message

```
root@alex-laptop:/home/alex/Program_Files/wacom/prebuilt# ./install
Installing Wacom man page......
Installed under /usr/share/man/man4

Installing wacom_drv....
WARNING: Can not install Wacom X driver (wacom_drv)
since the proper directory has not been found

You need to compile and install wacom.(k)o manually if your kernel is out of date.

After adding your Wacom tools into /etc/X11/xorg.conf, please restart X server or simply reboot your system to run the new Wacom X driver.

```

Anyone know what to do here?

---

### Post by Yellow Pasque on 2008-01-14
The default Ubuntu drivers don't work? Is this a wacom tablet or something different?
You should just try uncommenting the appropriate lines in /etc/X11/xorg.conf

---

### Post by smilingfrog on 2008-01-22
I find the default drivers don't work. Despite uncommenting xorg.conf
GIMP does not recognise the eraser as different from the stylus, and neither of the pen buttons work.
The tablet I have is a Graphire II, pretty old, but pretty solid. I hate trying to configure it in linux, cause it just never seems to work.

---

