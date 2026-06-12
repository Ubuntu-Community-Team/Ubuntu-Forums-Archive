---
title: "Video Resolution Problem"
date: 2014-09-05
forum: Hardware
---

### Post by mark_shore on 2014-09-05
Hi just installed Ubuntu Server on a HP Proliant micro server but cannot set the resolution only one is available (supported) when using either terminal or the gui. I have installed xfce4 as the gui, I peviously had Linux Mint 17 and could set to 1920x1200 60 hz.
How can i activate the extra settings as it will only set to one at present.
Thanks

---

### Post by papibe on 2014-09-05
Hi mark_shore. Welcome to the forum ):P

Could you open a terminal, run these commands and post back the results (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga

ls /etc/X11/xorg.conf

xrandr -q

xrandr -q --q1
```
Regards.

---

### Post by mark_shore on 2014-09-05
Thanks this what I got back.

$ lspci -nnk | grep -iA2 vga

ls /etc/X11/xorg.conf

xrandr -q

xrandr -q --q101:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] [1002:9712]
    Subsystem: Hewlett-Packard Company Device [103c:1609]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe [14e4:165b] (rev 10)
$ $ ls: cannot access /etc/X11/xorg.conf: No such file or directory
$ $  SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 325mm x 260mm )  *60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
$ $

---

### Post by papibe on 2014-09-05
Thanks.

Could you please execute one command (one line) at a time, so that we can see the results properly? 

At this moment with partial information, my guess right now is that is video driver problem.

ATI/AMD cards from prior to the 5000 series are no longer supported by the proprietary AMD driver. Did you install it? If so, I would recommend going back to the open source driver (radeon). There are ppa's for legacy proprietary drivers, but they have some issues.

Looking forward from hearing from you.
Regards.

---

### Post by mark_shore on 2014-09-05
Hi try these.
xrandr: unrecognized option '--q1lspci'
Try 'xrandr --help' for more information.

ls: cannot access /etc/X11/xorg.conf: No such file or directory


 SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 325mm x 260mm )  *60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none

$ xrandr -q --q1
 SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 325mm x 260mm )  *60  
Current rotation - normal
Current reflection - none
Rotations possible - normal 
Reflections possible - none
$ 

Thanks

---

### Post by papibe on 2014-09-05
Thanks.

There's only 1280x1024 available with the current driver, but still we don't which driver are you using.

Did you install the AMD/ATI proprietary driver?

Could you run this again?
```
lspci -nnk | grep -iA2 vga
```
and, then:
```
lsmod | grep -iE 'radeon|fglrx'
```
Regards.

---

### Post by mark_shore on 2014-09-06
Hi this is what I got
01:05.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RS880M [Mobility Radeon HD 4225/4250] [1002:9712]
    Subsystem: Hewlett-Packard Company Device [103c:1609]
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5723 Gigabit Ethernet PCIe [14e4:165b] (rev 10)
$ 

$ lsmod | grep -iE 'radeon|fglrx'
radeon               1522474  0 
ttm                    85115  1 radeon
drm_kms_helper         53081  1 radeon
drm                   303102  3 ttm,drm_kms_helper,radeon
i2c_algo_bit           13413  1 radeon
$ 
Hi a friend set up the server for me 'Ubuntu Server' not desktop but dont think he installed and video drivers I believe the drivers were found on install.
Thanks

---

### Post by mark_shore on 2014-09-06
Just checked under Synaptics and attached screenshot of the ati/radion packages installed.[ATTACH=CONFIG]256201[/ATTACH]

---

### Post by mark_shore on 2014-09-07
Remove drivers still no different a screenshot attached. Would replacing the shared card with a pci nvidea card cure the issue.
Thanks

[ATTACH=CONFIG]256231[/ATTACH]

---

