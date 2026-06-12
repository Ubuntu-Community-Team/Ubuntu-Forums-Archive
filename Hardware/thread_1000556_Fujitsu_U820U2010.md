---
title: "Fujitsu U820/U2010"
date: 2008-12-03
forum: Hardware
---

### Post by sadata on 2008-12-03
I just picked up a Fujitsu U820 UMPC and installed Intrepid on it. Everything generally works out of the box (although I have not yet tested the CF and SD slots or the integrated GPS). Video (based on Intel's new GMA 500 controller) works with the vesa driver but doesn't go above 1024x600 (the LCD's native resolution is 1280x800) and there's no 2D/3D acceleration. Does anyone know where I can get an accelerated display driver for Linux for the GMA500?

---

### Post by sadata on 2008-12-03
I've checked with Tungsten Graphics (who evidently wrote the Windows drivers for Intel) and they are a dead-end.

It looks like it's supposed to be supported by Ubuntu according to this page on the Intel site:

[URL="http://www.intel.com/support/notebook/mid/atom/sb/CS-029326.htm"]http://www.intel.com/support/notebook/mid/atom/sb/CS-029326.htm
[/URL]

In case the page changes, this is what it currently says:

Intel® Atom™ Processor Technology
Which operating systems are supported?

The Intel® Graphics Media Accelerator 500 driver for Intel® Atom™ processor technology supports the following operating systems:

Windows*:

    * Windows Vista* (32-bit versions)

Linux*:

    * Canonical* Ubuntu*
    * Asianux* (Consortium consisting of Red Flag*, Haansoft*, and Miracle*)
    * Moblin*

Operating System:
Windows Vista*, Linux*

This applies to:
Intel® Atom™ Processor Technology

---

### Post by wwwpanda on 2008-12-05
Same experience as you with my U2010. The major problem with 8.10 in U2010 is the missing 3D (2D acceleration is slow too), and no way to wake up from suspend. 

BTW, I have also replaced the HD with a fast sandisk CF 16Gb. Booting from start into Gnome takes about 50 secs. But I really hope it can wake up from suspend.

---

### Post by vvhh2002 on 2009-02-03
same as my u2010, no wifi,no 3d,no suspend,no web cam

---

### Post by Anfanglir on 2009-05-14
Got my Fujitsu u820 today and have installed jaunty (I dual boot Vista). To get 2D graphics working properly i added these repos:

deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main

and added ppa key as described in link from this page:
[https://launchpad.net/~ubuntu-mobile/+archive/ppa?field.series_filter=jaunty](https://launchpad.net/~ubuntu-mobile/+archive/ppa?field.series_filter=jaunty)

I then installed libdrm-poulsbo1 and xserver-xorg-video-psb through synaptic. Then reboot and now 2D works fine and with the correct resolution.

/ Anfanglir

EDIT: for installing Poulsbo-graphics (GMA500) drivers in Karmic Koala see this page:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo")
END EDIT

---

### Post by Anfanglir on 2009-05-19
Got touchscreen and rotate working by following the steps described at this page:
[http://spareinfo.blogspot.com/2009/05/linux-on-u810-p1620-touchscreen-iv.html#comment-form](http://spareinfo.blogspot.com/2009/05/linux-on-u810-p1620-touchscreen-iv.html#comment-form)

The fjbtndrv driver package mentioned on that site are located at:
[https://launchpad.net/~khnz/+archive/ppa?field.name_filter=fjbtndrv&field.status_filter=published&field.series_filter=any](https://launchpad.net/~khnz/+archive/ppa?field.name_filter=fjbtndrv&field.status_filter=published&field.series_filter=any)

/ Anfanglir

---

### Post by demonfuzz on 2009-07-18
Hoping someone can help me out here, I just got a new U820.
Installed 8.10/interepid.
I am trying to install the suggested drivers but keep running into all kinds of issues.

1st, with the fujitsu_usb_touchscreen driver.

I type "make" & it fires off this warning:

fujitsu-usb-touchscreen-0.3.5# make

make -C /lib/modules/2.6.29.4/build M=/root/fujitsu-usb-touchscreen-0.3.5 modules
make[1]: Entering directory `/usr/src/linux-source-2.6.29.4'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.29.4/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /root/fujitsu-usb-touchscreen-0.3.5/fujitsu_usb_touchscreen.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /root/fujitsu-usb-touchscreen-0.3.5/fujitsu_usb_touchscreen.mod.o
  LD [M]  /root/fujitsu-usb-touchscreen-0.3.5/fujitsu_usb_touchscreen.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.29.4'
gcc -o fujitsu_touchscreen_helper fujitsu_touchscreen_helper.c


And at boot time I get errors that say:

ERROR: Module fujitsu_usb_touchscreen does not exist in /proc/modules
ERROR: Module usbhid does not exist in /proc/modules
FATAL: Module fujitsu_usb_touchscreen not found.
FATAL: Module usbhid not found.

I take it that is due to the problems from compiling the touchscreen drivers?

How do I fix the usbhid not found issue?

I also could not install the fjbtndrv driver.
I added the repo, then did:
apt-get install fjbtndrv

It tries to install the "fsc-btns-kernel-source" .
This fails too, here is the output:


Setting up fsc-btns-kernel-source (2.0-4~intrepid1) ...

Creating symlink /var/lib/dkms/fsc_btns/2.0/source ->
                 /usr/src/fsc_btns-2.0

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.29.4.....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.29.4 (i686)
Consult the make.log in the build directory
/var/lib/dkms/fsc_btns/2.0/build/ for more information.
0
0
dpkg: error processing fsc-btns-kernel-source (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 fsc-btns-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas?
I'm dying to get this little PC working!

---

### Post by Anfanglir on 2009-07-25
could it be because you're using 8.10 instead of 9.04? I get none of those errors on my u820 with Ubuntu Jaunty 9.04, and I have repeated the install process several times trying to get the GPS to function (GPS works now btw).

/ Anfanglir

---

### Post by andres,moya on 2009-11-30
I am on 9.10. Webcam works, wifi works, but suspend or hybernate just halt a system peacefully. Someone said that screen brightness control works, but not in my case. 
 
Basically without hibernate or at least suspend system is a bit useless. Does anyone have a solution for it?
 
Now strange. Hotkeys for volume keys works. What driver responsible for it? It should work for brightness then.
There is fujitsu_laptop module loaded... it have a tree in /sys/devices/platform/fujitsu-laptop/ tried to change vaues for brightness nothing change :(

---

### Post by andres,moya on 2009-11-30
> **Anfanglir said:**
> Got my Fujitsu u820 today and have installed jaunty (I dual boot Vista). To get 2D graphics working properly i added these repos:
 
deb [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mobile/ppa/ubuntu) jaunty main
 
and added ppa key as described in link from this page:
[https://launchpad.net/~ubuntu-mobile/+archive/ppa?field.series_filter=jaunty](https://launchpad.net/~ubuntu-mobile/+archive/ppa?field.series_filter=jaunty)
 
I then installed libdrm-poulsbo1 and xserver-xorg-video-psb through synaptic. Then reboot and now 2D works fine and with the correct resolution.
 
/ Anfanglir
Tried to gi this way, but my packaging program said that going to install 3 packages and remove about 70. Including all other X servers and xorg package it self. I don't think it could help ;)
 
A ok. Now i see karmic == 9.10, right? There is no such packages for karmic, bad karma... :)

---

### Post by Anfanglir on 2009-11-30
For updated instructions on installing poulsbo drivers in Karmic see this page:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo")

The script mentioned there didnt work on my machine (in fact it crashed gnome) but the "Old method" worked fine. There is a catch since installing poulsbo-drivers borks sleep/hibernation.

A similar bug also appears on Aspire One and on this page  
[https://help.ubuntu.com/community/AspireOne/AO751h]("https://help.ubuntu.com/community/AspireOne/AO751h") 
its described how to fix it, I havent tried to apply this fix on my u820 yet.

---

### Post by andres,moya on 2009-11-30
did old method, scared to add old repositories.... what if it will start delete packages again. now i am going to reboot... scared...
 
rebooted... magic! works. now hibernate...
 
Hibernate and suspend are still crashing, but now computer doing something after screen black out. 
 
Now studying your next link.

---

### Post by andres,moya on 2009-11-30
> **Anfanglir said:**
> 


A similar bug also appears on Aspire One and on this page  
[https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h) 
its described how to fix it, I havent tried to apply this fix on my u820 yet.

That link recommend to edit this section:
/usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-acer.fdi
```

      <match key="system.hardware.product" prefix="AcerPower">
        <match key="system.hardware.product" contains="2000">
          <merge key="power_management.quirk.none" type="bool">true</merge>
        </match>
      </match>

      <!-- Aspire One 110 -->
      <match key="system.hardware.product" prefix_outof="AOA110;AOA150">
        <merge key="power_management.quirk.none" type="bool">true</merge>
      </match>


```Question is what is our Prefix and then product key to match?
how can i see it?

got something running hal-device
```

  system.firmware.vendor = 'FUJITSU // Phoenix Technologies Ltd.'  (string)
  system.firmware.version = 'Version 1.17'  (string)
  system.firmware.release_date = '12/16/2008'  (string)
  system.hardware.vendor = 'FUJITSU'  (string)
  system.hardware.product = 'FMVLUB50'  (string)
  system.hardware.version = ''  (string)
  system.chassis.manufacturer = 'FUJITSU'  (string)
  system.board.product = 'FJNB1EE'  (string)


```

i made this section:
```

      <match key="system.hardware.product" string="FMVLUB50">
        <merge key="power_management.quirk.dpms_on" type="bool">true</merge>
        <merge key="power_management.quirk.vbemode_restore" type="bool">true</merge>
        <merge key="power_management.quirk.vbestate_restore" type="bool">true</merge>
      </match>

```

---

### Post by andres,moya on 2009-11-30
Of course we need to enter that section into /usr/share/hal/fdi/information/10freedesktop/20-video-quirk-pm-fujitsu.fdi
 
Hm... this files. i guess i need to add one more for proper following updates. not edit existing one. question is numbers that meand priorieties. ... which file name to use in this case...
 
Same described here [http://planet.lugmen.org.ar/](http://planet.lugmen.org.ar/) ... still no luck. Suspend or Hybernate is the same as halt command.
 
Anyone who managed to get it work let me know ...

---

### Post by andres,moya on 2009-12-01
Solution with suspension solved. it was SD card mounted.

```

#!/bin/sh
# Drop to: /etc/pm/sleep.d
# Use this script to prevent problems with SD cards during  
# suspend. It syncs data and umounts all mmcblk devices prior to
# suspend, and cancels suspend if umounting was not posssible
# (i.e: something locks a file)
case "$1" in
    hibernate|suspend)
        sync
        for drive in $( mount | grep "^/dev/mmcblk" | sed 's/^\(\S\+\).*/\1/'  ); do
#       for drive in $( mount | grep "^/dev/mmcblk" | awk '{print $1}' ); do
            umount -f ${drive} # > /dev/null
            # If umount failed: abort suspend
            if [ $? -gt 0 ]; then
            # Test if device keeps mounted. Previous command could fail
            # (i.e device was not mounted) with a non-stopper
            # problem for the suspend precess
            mount | grep ${drive}
            if [ $? -eq 0 ]; then
                exit 1
            fi
            fi
        done
        ;;
esac


```


now i am going to figure out buttons for brightness... etc.

---

### Post by Anfanglir on 2009-12-01
cool ;)

I'm a newbie and not familiar with creating and running scripts, need to read up on that before I try it

/ Anfanglir

---

### Post by MrWorf on 2009-12-04
I got suspend to work once I disabled DRI (ie, 3D support) and that actually saves some extra power, which is nice (idle at around 4.0-4.4W now according to powertop compared to 4.4-4.8W before).

However, if I suspend and resume, any video playback will insta-crash my system. The screen just goes blank and I can't resurrect it.

Any clues?

My xorg.conf looks like the one described at [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo) with the exception of having DRI turned off.

I'm running UNR 9.10.

**EDIT**
Turning of 3D also seems to stop the network connectivity from stuttering :)

---

### Post by nfix on 2010-02-07
for me fjbtndrv does not fully work ~ key mapping is wrong, some keys like fn and left-down arrow do not work at all and they even show no event. does anybody know how to fix missing keys? the only correctly working button i have is rotation.

---

### Post by Anfanglir on 2010-03-09
finally a workaround for the problem with poulsbo and hibernation, it involves editing grub:

sudo gedit /etc/default/grub
change:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_skip_timer_override"
Save and close gedit, then update grub:
sudo update-grub
Reboot.

(Suspend is still buggy though).

BTW, there is a neat script that download, install and configure graphics drivers for the u820 on this page:
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)


/ Anfanglir

---

