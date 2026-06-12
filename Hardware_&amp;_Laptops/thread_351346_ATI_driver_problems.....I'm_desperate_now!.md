---
title: "ATI driver problems.....I'm desperate now!"
date: 2007-02-01
forum: Hardware &amp; Laptops
---

### Post by gfahey on 2007-02-01
OK, I uninstalled the fglrx driver via synaptic. I downloaded ATI's newest (8.32.5) driver on my desktop. I rebooted. Now I am at the command line as it won't boot to the GUI. I type in:

sh ./ati-driver-installer-8.32.5.run

And get "No such file or directory"

Am I navigating to the desktop here or what is the correct command to install the driver I downloaded to the desktop? I could use some help here. Pronto.

Thanks

---

### Post by empthollow on 2007-02-01
try this before your command
```
sudo chmod +x ati-driver-installer-8.32.5.run 
```
sometimes after you download the file you have to reset the execute permission on it

---

### Post by gfahey on 2007-02-01
Thanks. Tried that with same results. Get same error.

---

### Post by Patrick-Ruff on 2007-02-01
you tried "ls" and actually making sure you had the correct filename right?

also, why don't you install via synaptic or apt-get?

---

### Post by gfahey on 2007-02-02
Yeah, everything's correct. I'm still stuck at the command line unable to enter the GUI.

---

### Post by huocp on 2007-02-02
ati uses a graphic installer.
To make Xorg work again, edit /etc/X11/Xorg.conf, change the driver from "fglrx" to "ati".

Now you can start Xorg, and run the ati installer.

---

### Post by red0menace on 2007-02-05
You can also use the "--buildpkg Ubuntu/edgy" arguments I believe, and that will download and build the packages for you.  Here are is a post (for Dapper, but should work with edgy too):

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

---

### Post by ctt1wbw on 2007-02-06
I followed these directions and it works:

Install from ati.com (latest version of drivers)
Instructions for 6.10 (Edgy)

    *

      Download what's needed:
    *

      Download the appropiate drivers from [WWW] ati.amd.com. You will need the ATI Driver Installer, not the separate XFree86/X.org rpm packages. Save the installer into an empty directory (or at least one containing no *.deb files), since it will create some new files.
    *

      Make sure the universe section of the Ubuntu repositories is enabled (See the AddingRepositoriesHowto), and then run:

sudo aptitude install module-assistant build-essential debhelper debconf dh-make fakeroot libstdc++5 linux-headers-$(uname -r) 

    *

      Disable Composite Extension:

In Ubuntu Edgy the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. To disable Composite you must edit the /etc/X11/xorg.conf file, so add these lines at the end of xorg.conf:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

    *

      Blacklist old fglrx module from linux-restricted-modules

As ubuntu's linux-restricted-modules package includes the fglrx module from an old driver version (8.28.8), we have to blacklist this module to make sure the new kernel module which is needed by the new driver will be used instead.

sudo gedit /etc/default/linux-restricted-modules-common

We need to add fglrx (only! don't remove anything!) to this:
DISABLED_MODULES="somemodule2 fglrx"

Next,

    *

      Perform the following commands (where <version> is the version number of the installer):

sudo ln -sf bash /bin/sh
bash ./ati-driver-installer-<version>.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh
You may need to wait a few mintues for this to complete.

This will create a number of .deb files in the current directory.

    *

      next,

sudo dpkg -i *.deb

next you build the kernel module - (also note, this has to be done every time you upgrade the kernel)

sudo module-assistant prepare,update
sudo module-assistant build,install fglrx-kernel (or module-assistant -f to force a rebuild if needed)
sudo depmod
sudo rm -f /usr/src/fglrx-kernel*.deb

now see Modifying xorg.conf. Skip the "lrm-manager" and "depmod" commands.

After a reboot, confirm that it worked, by issuing the "fglrxinfo" command, as mentioned elsewhere on this page. Look at the troubleshooting sections to confirm if the output of the command is correct.

---

### Post by koztaz on 2007-03-15
now see Modifying xorg.conf. Skip the "lrm-manager" and "depmod" commands.

Sorry for the lame question but... How can I do that?

---

