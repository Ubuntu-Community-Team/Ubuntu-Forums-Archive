---
title: "Laptop HMDI to TV Not Working"
date: 2023-07-29
forum: Hardware
---

### Post by cwalins on 2023-07-29
[SIZE=2][FONT=arial] I am trying to connect my laptop to my TV using a HMDI cable and I am having problems.
[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]My Computer is a HP 15 TouchSmart with a Mesa DRI Intel HD Graphics 4400 (HSW GT2) graphics card.  I am running Ubuntu 20.04 LTS 64 bit, with Kernel Linux 5.4.0-155-generic x86_64, and MATE 1.24.0. The computer was purchased early 2015 with Windows originally installed.  Windows was removed.[/FONT][/SIZE]

[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]When I connect the computer to the TV and turn the computer on I see the hp logo as it boots up, then the Ubuntu logo, and finally the wallpaper.  After several minutes the mouse pointer disappears from the computer’s screen and appears on the TV.  The MATE desktop does not appear (no icons or task bar).  I can move the mouse pointer around and right click to get the menu to create a new folder, etc.  But that is all.
[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]I went into the BIOS to look for some type of setting but found none.[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]The command:
[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]lspci -k | grep -EA3 'VGA|3D|Display'
[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]Results in:[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]	Subsystem: Hewlett-Packard Company Haswell-ULT Integrated Graphics Controller[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]	Kernel driver in use: i915[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]	Kernel modules: i915
[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]The Intel web site says the drivers are provided and maintained by the Linux distribution vendors.  I have been updating Ubuntu regularly.  So, I should have the latest drivers.[/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]I found the Mesa web site and it has instructions for updating the Ubuntu drivers.  But, I am not sure that will solve my problem.[/FONT][/SIZE]

[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]
 [/FONT][/SIZE]
[SIZE=2][FONT=arial] [/FONT][/SIZE][SIZE=2][FONT=arial]Any advice?[/FONT][/SIZE]

---

### Post by TheFu on 2023-07-30
Force standard TV resolution and 60hz updates. Try these:
1920x1080     60.00  
1280x720      60.00

---

### Post by cwalins on 2023-07-30
> **TheFu said:**
> Force standard TV resolution and 60hz updates. Try these:
1920x1080     60.00  
1280x720      60.00

How is this done?  The menu on the TV does not give me these options.  I can not find any menu on the computer that allows these adjustments.  Do I make these adjustments using the MATE terminal window and commands?

---

### Post by #&amp;thj^% on 2023-07-30
Not on the TV, but through your Mate Setting Display
you can use keys {Super + p} to call it or run:
```
mate-display-properties
```
EDIT corrected code above
Here you can make those suggested changes

---

### Post by cwalins on 2023-07-31
> **1fallen said:**
> Not on the TV, but through your Mate Setting Display
you can use keys {Super + p} to call it or run:
```
mate-display-properties
```
EDIT corrected code above
Here you can make those suggested changes

In short problem solved.

I typed in the command and was instructed that I need to download a software package to run the command, and I did.

The newly installed software package is called Control Center.  Opened the program and clicked on the Displays icon in the Hardware section.  A window opened and there were 2 displays noted, the laptop monitor and the TV.  Clicked on the Mirror Display button and the laptop display now appeared on the TV.  Clicked on the Sound icon, Output tab, clicked on the HDMI output option and got sound.

I thank all who helped.

---

