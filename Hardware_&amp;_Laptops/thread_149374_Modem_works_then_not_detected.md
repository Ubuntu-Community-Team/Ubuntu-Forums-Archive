---
title: "Modem works then not detected"
date: 2006-03-23
forum: Hardware &amp; Laptops
---

### Post by raindog on 2006-03-23
I have a Ubuntu/win2kpro dual-boot setup. - Installed a Lucent winmodem the other day on Ubuntu and it worked great. Today I turned the machine on and Ubuntu says that it can't detect the modem. However, win2kpro finds it perfectly. Can someone help me figure out what's going wrong?

I have piled thru the wiki and so far I can't figure out what's causing this strange behavior.

---

### Post by John.Michael.Kane on 2006-03-23
[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems)
[http://linmodems.org/](http://linmodems.org/)
[http://www.tldp.org/HOWTO/Linmodem-HOWTO-2.html](http://www.tldp.org/HOWTO/Linmodem-HOWTO-2.html)
[http://iphitus.loudas.com/linmodems.php](http://iphitus.loudas.com/linmodems.php)

---

### Post by raindog on 2006-03-23
I'm attempting to do the following to get it working:
-----------------------------------------------------

Setup steps:

    *

      In a terminal type

        $ sudo sh -c "echo lt_serial >> /etc/modules"
        $ sudo sh -c "echo lt_modem >> /etc/modules"

      to add them to the module autoloading list.
    *

      Since udev rewrites /dev on each boot, and some dialup programs rely on the existence of /dev/modem, you need to have a symlink created on boot (from /dev/ttyLTM0 to /dev/modem). To do this, create the file /etc/udev/rules.d/10-local.rules, and put these lines in it:

        #ltmodem 
        KERNEL="ttyLTM0", SYMLINK="modem"

    *

      Now load the drivers for the first time:

        $ sudo modprobe lt_serial
        $ sudo modprobe lt_modem

      This should have created the device /dev/modem and you can now go on to configure your dialup connection.
    *

      No, I get an error about "FATAL: module not found" for this step :(

      Note for "5.04 Hoary" users: Ubuntu 5.04 Hoary was shipped with kernel 2.6.10, which has some problems with these modules. To fix, change the grub boot commands /boot/grub/menu.lst as follows (pci=routeirq is new):

        ## ## Start Default Options ##
        ## default kernel options
        ## default kernel options for automagic boot options
        ## If you want special options for specifiv kernels use kopt_x_y_z
        ## where x.y.z is kernel version. Minor versions can be omitted.
        ## e.g. kopt=root=/dev/hda1 ro
        # kopt=root=/dev/hda1 ro pci=routeirq

      Do not forget to update grub: $ sudo update-grub
----------------------------------------------------------
Unfortunately I get the "FATAL: module not found" error.
Now when I try to edit /boot/grub/menu.1st it won't let me.  I've tried sudo-s then gedit /boot/grub/menu.1st but it is a blank file and I know it is not blank.  

I certainly hope that this works as it took me three days to get my winmodem working and now to have to spend 4 hours more on it is really grating on my nerves.  However, I do appreciate all the help and patience.  Now if I could just figure out the correct commands to get this edit done and test it.  If this doesn't do it I am lost.

Thanks though.

---

### Post by raindog on 2006-03-24
bump

I'm really in need of some help trying to finish this up.  Anyone out there?

---

### Post by raindog on 2006-03-24
I have followed all the instructions from [here]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems#head-cc17ea0ff3df391406e74527f1aed569be04709f")
 and I still have no luck with the modem.  When I first installed the correct modem driver it worked fine for one day.  When I started up the next day the modem was unnresponsive.  What the heck is going on?  I figure I've spent 20 hours on this in the last 8 days.  That much time to setup a modem is crazy.  I don't know what else to do.

damn frustrated,
raindog

---

### Post by caseyaberhart on 2006-09-05
> **raindog said:**
> I have followed all the instructions from [here]("https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems#head-cc17ea0ff3df391406e74527f1aed569be04709f")
and I still have no luck with the modem. When I first installed the correct modem driver it worked fine for one day. When I started up the next day the modem was unnresponsive. What the heck is going on? I figure I've spent 20 hours on this in the last 8 days. That much time to setup a modem is crazy. I don't know what else to do.
 
damn frustrated,
raindog
 
same problem here... u ever fix it?

---

