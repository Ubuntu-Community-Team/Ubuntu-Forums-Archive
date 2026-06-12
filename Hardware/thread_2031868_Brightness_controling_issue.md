---
title: "Brightness controling issue"
date: 2012-07-22
forum: Hardware
---

### Post by amin021023 on 2012-07-22
Hey all! 

brieflly: the brightness doesn't change by keys...

Of course I can change it by this command: ```
echo "brightness_value" > /sys/class/backlight/intel_backlight/brightness
``` this way is usefull but hard and ugly...

I want to handle brightness by the defult keys(fn+right and left keys) is there a way to fix this issue...

my graphic is onboard

---

### Post by Toz on 2012-07-22
Which laptop do you have? Onboard intel graphics chip?
Sometimes it helps to add **acpi_backlight=vendor** to the kernel command line.

---

### Post by amin021023 on 2012-07-23
> **Toz said:**
> Which laptop do you have? Onboard intel graphics chip?
Sometimes it helps to add **acpi_backlight=vendor** to the kernel command line.

yes it's intel hd graphics , how do I add those commands? actually I have that issue in pointer speed too...

---

### Post by Toz on 2012-07-23
Try this (from a terminal window):

1. Open the config file for editing (enter password when prompted):
```
gksudo gedit /etc/default/grub
```

2. Search for the line starting **GRUB_CMDLINE_LINUX_DEFAULT=** and add *** acpi_backlight=vendor*** before the last quote so that it looks something like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```

3. Save the file, and rebuild grub:
```
sudo update-grub
```

4. Reboot and test.

If that doesn't work, you could try the same steps but this time adding ***acpi_osi=Linux*** to the mix like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```

Which laptop (make/model) do you have?

---

### Post by Redsandro on 2012-07-24
I have the same problem with my Lenovo Thinkpad Edge 15 after updates. It worked fine before.

I opened [this]("https://bugs.launchpad.net/ubuntu/+bug/1028518") possible related bugreport. Please click "this bug affects me" if you think our problems could be similar.

[https://bugs.launchpad.net/ubuntu/+bug/1028518](https://bugs.launchpad.net/ubuntu/+bug/1028518)

---

### Post by Redsandro on 2012-07-26
Bump

The proposal made by Toz does not work for me.
*Note though that you need to update-grub after those changes before rebooting.*

Any thoughts on this? Launchpad forced me into choosing a package for the bug, but honestly I just don't know.

When you see something *not* happening, it's hard to know what causes it.

---

### Post by Toz on 2012-07-26
> **Redsandro said:**
> Bump

The proposal made by Toz does not work for me.
*Note though that you need to update-grub after those changes before rebooting.*
Thanks for the catch. I'll update my post.

> Any thoughts on this? Launchpad forced me into choosing a package for the bug, but honestly I just don't know.
I would place the bug report against the kernel - the package name would be linux.

I'm noticing a number of threads regarding brightness breaking after updates recently. Have you tried booting previous kernels to see if you can get it to work again? It might be a regression bug against one of the kernels.

---

