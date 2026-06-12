---
title: "Monitor Brightness Issue"
date: 2016-04-05
forum: Hardware
---

### Post by nfmcclure on 2016-04-05
Hi, I have a Lenovo Y50-70 laptop.  Upon install of ubuntu (dual boot with windows 10), the monitor brightness settings were working great and responded to the hotkeys on the keyboard.

I tried and failed to update the video card drivers to the NVIDIA drivers, so I went back to the Nouveau generic drivers.  Since restoring to the Nouveau drivers, my monitor brightness seems to be stuck at full.

I've tried a few solutions and here is the relevant output for most of those:

```

$ cat /sys/class/backlight/ideapad/brightness 
7


$ cat /sys/class/backlight/ideapad/max_brightness 
16

```

I've tried editing the brightness number and nothing happens (even after a logout or reboot).  I know it's set at 7/16, but the monitor is on it's very brightest right now.  This is the same for any number I give it, even 0.

Here is the relevant part of my grub file:

```

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="nouveau.modeset=0 quiet splash nomodeset pcie_aspm=force acpi_backlight=vendor"
GRUB_CMDLINE_LINUX=""
# GRUB_CMDLINE_LINUX="acpi_backlight=vendor acpi_osi=Linux resume=/dev/sda7"

```


You can see the commented line at the bottom, tried that first, to no avail.

I also tried installing ppa:indicator-brightness, and the indicator seems to work, but the monitor does not respond to any level I set it at.

How can I get the monitor brightness to respond?

---

### Post by Bucky Ball on 2016-04-06
Are you running

> sudo update-grub

... after changing the /grub file? If not, the changes will be gone on reboot so they will make no difference. Things will be as they were prior to changing that file.

You really shouldn't need all that cruft in there, anyway. Might be getting confused with all those options you've inserted there. The /etc/default/grub file is not really the place to be trouble shooting this. I'm presuming you didn't have all those options in there when things were working fine ...

---

### Post by nfmcclure on 2016-04-06
Thank you!

I changed the line in GRUB to:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi_backlight=vendor"

```

And after updating grub it works.  The other stuff must have been left over from trying to get the nvidia drivers running.

---

### Post by Bucky Ball on 2016-04-06
Good news and thanks for marking as solved. Happy travels. ;)

---

