---
title: "Auto-select dual monitor ServerLayout?"
date: 2006-06-01
forum: Hardware &amp; Laptops
---

### Post by jgoguen on 2006-06-01
I've got an xorg.conf (relevant sections below) that allows me to use an external monitor with my laptop. It's set up so that the laptop screen is the main screen and the external monitor is to the right, both at 1024x768 (max resolution of the laptop screen. This works perfectly fine, but what I'm looking to do now is to have a single or dual monitor configuration automatically selected depending on whether there's an external monitor connected or not. Even if this only happens when the laptop boots, or if I have to restart X after attaching/removing the monitor, that would be fine. It's very rare that I would need/like to add/remove a monitor in the middle of a session. I use the i810 driver.  Anyone know how I could do this?

But if I can can attach/remove a monitor in the middle of a session and resize the desktop without restarting anything, even better :)

xorg.conf:
```
Section "ServerLayout"
 Identifier "Default Layout"
 Screen 0 "Default Screen"
 Screen 1 "Default Screen 2" RightOf "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
 InputDevice "Synaptics Touchpad"
EndSection
Section "ServerFlags"
 Option "Xinerama" "True"
EndSection
ection "Module"
 Load "bitmap"
 Load "dbe"
 Load "ddc"
 Load "dri"
 Load "extmod"
 Load "freetype"
 Load "glx"
 Load "int10"
 Load "record"
 Load "type1"
 Load "vbe"
EndSection
Section "Device"
 Identifier "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
 Driver "i810"
 BusID "PCI:0:2:0"
 Option "MonitorLayout" "CRT,LFP"
 VideoRam 65536
 Option "FlipPrimary" "false"
 Option "DevicePresence" "true"
 Option "VBERestore" "false"
 Screen 0 
EndSection
Section "Device"
 Identifier "Intel Corporation 82830 CGC [Chipset Graphics Controller] 2"
 Driver "i810"
 BusID "PCI:0:2:0"
 Option "MonitorLayout" "CRT,LFP"
 Option "DevicePresence" "true"
 VideoRam 65536
 Option "VBERestore" "false"
 Screen 1 
EndSection
#TFT
Section "Monitor"
 Identifier "Generic Monitor"
 Option "DPMS"
 HorizSync 28-49
 VertRefresh 43-72
EndSection
#External LCD
Section "Monitor"
 Identifier "Generic Monitor 2"
 Option "DPMS"
 HorizSync 28-49
 VertRefresh 43-72
EndSection
Section "Screen"
 Identifier "Default Screen 2"
 Device "Intel Corporation 82830 CGC [Chipset Graphics Controller] 2"
 Monitor "Generic Monitor 2"
 DefaultDepth 24
 SubSection "Display"
 Depth 24
 Modes "1024x768"
 EndSubSection
EndSection
Section "Screen"
 Identifier "Default Screen"
 Device "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
 Monitor "Generic Monitor"
 DefaultDepth 24
 SubSection "Display"
 Depth 24
 Modes "1024x768"
 EndSubSection
EndSection
Section "DRI"
 Mode 0666 #Disable by Xinerama
EndSection
```

---

### Post by magnusbb on 2006-06-02
I am not very into configurations of X, espcially considering that the driver manifactorers often change the options from release to release. I am having a similar problem myself, relating to the use of an external monitor.
Link: [http://www.ubuntuforums.org/showthread.php?t=186581](http://www.ubuntuforums.org/showthread.php?t=186581)

Earlier I used a script like this at bootup to detect the presense of an external monitor, and then change the xorg.conf accordingly:

```
# determine whether an external display is attached
#cp /etc/X11/xorg.conf /etc/X11/xorg.conf.pre-local
if /usr/sbin/ddcprobe | grep -q "analog signal"; then
    echo "External Display attached."
    # set external display as exclusive primary
    # cat /etc/X11/xorg.conf.pre-local | sed 's#"Single"#"Single,Reverse"#g' > /etc/X11/xorg.conf
else
    echo "Using build-in LCD."
    # set build-in LCD as exclusive primary display
    # cat /etc/X11/xorg.conf.pre-local | sed 's#"Single,Reverse"#"Single"#g' > /etc/X11/xorg.conf
fi
```

You can have a look at this script and see what it gives you. As you see, central is the command "/usr/sbin/ddcprobe" which is included in the standard install of Ubuntu.

When finished, simply add this script to:
/etc/init.d/ and make it executable with "chmod +x".

Then do an "update-rc-d script_name defaults", and you shall be up and running quickly.

---

### Post by jgoguen on 2006-06-02
Thanks a lot, that does exactly what I'm looking for.  I had to change "analog signal" to "monitorname", and I made symlinks to existing xorg.single and xorg.dual files based on the required configuration.

---

### Post by blue_chili on 2006-09-18
> **magnusbb said:**
> 

Earlier I used a script like this at bootup to detect the presense of an external monitor, and then change the xorg.conf accordingly:

```
# determine whether an external display is attached
#cp /etc/X11/xorg.conf /etc/X11/xorg.conf.pre-local
if /usr/sbin/ddcprobe | grep -q "analog signal"; then
    echo "External Display attached."
    # set external display as exclusive primary
    # cat /etc/X11/xorg.conf.pre-local | sed 's#"Single"#"Single,Reverse"#g' > /etc/X11/xorg.conf
else
    echo "Using build-in LCD."
    # set build-in LCD as exclusive primary display
    # cat /etc/X11/xorg.conf.pre-local | sed 's#"Single,Reverse"#"Single"#g' > /etc/X11/xorg.conf
fi
```

You can have a look at this script and see what it gives you. As you see, central is the command "/usr/sbin/ddcprobe" which is included in the standard install of Ubuntu.

When finished, simply add this script to:
/etc/init.d/ and make it executable with "chmod +x".

Then do an "update-rc-d script_name defaults", and you shall be up and running quickly.

Can you explain this further as I'm a bit ignorant with this sort of thing. I have my external monitor working fine but the problem is when I want to use my laptop by itself it still thinks the external monitor is there and opens things up on it! To clarify, your script will automatically detect if there is an external monitor attached and run the appropriate configuration? So you add this script to the directory /etc/init.d/ which is where scripts need to go to be run at bootup? Is that correct? Can you explain how exactly the script does the correct configuration - the only line of code I can see:
* is if /usr/sbin/ddcprobe | grep -q "analog signal"; then*

Is that what does the selecting of the correct configuration?

Thanks!

---

### Post by blue_chili on 2006-09-19
I've figured out that the line with ddcprobe is supposed to detect your monitor and the rest are just commented out until you go to use them. Its weird though, if I use the ddcprobe by itself from the command line it says that the monitorname is "color lcd". This identifier was used in my old xorg.conf which is now called xorg.conf_backup so I'm not sure where it is picking up "color lcd" from. Also, when I open the file xorg.conf it is just blank for some reason but my external monitor is working fine on each reboot.

It also says to run the command update-rc-d script_name defaults, this returns "command not found" on my machine.

Finally, the there's mention of creating symmlinks between the single and external monitor layouts - can someone please explain?

---

### Post by sportman1280 on 2006-09-25
Im also having issues.  the monitor is detected fine during boot. and displays 100% perfectly, until i hit where the login screen is.  then black screen :(.  theres no one that has this figured out yet?  someones gotta hava a successful laptop docking story. lol.

---

