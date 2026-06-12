---
title: "Compaq nx6125 - Suspend problem"
date: 2008-07-10
forum: Hardware
---

### Post by MetalH on 2008-07-10
Hi everybody, I've got a problem with my laptop. It is a Compaq nx6125, with Mobile Sempron 3100+, bcm4318 Wi-Fi adapter and a old ATI card, I think Xpress 200M.

I put Ubuntu 8.04 on this PC, and everything works fine. But suspend doesn't work.
When I click on the suspend button in the menu, I get a blank screen with a blinking _ (underscore) in the top left corner.

I tried to follow some tutorials to get suspend working, but I failed. Sometimes I was able to switch to other consoles (tty2, tty3, etc) in the screen I said, but no more, suspend has never worked.

I also tried to put Kubuntu on my laptop, but the result was the same (so I indicated "all variants" in the thread).

It doesn't matter if hibernate doesn't work, my unique goal is to have something like the Window$' standby to use, in order to save power when I leave the laptop on.

Can you help me?

Thanks.

EDIT: if you suggest me to try other distros, don't suggest OpenSUSE (doesn't work on my PC).

---

### Post by MetalH on 2008-07-12
I don't believe that nobody knows a solution.
Please suggest me a way to simulate the Windows' standby, next year I need my laptop even out of home, and, if the power saving doesn't work, I'll have to uninstall Linux :(!

---

### Post by Foster Grant on 2008-07-13
Try this, from [this site](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Suspend.2FHibernation):

In the file /etc/default/acpi-support, make the following changes:

```

SAVE_VBE_STATE=false

POST_VIDEO=false 

ENABLE_LAPTOP_MODE=false

```

Notes:

[list=1]
[*]The last item may already be set to "false," as it was on my Gateway with ATi Radeon Xpress 1100.
[*]If you have a USB keyboard plugged in as a docking-station setup, unplug it before waking up the computer or restart will crash and you'll have to reboot.
[/list]

---

### Post by MetalH on 2008-07-16
Already tried, but nothing.
Now I'm using Mandriva One Spring 2008. I'd prefer Ubuntu, but the suspend still doesn't work.

---

### Post by sateeshpnv on 2008-11-10
I too use hp Compaq nx6125 laptop. It runs Ubuntu 8.10 fairly well.

My suspend to disk started working after I unloaded a few modules during suspend/resume.
/etc/default/acpi-support -- MODULES="ehci_hcd ohci_hcd usbcore fglrx radeonfb". Not sure if the USB drivers were needed to be unloaded.

My suspend to RAM started working after I removed "vga=791" from kernel options.

You may want to look at [http://lxr.linux.no/linux/Documentation/power/basic-pm-debugging.txt](http://lxr.linux.no/linux/Documentation/power/basic-pm-debugging.txt). If you follow those instructions, you should be able to find out the module causing your problem and unload that module.

I have only one issue with nx6125 -- external video output to a projector is not working yet, even after using xrandr and various other solutions. It was working fine on 8.04. Something changed in X in 8.10.

---

### Post by sateeshpnv on 2008-11-10
I too use hp Compaq nx6125 laptop. It runs Ubuntu 8.10 fairly well.

My suspend to disk started working after I unloaded a few modules during suspend/resume.
/etc/default/acpi-support -- MODULES="ehci_hcd ohci_hcd usbcore fglrx radeonfb". Not sure if the USB drivers need to be unloaded.

My suspend to RAM started working after I removed "vga=791" from kernel options.

You may want to look at [http://lxr.linux.no/linux/Documentation/power/basic-pm-debugging.txt](http://lxr.linux.no/linux/Documentation/power/basic-pm-debugging.txt). If you follow those instructions, you should be able to find out the module causing your problem and unload that module.

I have only one issue with nx6125 -- external video output to a projector is not working yet, even after using xrandr and various other solutions. It was working fine on 8.04. Something changed in X in 8.10.

---

