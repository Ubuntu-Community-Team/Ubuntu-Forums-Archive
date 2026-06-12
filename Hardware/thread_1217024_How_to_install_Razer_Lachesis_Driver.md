---
title: "How to install Razer Lachesis Driver?"
date: 2009-07-19
forum: Hardware
---

### Post by cb2410 on 2009-07-19
Hello , 

How to install Razer Lachesis Driver?

I tried using Wine but this didnt make the job.  

Thx

---

### Post by JoshLukas on 2009-07-19
There is no way installing razer lachesis tools to programe your own mouse config on linux. However the mouse is working out of the box with debian squeeze. Can confirm this, because my grandpa uses a razer lachesis on his notebook.

---

### Post by rich-brun on 2009-11-28
I know it's been a while since your posts, but would this be of any use?
[http://sourceforge.net/projects/razertool/](http://sourceforge.net/projects/razertool/)

---

### Post by no0ne on 2009-12-08
Well, actually, you _have_ to configure  most razer mice including lachesis first by the provided (yes I know it sounds ugly) windows drivers for the extra buttons to work. However, since I dislike windows atleast as much as the average Ubuntu user I decided it would be most convenient to run windows just on a virtual machine, since I need it only for hardware compatibility (and just until we someday may have an opensource alternative).

So I ended up having setup [VirtualBox 3 (non-free, from the sun repository)]("http://www.virtualbox.org/wiki/Linux_Downloads"), running a basics only xp sp3 with questadditions and set usb passtrough for the devices in question (razer lachesis, a canon scanner and a wd external hd). (All hardware used supports modern intel virtualization technologies, like [PAE/NX]("http://en.wikipedia.org/wiki/Physical_Address_Extension"), [VT-x]("http://en.wikipedia.org/wiki/VT-x#Intel_Virtualization_Technology_for_x86_.28Intel_VT-x.29") and Nested Paging, but I suppose that's not relevant for the usb passtrough, which is the key to success in this case). A traditional windows intallation would work just as well, but this way I avoided any reboots, and hence think of it as a configuration utility.

Then (in the virtual machine) I downloaded the [latest firmware]("http://www.razersupport.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=184&nav=0,18") for the device, updated, restarted and proceeded to install [the driver]("http://www.razersupport.com/index.php?_m=downloads&_a=viewdownload&downloaditemid=181&nav=0,18"). After another restart I was able to configure the mouse completely and when I shut down the virtual machine also Ubuntu was capable of using the configured buttons. Not only that, it also did follow every bit of configuration made, including macros, binds, functions etc. Also all the previously dead buttons were now happily recorded by the kernel and xev.

So my point being, configure mice with onboard memory first before trying to poll info about the extra buttons on ```
xev
```

Past that point there are plenty of guides out there, [this one]("http://gaarai.com/2009/02/13/navigate-in-ubuntu-nautilus-using-the-mouse/") is the one I used since it's clear, complete and quite recent. Besides transition [from xbindkeys to HAL]("https://wiki.ubuntu.com/X/Config/Input#Input%20Configuration%20with%20HAL") is quite painless. If you want to follow recent developments, you're supposed to use a program called [imwheel]("https://help.ubuntu.com/community/ManyButtonsMouseHowto#Mapping%20More%20Buttons") to configure on a per application basis, but I'd rather stick to X.

The rest of the mouse can be configured with Ubuntu:

```
xset m 0 0
```
disables acceleration, made this a script to run before kde login.
([Source]("http://wiki.archlinux.org/index.php/How_to_set_mouse_acceleration_in_X").)

created /etc/modprobe.d/options and added
```
options usbhid mousepoll=1
```
in order to get the polling rate up to 1000hz.
(Can also be temporarily set with modprobe. [Source]("http://wiki.archlinux.org/index.php/Mouse_Polling_Rate").)

The resolution for the mouse can be set still in /etc/X11/xorg.conf.
Here's my mouse section:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Name" "Razer Lachesis Optical Mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "11"
    Option         "Resolution" "4000"
    Option         "ZAxisMapping" "4 5"
EndSection
```
PS If you happen to try this out with a virtual machine, don't mind the cursor icon... you'll know what I'm talking about ;)
Also, props for [patroclo7]("http://bbs.archlinux.org/profile.php?id=5092") for [clearing the inner workings of xorg and the linux kernel]("http://bbs.archlinux.org/viewtopic.php?pid=529950#p529950") nice and tight on the archlinux forums.

---

### Post by no0ne on 2010-05-08
Hey, just thought an update was due. Bought a Razer Mamba yesterday and just got it tuned to my fancy.

Here's my InputDevice section:
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "Name" "Razer Mamba Optical Mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Buttons" "7"
    Option         "Resolution" "5600"
    Option         "ZAxisMapping" "4 5"
EndSection
```

The rest of the configuration remains the same as with Lachesis, described above.

---

