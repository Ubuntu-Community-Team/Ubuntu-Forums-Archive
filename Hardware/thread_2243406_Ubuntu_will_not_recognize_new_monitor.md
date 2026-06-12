---
title: "Ubuntu will not recognize new monitor"
date: 2014-09-08
forum: Hardware
---

### Post by notquitestr8t2 on 2014-09-08
I have a new monitor. It is connected using the HDMI port. My graphics driver is Nvidia but it is reporting not currently in use. However, the conf files indicates that it is using the nvidia driver. 

The conf file is below. I removed all nvidia drivers with Synaptic. Then I installed again from command line - sudo apt-get install nvidia-current and ran sudo nvidia-xconfig. It did not do a thing. The monitor shown below is the old one and it is incorrect. The existing monitor is a 21 Acer S241HL.
How can I get Ubuntu to recognize the new monitor?
Why does ubuntu only show my display as a laptop?

ubuntu 12.04 LTS

ection "ServerLayout" 
    Identifier     "Default Layout" 
    Screen      0  "Screen0" 0 0 
    InputDevice    "Keyboard0" "CoreKeyboard" 
    InputDevice    "Mouse0" "CorePointer" 
    Option         "Xinerama" "0" 
EndSection 
 
Section "Module" 
    Load           "glx" 
EndSection 
 
Section "InputDevice" 
 
    # generated from default 
    Identifier     "Keyboard0" 
    Driver         "kbd" 
EndSection 
 
Section "InputDevice" 
 
    # generated from default 
    Identifier     "Mouse0" 
    Driver         "mouse" 
    Option         "Protocol" "auto" 
    Option         "Device" "/dev/psaux" 
    Option         "Emulate3Buttons" "no" 
    Option         "ZAxisMapping" "4 5" 
EndSection 
 
Section "Monitor" 
    Identifier     "Configured Monitor" 
EndSection 
 
Section "Monitor" 
    Identifier     "Monitor0" 
    VendorName     "Unknown" 
    ModelName      "Samsung SyncMaster" 
    HorizSync       30.0 - 81.0 
    VertRefresh     56.0 - 75.0 
EndSection 
 
Section "Device" 
    Identifier     "Configured Video Device" 
    Driver         "nvidia" 
    Option         "NoLogo" "True" 
EndSection 
 
Section "Device" 
    Identifier     "Device0" 
    Driver         "nvidia" 
    VendorName     "NVIDIA Corporation" 
    BoardName      "GeForce GTX 560 Ti" 
EndSection 
 
Section "Screen" 
    Identifier     "Default Screen" 
    Device         "Configured Video Device" 
    Monitor        "Configured Monitor" 
    DefaultDepth    24 
    Option         "UseDisplayDevice" "DFP" 
EndSection 
 
Section "Screen" 
    Identifier     "Screen0" 
    Device         "Device0" 
    Monitor        "Monitor0" 
    DefaultDepth    24 
    Option         "TwinView" "0" 
    Option         "TwinViewXineramaInfoOrder" "DFP-2" 
    Option         "metamodes" "1440x900 +0+0" 
    SubSection     "Display" 
        Depth       24 
    EndSubSection 
EndSection

---

### Post by grahammechanical on 2014-09-08
Are you saying that when Ubuntu loads nothing is appearing on this new monitor? Or are you able to use Ubuntu with this monitor?

When we use an open source video driver we can use the Displays utility to detect monitors. Likewise when we use an Nvidia proprietary video driver the Nvidia Xserver settings manager will have an option to detect displays. Are you saying that either of these display setting managers is not reporting your monitor correctly?

The Xserver gets it information about monitor resolutions from the Extended Display Identification Data (EDID) in the electronics in the monitor. I, recently, was able to connect a new monitor (actually a TV) without having to do anything. At first I could not get the full range of resolutions but that was because I was using a VGA cable. Once I started using a HDMI cable I got the full range. The correct information was displayed on boot without my doing anything. This was on the open source video driver.

I think that at some point you have created a Xserver configuration file that is being read every time you boot instead of the Xserver reading the EDID at every boot. That is why Ubuntu thinks you are still using the old monitor.

Regards.

---

### Post by notquitestr8t2 on 2014-09-11
Thank you. Perhaps that is what is happening. How do I allow the detection to take place? I can use the monitor but I have very few display options and of course I can not take advantage of the full screen available.

---

### Post by didier5 on 2014-09-11
It should remain links with the old monitor.
sudo apt-get --*-purge* *remove/autoremove* "package"

--
You could also rename the .conf file and reboot ?

---

