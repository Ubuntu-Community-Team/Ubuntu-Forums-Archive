---
title: "Touchpad malfunctiong on dell laptop"
date: 2023-06-04
forum: Hardware
---

### Post by ghoracek on 2023-06-04
Ubuntu 23.04/Dell Latitude 5470.  Searched in vain for similar issue looking for solutions.  Sometime over the last few months my touchpad has been acting erratically.  I am unable to inactivate while typing, plugging in a wired mouse does not inactive touchpad.  I've tried all the Gnome extensions for the touchpad t0 no avail.  Most irritating is that when i try to move the cursor to select objects or menus, the screen scrolls and not in any one direction (ignoring natural scrolling selection).  If i get anywhere near the pad when typing, my next keystroke entry could be anywhere.  My question today is should the installed Alps touchpad be listed twice in "cat /proc/bus/input/devices'?

I: Bus=0011 Vendor=0002 Product=0008 Version=0800
N: Name="AlpsPS/2 ALPS DualPoint Stick"
P: Phys=isa0060/serio1/input1
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=21
B: EV=f
B: KEY=70000 0 0 0 0
B: REL=3
B: ABS=1000000

I: Bus=0011 Vendor=0002 Product=0008 Version=0800
N: Name="AlpsPS/2 ALPS DualPoint TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input6
U: Uniq=
H: Handlers=mouse1 event6 
B: PROP=1
B: EV=b
B: KEY=e520 70000 0 0 0 0
B: ABS=260800001000003

If nor, how do I get rid of one and which one?

Should I just back up my files and reinstall fresh copy?

---

### Post by TheFu on 2023-06-04
If it were me, I'd boot into a Try Ubuntu environment and see if that fixes the issue.  If it doesn't, then a fresh reinstall isn't likely to fix it.

Almost always, touchpads and mice appear as USB devices, so you can disable them.  Certainly you can disable the touchpad in the BIOS and use a mouse instead.

Have you tried using a different touchpad driver and manually making the settings you desire using Synapse?  I haven't set up my touchpads in a few years and Synapse was the program that allowed more detailed control.  At login for a local/console GUI session, I have this setup:
```
synclient AreaRightEdge=850 &
synclient AreaLeftEdge=50 &
synclient TapButton1=1 &
synclient TapButton2=3 &
synclient TapButton3=2 &
```

This only works with touchpads that are supported. Synapse may be out of favor these days. IDK.
[https://wiki.archlinux.org/title/Touchpad_Synaptics](https://wiki.archlinux.org/title/Touchpad_Synaptics) has more details and says most ALPS are included.

I get the feeling none of this works with Wayland, so that would be the first thing to check. Are you using Wayland or X11?

---

### Post by ghoracek on 2023-06-05
No, I'm using X11; but I switched to Wayland just to see and nothing changed.  Went through all the desktop options I have at log in (gnome, gnome classic, ubuntu, etc) and they all had the same random scrolling and erratic uncontrollable cursor  Went with your first statement about trying a live distro (Fedora 37) and this solved all the issues -- lost the ability to tap instead of clicking, but I'm willing to make that sacrifice (and there is probably a setting somewhere to fix that).  So my feeling is that having two input sections for the ALPs touchpad is the issue.  So I will either clean install ubuntu or probably just try Fedora to see if its as great as all the chatter on the web makes it to be.

---

### Post by ghoracek on 2023-06-05
I’ll continue to think about my options, but I do want to thank you for your input. It definitely moved me from a point of high frustration to one of ‘let’s fix this’.

---

### Post by TheFu on 2023-06-05
Having multiple gnome-based DEs used by the same userid on the same system can cause conflicts.
While you are picking which DE to use, it is best to always use a new, different, account for each.  Linux is multi-user.  Take advantage of that.

To see of the conflicts ARE the issue, you can create a new userid, login with it with 1 of the DEs and only use it with 1 DE.

BTW, on recent "Ubuntu Desktops", that's Gnome 4 as the DE.  I think 20.04 is Gnome3 and before then it was Unity for the DE.  Classic Gnome is probably Gnome2, but I don't know.  I avoid Gnome stuff due to bloat.

---

### Post by ghoracek on 2023-06-05
All those ‘other’ options are not a result of distribution hopping but rather just upgrading Ubuntu over the years as it’s default desktop changed.  I do any distribution testing in a virtual machine.  Time for a clean install to clear out the ‘mess’.   Gnome is perfect for me as my workflow is not menu driven which most other distros feature. Mint, PopOS and others are solid but slow me down.  Again thanks for the help.

---

