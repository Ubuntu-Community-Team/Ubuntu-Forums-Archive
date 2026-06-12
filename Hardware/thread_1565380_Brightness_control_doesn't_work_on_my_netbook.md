---
title: "Brightness control doesn't work on my netbook"
date: 2010-08-31
forum: Hardware
---

### Post by lefty81 on 2010-08-31
Hi,
Turkish telecoms company by winning the lottery I'm having a problem on the Vestel brand netbook.
fn + brightness plus / minus when I press the keys, indicator icons on the applet runs but does not fulfill the function. (Brightness does not change)
Enter the following command from the terminal, but when it works:
sudo-s 00:02.1 setpci f4.b = 50

To enter this command every time very tiring. I am looking for a solution in this regard.

Intel Atom N270 processor
945GSE mobile intel express chipset / ICH7-m
77-key keyboard
8.9" SWVGA 1024x600 dpi LCD Display (AUO Brand)

---

### Post by lefty81 on 2010-09-04
unsolved :(

---

### Post by pavolzetor on 2010-09-05
please, post output of ```
lspci
```

---

### Post by lefty81 on 2010-10-27
> **pavolzetor said:**
> please, post output of ```
lspci
```


yusuf@yusuf-netbook:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
yusuf@yusuf-netbook:~$ ^C
yusuf@yusuf-netbook:~$


on ubuntu netbook remix 10.10 :)

---

### Post by pavolzetor on 2010-10-27
please, it is probably ACPI bug, could you report it in launchpad?

and, post here xev and acpi_listen output (you have to press key and if something will be returned, post it)

---

### Post by lefty81 on 2010-10-27
I could not do :( Sorry.
I'm new to Ubuntu.

---

### Post by pavolzetor on 2010-10-27
okey, so

run gnome-terminal

and run command "xev"; press key (hotkey for brightness), it should return some Keycodes
run "sudo acpi_listen"; press key (hotkey for brightness), it should return some events, please, post them here

---

### Post by lefty81 on 2010-10-27
> **pavolzetor said:**
> okey, so

run gnome-terminal

and run command "xev"; press key (hotkey for brightness), it should return some Keycodes


yusuf@yusuf-netbook:~$ xev
Outer window is 0x3c00001, inner window is 0x3c00002

PropertyNotify event, serial 8, synthetic NO, window 0x3c00001,
    atom 0x27 (WM_NAME), time 195384, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x3c00001,
    atom 0x22 (WM_COMMAND), time 195384, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x3c00001,
    atom 0x28 (WM_NORMAL_HINTS), time 195384, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x3c00001,
    parent 0x3c00001, window 0x3c00002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 14, synthetic NO, window 0x3c00001,
    atom 0x11c (WM_PROTOCOLS), time 195384, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x3c00001,
    event 0x3c00001, window 0x3c00002, override NO

ConfigureNotify event, serial 18, synthetic NO, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, (0,0), width 178, height 178,
    border_width 0, above 0x1400062, override NO

PropertyNotify event, serial 18, synthetic NO, window 0x3c00001,
    atom 0x16d (_NET_WM_ALLOWED_ACTIONS), time 195386, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3c00001,
    atom 0x16d (_NET_WM_ALLOWED_ACTIONS), time 195386, state PropertyNewValue

ReparentNotify event, serial 18, synthetic NO, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, parent 0x22005d6,
    (0,0), override NO

PropertyNotify event, serial 18, synthetic NO, window 0x3c00001,
    atom 0x124 (_NET_WM_DESKTOP), time 195469, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3c00001,
    atom 0x124 (_NET_WM_DESKTOP), time 195469, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3c00001,
    atom 0x121 (_NET_FRAME_EXTENTS), time 195470, state PropertyNewValue

ConfigureNotify event, serial 18, synthetic NO, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, (1,29), width 178, height 178,
    border_width 0, above 0x0, override NO

PropertyNotify event, serial 18, synthetic NO, window 0x3c00001,
    atom 0x142 (WM_STATE), time 195470, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3c00001,
    atom 0x12a (_NET_WM_STATE), time 195470, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x3c00001,
    atom 0x18f (XKLAVIER_STATE), time 195475, state PropertyNewValue

MapNotify event, serial 18, synthetic NO, window 0x3c00001,
    event 0x3c00001, window 0x3c00001, override NO

VisibilityNotify event, serial 18, synthetic NO, window 0x3c00001,
    state VisibilityUnobscured

Expose event, serial 18, synthetic NO, window 0x3c00001,
    (0,0), width 178, height 10, count 3

Expose event, serial 18, synthetic NO, window 0x3c00001,
    (0,10), width 10, height 58, count 2

Expose event, serial 18, synthetic NO, window 0x3c00001,
    (68,10), width 110, height 58, count 1

Expose event, serial 18, synthetic NO, window 0x3c00001,
    (0,68), width 178, height 110, count 0

PropertyNotify event, serial 18, synthetic NO, window 0x3c00001,
    atom 0x12a (_NET_WM_STATE), time 195479, state PropertyNewValue

FocusIn event, serial 18, synthetic NO, window 0x3c00001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 18, synthetic NO, window 0x0,
    keys:  4294967235 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 18, synthetic NO, window 0x3c00001,
    atom 0x12a (_NET_WM_STATE), time 195479, state PropertyNewValue

PropertyNotify event, serial 29, synthetic NO, window 0x3c00001,
    atom 0x163 (_NET_WM_ICON_GEOMETRY), time 195558, state PropertyNewValue

FocusOut event, serial 30, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 30, synthetic NO, window 0x3c00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 30, synthetic NO, window 0x3c00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

FocusOut event, serial 30, synthetic NO, window 0x3c00001,
    mode NotifyNormal, detail NotifyNonlinear


> **pavolzetor said:**
> okey, so

run gnome-terminal

run "sudo acpi_listen"; press key (hotkey for brightness), it should return some events, please, post them here

yusuf@yusuf-netbook:~$ sudo acpi_listen
[sudo] password for yusuf: 
video DD02 00000086 00000000       // press when fn + brightness up
video DD02 00000087 00000000      // press when fn + brightness down

---

### Post by pavolzetor on 2010-10-28
nice, there are missing ACPI handling
so try sudo sh -c 'echo 10 > /sys/class/backlight/acpi_video0/brightness'

---

### Post by lefty81 on 2010-10-28
on terminal:

yusuf@yusuf-netbook:~$ sudo sh -c 'echo 10 > /sys/class/backlight/acpi_video0/brightness'
[sudo] password for yusuf: 
yusuf@yusuf-netbook:~$ 

did not change anything.

---

### Post by pavolzetor on 2010-10-28
so just report bug in bugzilla, I am not acpi dev :/

---

### Post by lefty81 on 2010-10-28
is interested in my problem thank you very much.

---

