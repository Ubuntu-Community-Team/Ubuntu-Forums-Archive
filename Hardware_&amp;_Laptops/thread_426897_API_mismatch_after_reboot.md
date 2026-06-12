---
title: "API mismatch after reboot"
date: 2007-04-28
forum: Hardware &amp; Laptops
---

### Post by jpcunha on 2007-04-28
I just installed nvidia drivers using:

sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable

and changed the driver option on xorg.conf to 'nvidia'

It worked great.. but when i reboot my pc and start kubuntu i get:

"the Nvidia kernel module has the version 1-0-7184 but this X module has the version 1.0.9631"

any ideas??

---

### Post by simonn on 2007-04-29
Let me guess, you had previously tried to install the drivers from nvidia's site?

Basically, when using the restricted drivers, a temporary file system (which uses a ram disk) is mounted to /lib/modules/[kernel]/volatile and the restricted drivers are copied to it. If you install the drivers from nvidia's site when the restricted modules are installed then they will be paritially installed to the temporary file system. Because the temporary file system is in RAM, it gets lost on a reboot.

IMHO, probably the easiet way to fix this is to:

Make a backup copy of your xorg.conf (if it worked before, which I assumed it does).

Uninstall the restricted modules and nvidia drives:

```

$ sudo apt-get --purge remove linux-restricted-modules-$(uname -r) nvidia-glx nvidia-kernel-common

```

Swap back to the nv driver.

Download the latest drivers from the nvidia site and install them:

```

$ sudo sh /path/to/NVIDIA????.run

```

However, if you need other drivers in the restricted modules package, uninstall the same packages as above. Hunt down the old nvidia files and mv them to a directory out of the way rather than deleting them so if you accidentally move the wrong file you can move it back. This can be long and laborious, but using commands like the following can help:

```

$ find /usr/X11R6 -name "*nvid*"
$ find /usr/lib -name "*nvid*"
$ find /usr/X11R6 -name "*9631*"
$ find /usr/lib -name "*9631*"
$ find /usr/X11R6 -name "*7184*"
$ find /usr/lib -name "*7184*"

```

Then, reinstall the packages you just uninstalled.

Once the drivers are reinstalled backup the default xorg.conf and restore your old working one.

---

### Post by bimargulies on 2007-04-30
I want to accomplish the opposite -- to remove all traces of the driver from the nv site and just run the standard distro. How?

---

### Post by donmiguel on 2007-09-11
yeah, i'd also like to know that! :) how could this be acomplished?

i want to remove all the nv-site driver traces so that the resticted drivers module would just work and not cause an api-mismatch... how do i know which ones?

thanks for any reply

---

