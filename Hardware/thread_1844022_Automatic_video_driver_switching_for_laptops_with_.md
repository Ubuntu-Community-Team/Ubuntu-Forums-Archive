---
title: "Automatic video driver switching for laptops with switchable graphics"
date: 2011-09-14
forum: Hardware
---

### Post by gatman3 on 2011-09-14
I developed a method for automatically switching the video driver on my laptop depending on which graphics chip I choose at boot time.  I have mentioned this in other threads and have been asked for help with this on occasion, so I thought I'd just share it in a central place in case it helps other people.  This may be useful for anyone with a high-end laptop with multiple graphics chips (switchable graphics) who runs sometimes in a dock and sometimes out of the dock.

A little background:

Some higher-end laptops have multiple graphics chips.  It seems like this is usually a combination of the integrated video provided by the Intel chipset along with some discrete ATI or NVidia graphics chip.  Lenovo has implemented this on their W-series laptops, but I think that there are other manufacturers as well that do this with higher end products.  On Lenovo laptops they typically have an option in the BIOS config at boot-up for choosing either "Integrated" graphics or "Discrete" graphics, where Integrated=intel and Discrete=ATI or NVidia.  On my Lenovo W500 the discrete chip was an ATI HD3650 and on my newer W520 it is an NVidia Quadro 1000M, and I used this method successfully on both machines.

Note that the "switchable graphics" options such as NVidia's "Optimus" are not helped by this script.  I believe there are efforts to support this for Linux (the "bumblebee" project perhaps?) but this setup is just intended to make it easier to switch between Integrated graphics using the included open-source intel driver and Discrete graphics using the proprietary fglrx or nvidia driver after choosing the graphics chip at boot time.  This is especially useful if you have a multi-monitor setup using a dock so that you can run using the Discrete chip when docked but the Integrated chip when undocked.  Typically the Integrated graphics burns less power, so it's useful when you are running on battery, but it also doesn't typically support DVI outputs and/or multiple external monitors.

So, here is my recipe.  If anyone has a better way to do this, please chime in.  I'm using my newer W520 as an example machine, and this was crafted for Ubuntu 11.04 with the upstart boot scripts.

-----

A couple of things to understand first.  When running the open-source intel graphics driver you do not need an /etc/X11/xorg.conf configuration file as Xorg handles the configuration automatically, but you do need an xorg.conf when you are running the proprietary drivers for ATI (fglrx) or nvidia graphics.  I believe that if you use the open-source ati or nvidia (nouveau) drivers you should not need this method.  This is a matter of personal choice, and many people may be perfectly happy with the open-source drivers and won't need a method like this to switch graphics drivers.  I'm assuming you have already made the choice to use the proprietary driver for your discrete graphics chip and have already enabled and installed the driver properly, as there are plenty of other threads about how to do that (and it's generally trivial in the newer Ubuntu versions).

The first step is to get your nvidia graphics configured the way you want it and then make an xorg.conf file that represents that configuration.  This took some experimentation for me, but wasn't all that difficult.

NVIDIA DUAL MONITOR CONFIGURATION

So to get an xorg.conf that's correct for nvidia, what I did was boot up in Discrete graphics mode (selected in the BIOS config) and then ran the "NVIDIA X Server Settings" application, which for me is in my System menus.  I believe this is the same as the /usr/bin/nvidia-xconfig program, and you may need to be root to run it.  For dual monitors I believe you will want to use the "TwinView" setting, and then arrange your screens how you like them in their configuration program.  When you have both monitors turned on and configured the way you want them, you should have the configuration application write out an xorg.conf file.  This didn't work properly for me for some reason in that the application gave an error that it couldn't write directly to /etc/X11 (despite having permissions) so I changed the path and just wrote the xorg.conf file to my home area.

At this point you should test that the configuration is working by rebooting again in nvidia mode with your new xorg.conf file in place at /etc/X11.  If it works the way you want, you're in good shape, otherwise repeat the configuration process until your dual monitors are set up the way you want them.

AUTOMATIC CONFIGURATION SWITCHING BETWEEN INTEL AND NVIDIA

The whole idea here is to add a step to the boot process that either switches in the xorg.conf file (for nvidia) or deletes the xorg.conf file (for intel) before the graphics driver is loaded during boot-up.  This needs to be done fairly early in the boot process.

To do this, you need to (1) place the following script in /etc/init.d, (2) place your newly created xorg.conf file for nvidia mode in /etc/X11 under the different name xorg.conf.nvidia, and (3) add a line in /etc/init/kdm.conf for KDE users or /etc/init/gdm.conf for GNOME users that invokes this script.  Here is an example /etc/init/kdm.conf:

.
.
.
/etc/init.d/xorg-config      # (this is the line you add)
    /etc/init.d/xorg-config
    if [ -n "$UPSTART_EVENTS" ]
    then
.
.
. etc...

Here is the script:

```
#xorg.conf switcher shell script
#
#1. place this script (or a link to this script) in /etc/init.d/
#2. create the xorg.conf.nvidia file in /etc/X11 (copy from a properly
#     configured xorg.conf when the fglrx driver is used)
#3. Add a line in /etc/init/kdm.conf to execute this script as the first step
#     in the script section:
#
# Example /etc/init/kdm.conf:
# .
# .
# .
# script
#     /etc/init.d/xorg-config
#     if [ -n "$UPSTART_EVENTS" ]
#     then
# .
# .
# . etc...

/usr/bin/lspci > /tmp/lspci.txt
VIDEO=`/usr/bin/lspci |grep -i VGA|grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
cp -f /etc/X11/xorg.conf.nvidia /etc/X11/xorg.conf
else
rm -f /etc/X11/xorg.conf
fi

```

Make sure the script has execute privileges (only root is necessary, I think).  If you have a machine with a discrete ATI graphics chip, you would need to change the grep portion of the script to look for the string "ATI" instead of "nVidia", and probably change the xorg.conf.nvidia filename as appropriate.

Now if you reboot undocked with Integrated (intel) graphics selected in the BIOS config, when this script runs at boot time it should automatically delete the /etc/X11/xorg.conf and X should bring up the intel graphics driver properly, and if you reboot docked with your dual monitors and you select Discrete (nvidia) graphics in the BIOS config this script should automatically copy the /etc/X11/xorg.conf.nvidia script into /etc/X11 and your dual monitors should come up properly.

It would be nice if Ubuntu included a more built-in method for doing this (hint to any Ubuntu developers who might read this), as laptops with switchable graphics seem to be gaining in popularity at the high-end.

---

