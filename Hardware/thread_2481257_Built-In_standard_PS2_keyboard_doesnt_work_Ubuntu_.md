---
title: "Built-In standard PS/2 keyboard doesnt work Ubuntu 22.04 LTS"
date: 2022-11-23
forum: Hardware
---

### Post by brueb44 on 2022-11-23
Hi all,
since buying my new laptop, the built in keyboard doesnt work consistently when using Ubuntu 22.04. Using Windows on the same laptop works fine. Furthermore, the keyboard works fine when in GRUB menu.
Fast Boot is turned off.

Checking for inputs using [this website]("https://www.keyboardtester.com/tester.html") shows that inputs are registered, but very delayed and inaccurately ( e.g pressing 'm' once, registers the press 3 seconds later, Then registers 'm' as if I was pressing the key down).
I was unable to find the exact keyboard type on Linux. but switching over to Windows I was able to find this information:

[COLOR=#000000]The keyboard itsself is a standard PS/2 keyboard[/COLOR]
[COLOR=#000000]The windows driver used is as follows:[/COLOR]
[COLOR=#000000]Driver C:\WINDOWS\SYSTEM32\DRIVERS\I8042PRT.SYS (10.0.22000.653)
[/COLOR]No idea if thats helpful in any way but I thought Id add it.

Im fairly new to Linux/Ubuntu so im not sure what commands to run on the command line for useful information to help diagnose the issue.
Heres some output that might help. It seems the keyboard isnt detected as an input at all?
```

sudo evtest
No device specified, trying to scan all of /dev/input/event*
Available devices:
/dev/input/event0:    Power Button
/dev/input/event1:    Lid Switch
/dev/input/event2:    Video Bus
/dev/input/event3:    Integrated Camera: Integrated C
/dev/input/event4:    Integrated Camera: Integrated I
/dev/input/event5:    Logitech Optical USB Mouse
/dev/input/event6:    USB USB Keyboard
/dev/input/event7:    USB USB Keyboard Consumer Control
/dev/input/event8:    USB USB Keyboard System Control
/dev/input/event9:    Ideapad extra buttons
/dev/input/event10:    ELAN2841:00 04F3:31AD Mouse
/dev/input/event11:    ELAN2841:00 04F3:31AD Touchpad
/dev/input/event12:    HD-Audio Generic HDMI/DP,pcm=3
/dev/input/event13:    HD-Audio Generic HDMI/DP,pcm=7
/dev/input/event14:    HD-Audio Generic Mic
/dev/input/event15:    HD-Audio Generic Headphone

```

```

WARNING: running xinput against an Xwayland server. See the xinput man page for details.
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer:17                     	id=6	[slave  pointer  (2)]
&#9116;   &#8627; xwayland-relative-pointer:17            	id=7	[slave  pointer  (2)]
&#9116;   &#8627; xwayland-pointer-gestures:17            	id=8	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; xwayland-keyboard:17                    	id=9	[slave  keyboard (3)]

```

Any and all help is greatly appreciated and would finally let me use my laptop more freely!

Thanks in advance.

---

### Post by slushee2 on 2023-06-06
Have yo managed to find a fix? I have the exact same issue

---

### Post by ggiovanet on 2023-07-12
I have the same problem with a Lenovo Idepad sLim (AMD Ryzen 7300 chipset).
Keyboard and touchpad work fine on BIOS, Windows and Grub, bu stop working on ubuntu. I tried different kernels and different distros as well with no success...

---

### Post by Autodave on 2023-07-15
ggiovanet posted his laptop name.....how about you other ones tell us what you are using?

---

