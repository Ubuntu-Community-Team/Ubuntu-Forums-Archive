---
title: "New Mouse"
date: 2006-01-18
forum: Hardware &amp; Laptops
---

### Post by heart_reaver on 2006-01-18
Hi there 

I am having optical mouse which is having some problem in clicking so i plug old serial mouse. This is not detected, how can i do that. In general, how can i detect new hardware like monitor, LCD display ...

---

### Post by heart_reaver on 2006-01-27
That was simple 

just needed to configure my xorg.conf file 

This file is at /etc/X11/

In that you can always switch mouse drivers from command line,
you'll have to make changes to your xorg.conf 


```

# comments start with a "#"
#############################for PS2/usb
connector###############
Section "InputDevice"
	Identifier  "Mouse0"
        Driver	    "mouse"
        Option      "Protocol" "IMPS/2"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "no"
EndSection
#################################################################

#####################For serial
connector########################
Section "InputDevice"
 Identifier  "Mouse0"
 Driver      "mouse"
 Option     "Protocol" "Microsoft"
 Option     "Device" "/dev/ttyS0"
EndSection
#################################################################



```

Remember that at a time, only one configuration should be active (depending on the mouse being used).

**CAUTION :: Take backup of all files you are modifing **
Open your eyes and then modify it 

Dont foreget to restart your Xserver

---

