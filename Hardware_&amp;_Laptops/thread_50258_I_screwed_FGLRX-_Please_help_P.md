---
title: "I screwed FGLRX- Please help :P"
date: 2005-07-19
forum: Hardware &amp; Laptops
---

### Post by leezer3 on 2005-07-19
Hi guys,
Now this is NOT a problem with compiling or installing FGLRX, & I know my xorg.conf is correct, as it was working before I bust it. What I need is help to fix it :oops:

This is the situation:
[list]
[*]Tried to compile plib 1.4.8- Errors. Trace these down to a component of MESA not being installed properly; I have all devs etc installed, so I have a poke in Synaptic.
[*]Installed libglu1-mesa & devel version, replacing the xlib-mesa stuff already installed.
[*]Compile etc. didn't work, and FGLRX was bust so I restored the system to it's previous state
[*]FGLRX still doesn't work, so I try reinstalling the X server & recompiling the driver
[*]Still bust!!!!!
[*]Install plib from the Debian reps (What I probably should have done in the first place  :-# )
[*]Run for help :P
[/list] 

Help me please!

Thanks

-Leezer-

---

### Post by mad_scientist03 on 2005-07-19
I'm not sure this would work, but you could try uninstalling the xorg-driver-fglrx package and reinstall it. You could also try "sudo dpkg-reconfigure xserver-xorg" and see if being able to select from Ubuntu's list of drivers is at all helpful you.

Sorry if this turns out to be a waste.

---

### Post by leezer3 on 2005-07-20
Panic over :)
Steps to take:
[list]
[*]Revert to old system state.
[*]Install the xorg fglrx driver package from Synaptic.
[*]Recompile & install current ATI drivers.
[*]Reboot
[/list] 

-Leezer-

---

### Post by leezer3 on 2005-07-20
Panic over :)
Steps to take:
[list]
[*]Revert to old system state.
[*]Install the xorg fglrx driver package from Synaptic.
[*]Recompile & install current ATI drivers.
[*]Reboot
[*]Uninstall xorg fglrx package
[/list] 

-Leezer-

---

