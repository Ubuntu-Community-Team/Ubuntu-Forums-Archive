---
title: "Synpatics touchpad doesnt work after latest Dapper updates"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by motin on 2006-12-18
With the latest kernel update (still -27 but apparently a minor version upgrade) came problems. I think suspend is not working but I do not want to try before posting this...

My touchpad went dead after the reboot, and is still dead after 3 reboots... I have installed qsynaptics (again - it was apparently removed) and it says that I need to install teh synaptics driver and enable shared memory in X config file... However that is done?

I reinstalled xserver-xorg-input-synaptics with no success. 

Found errors in Xorg.0.log: here is the Synaptics part in the near end of the log:

(II) Synaptics touchpad driver version 0.14.3
Synaptics Touchpad no synaptics event device found (checked 12 nodes)
(**) Option "Device" "/dev/psaux"
(**) Option "SHMConfig" "on"
(**) Option "MaxTapTime" "0"
(**) Option "MaxTapMove" "0"
(**) Option "HorizScrollDelta" "0"
(**) Option "RTCornerButton" "0"
(**) Option "RBCornerButton" "0"
(**) Option "TapButton1" "0"
(**) Option "TapButton2" "0"
(**) Option "TapButton3" "0"
Query no Synaptics: 6003C8
(EE) Synaptics Touchpad no synaptics touchpad detected and no repeater device
(EE) Synaptics Touchpad Unable to query/initialize Synaptics hardware.
(EE) PreInit failed for input device "Synaptics Touchpad"
(II) UnloadModule: "synaptics"

What now?

Very thankful for tips and help!

---

### Post by garciadc on 2006-12-18
I gave up on Dapper and upgraded to Eft.  Touchpad works perfect

---

### Post by motin on 2006-12-18
> **garciadc said:**
> I gave up on Dapper and upgraded to Eft.  Touchpad works perfect

If only it was possible: [https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/71979](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/71979)

Luckily I had a fresh 1:1 ghost image of the hard drive partitions. 

About the touchpad: I restarted again and now it works. Strange things happen, next time I will restart 4 times before posting...

---

