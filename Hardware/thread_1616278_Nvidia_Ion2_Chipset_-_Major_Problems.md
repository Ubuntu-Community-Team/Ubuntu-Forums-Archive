---
title: "Nvidia Ion2 Chipset - Major Problems"
date: 2010-11-08
forum: Hardware
---

### Post by jorny32 on 2010-11-08
Hey guys,

My Computer
-Asus Eee PC 1015PN
-Ubuntu 10.04 64bit
--Intel Atom 550 Dual-Core 1.50Ghz
--Nvidia Ion2 Graphics card w/onboard Intel GMA also(PROBLEM)


What I did - I install the Nvidia drivers that "Hardware Drivers" tells me should be installed and are recommended. 

Problem - Cannot run GUI correctly, only works for 30ish seconds before it freezes everything but the mouse.

I NEED HELP. I have tried it twice. 

This computer has the "Optimus" tech that switches the good Ion2 card on when you really need power and I think that is the problem. I know the switch only works in Win7 but why does it tell me to install these drivers then break everything????

ALSO, while I work on this, how can I revert back to my other drivers while in terminal, as in disable the current driver?

---

### Post by P4man on 2010-11-08
You need to configure the bios to disable optimus and set it manually to either intel or nvidia graphics.  If you set it to nvidia, you can enable the drivers (at the expense of battery life).

If you dont have such an option in the bios, you shouldnt install the nvidia drivers. As you said, optimus is not (yet?) supported on linux.

To remove the nvidia driver, try

```
sudo jockey-text -l
```

to list your drivers, and -d to disable it (-h for help)

---

### Post by Szat on 2011-02-10
I also have the EEE 1015PN and was having the same problem. I found that by installing the Nvidia binary driver manually, restarting, and then installing the recommended driver it fixed my gui/freezing problem. Hope it works for you! Hope it keeps working for me! 

Start here:
```
 sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
 sudo apt-get update && sudo apt-get install nvidia-current
```

This might be helpful too: [Hardware Support for Netbooks]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/#Asus Eee PC 1015PN")

---

