---
title: "[SOLVED] Bamboo Fun and Gutsy Gibbon"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by narehart on 2007-11-29
[B]This has been SOLVED and I've posted a HOW TO for the Bamboo tablets under Gutsy Gibbon [here.]("http://ubuntuforums.org/showthread.php?t=631881&highlight=bamboo+fun")
[/B]
Hi there everybody.  I recently bought a Wacom Bamboo Fun tablet.  It comes with a stylus and a mouse.  Unfortunately, I can not get either one of these working under Gutsy Gibbon.

I tried following this guide [here]("http://ubuntuforums.org/showthread.php?t=601143&highlight=bamboo+fun") but it contains too much missing information for me to piece together as well as dead links.

There is also a [HOW TO]("http://linuxwacom.sourceforge.net/index.php/howto/main") on the Linux Wacom website but the directions are so technical as to be beyond me.

So, I posted this in hopes that someone who has implemented this and gotten their Bamboo to work under Gutsy or someone who could make sense of these instructions could post a easy to follow step by step guide

I would be so grateful and I'm sure many other people would be.

---

### Post by narehart on 2007-11-29
bump

---

### Post by narehart on 2007-11-30
bump again!

---

### Post by arelis on 2007-12-01
I fully agree, i've tried getting it to work too. I've followed all those guides, and with that got to a point where my tablet would function as a touch pad (you touch the thing, move the pen, and the mouse moves..), but not as a tablet. Looking further into it i saw that the latest kernel in Gutsy doesn't support the Bamboo Fun yet... but the next one will, which is in the next release, Hardy. It's possible to patch the kernel that's active now and that's what i did but like i said, it functioned like a touch pad. (by the way, if you search this forum for 'bamboo fun' you can see other people having that same problem too)

So if anyone could please clarify this matter and write a couple of guides or tell us how to get the newest kernel, i think that indeed many people would be grateful.

---

### Post by narehart on 2007-12-02
somebody?

---

### Post by narehart on 2007-12-03
i haven't tested this yet but i just got an email from the linuxwacom mailing list.  Basically, it's a short how to on setting up the Bamboo Fun in Gutsy.  I won't get to try it out for a few more hours because i'm at school but if one of you guys want to give it a shot please post back about how it went and any refinements that might need to be made. EDIT: I updated this to make it a little easier to follow.  I still haven't got to try it though.

Credit goes to Philippe

> hi,

here is what I did to install the pilots for the bamboo fun on a brandnew ubuntu 7.10 fully updated as of 3/12/2007

hope this help

Philippe



Get the latest linuxwacom driver on /[http://linuxwacom.sourceforge.net/]("http://linuxwacom.sourceforge.net/") and save it to your desktop.

Get last udev file for wacom on [http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob_plain;f=debian/xserver-xorg-input-wacom.udev;hb=master]("http://git.debian.org/?p=users/ron/wacom-tools.git;a=blob_plain;f=debian/xserver-xorg-input-wacom.udev;hb=master")

Copy and paste that code into a new text file and name it **xserver-xorg-input-wacom.udev**.  Save it onto your desktop.

Get the necessary dependencies:  

```
sudo apt-get install build-essential x11proto-core-dev libxau-dev libxdmcp-dev x11proto-input-dev x11proto-kb-dev xtrans-dev libx11-dev x11proto-xext-dev libxext-dev libxi-dev linux-libc-dev libc6-dev libncurses5-dev xserver-xorg-dev
```

Create a folder, like **home/administrator**, to hold backup files in case you have any problems. Then backup the old rules:

```
cp /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules /home/administrator/50-xserver-xorg-input-wacom.rules_orig
```

Navigate to your desktop and replace the old udev with the one you made:

```
cd /home/**yourname**/Desktop
cp xserver-xorg-input-wacom.udev /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules libice-dev libsm-dev libxt-dev tcl8.4-dev tk8.4-dev
```

Then extract the wacom driver:

```
bunzip2 linuxwacom-0.7.9-3.tar.bz2
```

```
tar xvf linuxwacom-0.7.9-3.tar
```

Then go into the newly created folder and configure:

```
cd linuxwacom-0.7.9-3
```

```
./configure --enable-wacom
```

If everything went well, you should see something like this:

```
----------------------------------------
 BUILD ENVIRONMENT:
      architecture - i486-linux-gnu
      linux kernel - yes 2.6.22
 module versioning - yes -DCONFIG_MODVERSIONS -DMODVERSIONS -include
/lib/modules/2.6.22-14-generic/build/include/linux/modversions.h
     kernel source - yes /lib/modules/2.6.22-14-generic/build
          Xorg SDK - yes /usr/include/xorg
         XSERVER64 - no
          dlloader - yes
              XLib - yes /usr/lib
               TCL - yes /usr/include/tcl8.4/
                TK - yes /usr/include/tcl8.4/
           ncurses - yes

 BUILD OPTIONS:
           wacom.o - yes
           wacdump - yes
            xidump - yes
       libwacomcfg - yes
        libwacomxi - yes
         xsetwacom - yes
             hid.o - no
        usbmouse.o - no
           evdev.o - no
        mousedev.o - no
           input.o - no
       tabletdev.o - no
      wacom_drv.so - yes /usr/lib/xorg/modules/input
       wacom_drv.o - no
----------------------------------------

```

Then make and install:

```
make
sudo make install
```

Next, you have to edit your xorg file so that it will detect the Bamboo.  **Before you do any altering to your xorg.conf file, first make a backup!**

```
 cp /etc/X11/xorg.conf /home/administrator/xorg.conf_old
```

```
sudo gedit /etc/X11/xorg.conf
```

```
Section "InputDevice"
       Driver          "wacom"
       Identifier      "stylus"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "stylus"
       #Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
   Option "USB" "on"
EndSection

Section "InputDevice"
       Driver          "wacom"
       Identifier      "eraser"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "eraser"
       #Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
   Option "USB" "on"
EndSection

Section "InputDevice"
       Driver          "wacom"
       Identifier      "cursor"
       Option          "Device"        "/dev/input/wacom"
       Option          "Type"  "cursor"
       #Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
   Option "USB" "on"
EndSection

...
       # Uncomment if you have a wacom tablet
              InputDevice     "stylus"        "SendCoreEvents"
              InputDevice     "cursor"        "SendCoreEvents"
              InputDevice     "eraser"        "SendCoreEvents"

```

```
Section "InputDevice"
Driver "wacom"
Identifier "pad"
Option "Device" "/dev/input/wacom"
Option "Type" "pad"
Option "USB" "on"
EndSection
```

Add this to the lower section:

```
InputDevice "pad" "SendCoreEvents"
```

Now, back up the old driver:

```
cp /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/wacom.ko /home/administrateur/wacom.ko_old
```

Then, replace it with the new one:

```
sudo cp /home/**yourname**/Desktop/linuxwacom-0.7.9-3/src/2.6.22/wacom.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/tablet/
```

Next, test the module to see if there is anything unresolved. If you get nothing back, your golden!

```
sudo depmod -e
```

Save any important data, reboot the system and see if it works:

```
sudo reboot
```

**What did not work for me is the following:**

If it worked you can set the actions for the buttons with instructions like these:

```
xsetwacom set pad AbsWUp 4 #scroll up
xsetwacom set pad AbsWDn 5 #scroll down
xsetwacom set pad button3 4 #< key: scroll up
xsetwacom set pad button1 5 #> key: scroll dn
xsetwacom set pad button2 1 #FN1 key: left mouse button
xsetwacom set pad button4 3 #FN2 key: right mouse button

```

---

### Post by Dan_Dranath999 on 2007-12-04
I'll try that today !

---

### Post by Radioactiveroach on 2007-12-04
Refering to the following section
```

Section "InputDevice"
Driver "wacom"
Identifier "cursor"
Option "Device" "/dev/input/wacom"
Option "Type" "pad"
Option "USB" "on"
EndSection

```

for the line that says 
```

Identifier "cursor"

```
write 
```

Identifier "pad"  

```
instead.
I got the device working properly however if I unplug it and plug it back in it will not load.
I am trying to get the driver to load when the device is plugged in. That way  I won't have to press ctrl+alt+backspace every time I plug it in any suggestions?

---

### Post by dm1024 on 2007-12-11
How to autoload wacom driver in Xorg? When I'm plugging bamboo after X started it acts as touchpad. So i should restart X every time before use bamboo. How to avoid it?

And the second - how to apply "xsetwacom set pad ..." automaticaly at startup?

---

### Post by dz61 on 2007-12-12
It seems there is a syntax error in a line of code you give:

```
cp xserver-xorg-input-wacom.udev /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules libice-dev libsm-dev libxt-dev tcl8.4-dev tk8.4-dev
```

Could you please explain me what should I copy where? 

---Thanks.

---

### Post by dm1024 on 2007-12-12
it should be
```
cp xserver-xorg-input-wacom.udev /etc/udev/rules.d/50-xserver-xorg-input-wacom.rules
```

---

