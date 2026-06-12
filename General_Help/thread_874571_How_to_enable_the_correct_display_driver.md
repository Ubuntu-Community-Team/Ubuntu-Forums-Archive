---
title: "How to enable the correct display driver?"
date: 2008-07-30
forum: General Help
---

### Post by Avinash.Rao on 2008-07-30
Hi Guys,

Below is the output of lspci on my ubuntu studio 8.04 on a Intel Machine.

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

my /etc/X11/xorg.conf looks something like this.. 

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Is it using the SIS Display driver or just the standard vga driver? How will i know what display driver my system is using? 

Also, i installed "xserver-xorg-video-sis" and "displayconfig-gtk", but i don't see the System->Administration->Screens and Graphics menu at all.

Kindly help
Avinash

---

### Post by Nepherte on 2008-07-30
Just enter this in a terminal:
```
displayconfig-gtk
```
and pick the tab 'graphic card'. There you can see what driver is in use.

---

### Post by prshah on 2008-07-30
> **Avinash.Rao said:**
> 

Is it using the SIS Display driver or just the standard vga driver? How will i know what display driver my system is using? 


> **Nepherte said:**
> 
```
displayconfig-gtk
```
and pick the tab 'graphic card'. There you can see what driver is in use.

And if you want to change it:

1) Press Alt+F2
2) ```
gksudo displayconfig-gtk
```
3) Choose "Graphics Card" tab
4) Change to a suitable driver.

If you still can't get it to work properly, post your /var/log/Xorg.0.log" file; you may need to (b/g)zip it up first.

---

### Post by Avinash.Rao on 2008-07-30
Thanks for the information, i executed displayconfig-gtk on the terminal and could see the adapter information and it says "Graphics Card (SIS REAL256, but i doubt this the correct driver, i guess its taken the driver closest to [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter.

---

