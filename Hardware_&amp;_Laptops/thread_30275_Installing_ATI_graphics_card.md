---
title: "Installing ATI graphics card"
date: 2005-04-27
forum: Hardware &amp; Laptops
---

### Post by dr43058 on 2005-04-27
logged in under root

issued, sudo apt-get install fglrx-driver

it fails and i get

postdrop:warning:unable to lookup public/pickup:no such file or directory

reading package lists...done

building dependency tree...done

e: couldn't find package fglxr-driver

---

### Post by codejunkie on 2005-04-28
open up synaptic hit search use option Description and Name type fglrx that should list what you need, for hoary it's not fglrx-driver it's xorg-driver-fglrx or xfree86-driver-fglrx depending on whether your using hoary or wartey, hoary uses xorg, wartey uses xfree86. that is if you can log into x and open synaptic, if not type sudo apt-get update, sudo apt-get install xorg-driver-fglrx also install the linux-restricted-modules for your kernel type uname -a it should say for example Linux ubuntu 2.6.10-5-[COLOR=Red]686[/COLOR] if it says this you would use sudo apt-get install linux-restricted-modules-2.6.10-5-[COLOR=Red]686[/COLOR] replace the [COLOR=Red]-686[/COLOR] with whatever kernel version you have, after you install these, echo fglrx | sudo tee -a /etc/modules, sudo sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf, restart and that should do it. after you have x up and running you may also want to open synaptic and install some other things like fglrx-control hope this helps.

---

### Post by dr43058 on 2005-04-28
It won't start X server. I tried the commands you gave me and they didn't work. 

My kernel is 2.6.8.1-3-386

I am a programmer so I can handle the syntax, I am just new to Unix/Linux conventions and they take a little time to assimilate them.

---

### Post by codejunkie on 2005-04-29
[http://ubuntulinux.org/wiki/BinaryDriverHowto](http://ubuntulinux.org/wiki/BinaryDriverHowto) this may help a little more than i have, it goes into great detal on installing binary drivers in ubuntu i'm sorry the directions i gave didn't work i hope this helps if this does'nt work please post in detal the exact errors you are having, what version of ubuntu you are installing, the model number of your ati card, your computer model number or specifications, and your /etc/X11/xorg.conf file.

---

### Post by dr43058 on 2005-05-04
Warty 4.10 
Linux kernel 2.6.8.1-3-386
ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

---

### Post by Tsjoklat on 2005-05-05
[QUOTE=dr43058]Warty 4.10 
Linux kernel 2.6.8.1-3-386
ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE][/QUOTE]

Make sure your reps say: main restricted universe multiverse > sudo apt-get update

My setup:

Kernel 2.6.10-k7 version
Restricted Modules 2.6.10-k7 version 
xorg-driver-fglrx

In my xorg.conf:

        Driver          "fglrx"
# If X refuses to use the screen resolution asked for,
# uncomment this; see "Bugs and Workarounds" for details.
  #Option "NoDDC"

# === Video Overlay for the Xv extension ===
        Option          "VideoOverlay"          "on"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
        Option          "OpenGLOverlay"         "off"

# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.
        Option          "UseInternalAGPGART"    "no"

# You don't actually need this next BusID bit - unless maybe you have dual monit ors?
# I've removed it from mine (single monitor only) and all is well.
# I think it's a leftover from fxglrconfig - doh!
#       BusID           "PCI:1:0:0"
        BusID           "PCI:2:0:0"
EndSection

Some cards want BusID 1, others want 2. It is a matter of trail and error I think. Hope this will help you out,

D

---

### Post by dr43058 on 2005-05-05
Do you know why I don't have an xorg.conf file in my* /etc/X11 * directory?

---

