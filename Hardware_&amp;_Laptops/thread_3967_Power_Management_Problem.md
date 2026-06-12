---
title: "Power Management Problem"
date: 2004-11-10
forum: Hardware &amp; Laptops
---

### Post by Eklipz on 2004-11-10
Whenever I close my laptop cover while it is still powered on, it goes to sleep, but then I cannot ever wake it back up.  How might I go about fixing this?

---

### Post by humberto on 2004-11-12
[QUOTE=Eklipz]Whenever I close my laptop cover while it is still powered on, it goes to sleep, but then I cannot ever wake it back up.  How might I go about fixing this?[/QUOTE]

First, go check the laptop support page on the Ubuntu Wiki.

[http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops](http://www.ubuntulinux.org/wiki/HardwareSupportMachinesLaptops)

If you still have problems, you can try to tell us what laptop you have, and how you configured it.

---

### Post by SteveK on 2004-11-16
I'm having the same problem as the original poster [Inspiron 8200 w/ kernel 2.6.8.1-3]  -- to wit, when I close the lid, the screen blanks, but the computer remains on (I have to press fn-8 (crt/lcd) to return to the display ). Also, I can't suspend with fn-1 either. The wiki entry linked to does not mention this issue. . 

I've attached dmesg output taken before (dmesg) and after (dmesg2) an attempt to suspend. Also, [FONT=Lucida Console]echo 3 >/proc/acpi/sleep[/FONT] successfully suspends, but when waking up, the display comes back on but it's just a white screen. ACPI events are generated both by pressing fn-F1 and by closing the lid:

steve@jerico:~ $ acpi_listen
button/sleep SBTN 00000080 00000001
button/sleep SBTN 00000080 00000002

steve@jerico:~ $ acpi_listen
button/lid LID 00000080 00000005
button/lid LID 00000080 00000006

Thanks for any help.

---

### Post by humberto on 2004-11-16
[QUOTE=SteveK]I'm having the same problem as the original poster [Inspiron 8200 w/ kernel 2.6.8.1-3]  -- to wit, when I close the lid, the screen blanks, but the computer remains on (I have to press fn-8 (crt/lcd) to return to the display ). Also, I can't suspend with fn-1 either. The wiki entry linked to does not mention this issue. . 
[/QUOTE]

You'll have to write or modify the scripts and events in /etc/acpi to do something useful with your events.

I started with the scripts in thinkpad-support-x40, and built up usefull ones for my Fujitsu Lifebook P2120.

---

### Post by humberto on 2004-11-16
[QUOTE=humberto]You'll have to write or modify the scripts and events in /etc/acpi to do something useful with your events.[/QUOTE]
To elaborate, the suspend.sh script complained about different things on my laptop, so I modified the list of modules unloaded and loaded by the suspend script untill I got most everything working.

The best way for me to debug the problems were by calling the /etc/acpi/suspend.sh by hand from an X terminal.

There is also a Suspend Howto on the Ubuntu Wiki

[https://www.ubuntulinux.org/wiki/SuspendHowto](https://www.ubuntulinux.org/wiki/SuspendHowto)

---

### Post by SteveK on 2004-12-06
I never completely resolved this issue, but after installing the proprietary NVidia driver and disabling AGP, I managed to get suspend-to-ram working on my Inspiron 8200/GForce 440. If 3d acceleration isn't important, here's a workaround (note: I'm now running kernel 2.6.9-1-686/Hoary, but this should work for Warty & other kernels):

[note: you will have to to edit files as the root user -- open a terminal window (Applications > System Tools > Terminal, and start up a text editor (gedit, in this case) by entering 'sudo gedit *filename*' w/o the 's in the terminal]

[list]
[*]Download NVidia driver
[indent][http://download.nvidia.com/XFree86/Linux-x86/1.0-6629/NVIDIA-Linux-x86-1.0-6629-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/1.0-6629/NVIDIA-Linux-x86-1.0-6629-pkg1.run)[/indent]
[*]edit /etc/X11/xorg.conf or /etc/X11/XFree86.conf
[list=1]
[*]in Section "Modules", remove (or comment out with a #) the lines
[indent]Load "GLcore"
Load "dri"[/indent]
[*]in Section "Device", remove or comment out the line
[indent]Driver "nv"[/indent]
and add the lines
[indent]Driver "nvidia"
Option "NvAGP" "0"[/indent]
[/list]

[*]edit /etc/hotplug/blacklist, adding the following lines:
[indent]intel_agp
agpgart[/indent]

[*]cd to directory where you downloaded the driver to, then install it:
[indent]sudo sh NVIDIA-Linux-x86-1.0-6629-pkg1.run[/indent]
The installation will complain about the rivafb module, but I haven't noticed any problems.

[*]reboot

[*]the nvidia driver didn't want to load properly at startup for some reason, so the X server wouldn't start. I got it to work by adding
[indent]nvidia[/indent] 
to the file /etc/modules
[/list]

---

### Post by cnspy on 2006-01-03
Are you sure it is the video driver problem? I am using the integrated video chip from SIS. I have the same problem.

It can not suspend to ram when I press the Fn+F1. After I close the LID, the screen comes to black but the system does not suspend. 

I can use the commamd:
echo -n mem > /sys/power/state

to suspend my laptop. But It can not be resumed.

---

