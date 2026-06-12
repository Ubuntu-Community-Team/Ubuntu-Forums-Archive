---
title: "ASUS N53SV and Ubuntu 11.04"
date: 2011-04-12
forum: Hardware
---

### Post by Elkaz on 2011-04-12
Hello, folks. 
I have a problem with my new laptop from ASUS (N53SV). 

It has a hybrid graphic system, but I can not use any of them. The LED shows that nVidia card is active, but when I am going to nVidia setting I am getting a message that "You do not appear to use nVidia X Driver". 

There is no official linux drivers for my GT 540M. 
What nvidia packages I have installed: 

```

elkin@elkin-N53SV:~$ aptitude search nvidia
p   nvidia-173                                                                  - NVIDIA binary Xorg driver, kernel module and VDPAU library                            
p   nvidia-173-dev                                                              - NVIDIA binary Xorg driver development files                                           
p   nvidia-173-kernel-source                                                    - Transitional package for nvidia-glx-173-kernel-source                                 
p   nvidia-180-kernel-source                                                    - Transitional package for nvidia-glx-185-kernel-source                                 
p   nvidia-180-libvdpau                                                         - Transitional package for nvidia-185-libvdpau                                          
p   nvidia-180-libvdpau-dev                                                     - Transitional package for nvidia-185-libvdpau-dev                                      
p   nvidia-180-modaliases                                                       - Transitional package for nvidia-185-modaliases                                        
p   nvidia-185-kernel-source                                                    - Transitional package for nvidia-glx-185-kernel-source                                 
p   nvidia-185-libvdpau                                                         - Transitional package for nvidia-185-libvdpau                                          
p   nvidia-185-libvdpau-dev                                                     - Transitional package for nvidia-185-libvdpau-dev                                      
p   nvidia-96                                                                   - NVIDIA binary Xorg driver, kernel module and VDPAU library                            
p   nvidia-96-dev                                                               - NVIDIA binary Xorg driver development files                                           
p   nvidia-96-kernel-source                                                     - Transitional package for nvidia-glx-96-kernel-source                                  
p   nvidia-cg-toolkit                                                           - Cg Toolkit - GPU Shader Authoring Language                                            
i   nvidia-common                                                               - Find obsolete NVIDIA drivers                                                          
i   nvidia-current                                                              - NVIDIA binary Xorg driver, kernel module and VDPAU library                            
p   nvidia-current-dev                                                          - NVIDIA binary Xorg driver development files                                           
p   nvidia-glx-173                                                              - Transitional package for nvidia-glx-173                                               
p   nvidia-glx-173-dev                                                          - Transitional package for nvidia-glx-173-dev                                           
p   nvidia-glx-180                                                              - Transitional package for nvidia-glx-185                                               
p   nvidia-glx-180-dev                                                          - Transitional package for nvidia-glx-185-dev                                           
p   nvidia-glx-185                                                              - Transitional package for nvidia-glx-185                                               
p   nvidia-glx-185-dev                                                          - Transitional package for nvidia-glx-185-dev                                           
p   nvidia-glx-96                                                               - Transitional package for nvidia-glx-96                                                
p   nvidia-glx-96-dev                                                           - Transitional package for nvidia-glx-96-dev                                            
i A nvidia-settings                                                             - Tool of configuring the NVIDIA graphics driver                                        
v   nvidia-va-driver                                                            -                                                  

```

This is my xorg.conf:

```


elkin@elkin-N53SV:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.30  (buildmeister@swio-display-x86-rhel47-01.nvidia.com)  Fri Feb 25 14:54:56 PST 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fbdev"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Also I have a problem with touchpad — I can not disable it. 
Also I have problem with fn buttons (in Keyboard system menu I choosed Asus laptop keyboard, but it does not seems to work). Works only Wifi switch on/off, brightness control. Sound does not working :( (f10-f12).

Is there any way to make my graphic card to work? If no, how I can totally disable it and manage integrated intel graphic card? 

OS: Ubuntu 11.04, x86_64.
Model: ASUS N53SV (i5, 3 Gb RAM, GT 540M)

Thanks a lot for any help.

---

### Post by beew on 2011-04-12
Someone may have managed to disable the Nvidia card for some laptops.
[http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus](http://ubuntuforums.org/showthread.php?t=1657660&highlight=optimus)

Maybe you can also write to Nvidia.[ ]("http://ubuntuforums.org/showthread.php?t=1712278")
[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

With Optimus there is no way to use the Nvidia card even if Nvidia provides the Linux driver, so basically that means Nvidia no longer supports Linux laptop (some laptops have a BIOS switch to disable Optimus but they are rare and tend to be expensive)  Many Linux users probably don't care for gpu switching, but it is not unreasonable to ask Nvidia for a way to use the card it supposedly supports and the user has paid for.

---

### Post by komasoftware on 2011-04-14
Dont install the nvidia drivers and remove your xorg.conf
that worked for me...

here's my story : [http://ubuntuforums.org/showthread.php?t=1728038](http://ubuntuforums.org/showthread.php?t=1728038)

---

### Post by yahooking on 2011-04-28
i used acpi_call to disable the nvidia gpu at boot. This was evident with the reduced heat as well as better battery life. The LED trigger is always going to remain WHITE. It worked for me. 
I removed all nvidia drivers. Then i used the acpi_call trigger in rc.local to disable the nvidia gpu at boot. 
google acpi_call they have allot of progress on it.

---

### Post by sentythee on 2011-05-26
Late reply, but I'm sure we're not the only ones struggling with this.

Bumblebee ([https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)) should work for your graphics card problem. This works a lot better for me than switcheroo did. It won't automatically switch between the nvidia card and intel, but it does let you use both as needed.

Once you grab the files from github, you can install it by running install.sh as root. By default, the nvidia card will always be powered on, and you can tell an application to use it by running "optirun64 application". Everything not run this way will use the intel graphics.

You can turn off your graphics card to save power by running "bumblebee-disablecard" and re-enable it with "bumblebee-enablecard". Disabling the nvidia card when you're not using it will almost double your battery life. Most of those two scripts are already set up for you, but you'll need to make a minor change to both of them. To use either of these scripts, you'll need to install acpi_call first. This thread details that well (but don't blacklist the drivers):

[http://ubuntuforums.org/showthread.php?t=1569380](http://ubuntuforums.org/showthread.php?t=1569380)

That thread uses '\_SB.PCI0.PEG1.GFX0._OFF' to disable the card. You should be using '\_SB.PCI0.PEG0.GFX0.DOFF'. For people using different graphics cards, you can find what value you should be using by running 'test_off.sh' in whichever directory you downloaded acpi_call to.

Once acpi_call is set up, you can fix those two scripts. Open the bumblebee-disablecard script (vim `which bumblebee-disablecard`) and uncomment everything after (and including) 'rmmod nvidia'. At the bottom, you should see two lines starting with "echo NVOP" and "echo _PS3". Comment out the first one (or the second, it really doesn't matter) and replace the string with '\_SB.PCI0.PEG0.GFX0.DOFF'. Now open the script for bumblebee-enablecard. Do the same thing you did for bumblebee-disablecard, but replace the string with '\_SB.PCI0.PEG0.GFX0.DON'.

Good luck.

---

### Post by JanWiel on 2012-04-15
Just got an N53SV.  Installed Ubuntu 12.04 Beta-1 (now upgraded to Beta-2).
Everything works fine out of the box.  The only extra one needs to intall is
Bumblebee.  This worked shaky in Beta-1, but fine in Beta-2.

I'm using the nvidia-current driver.  The only tweak needed was to edit
/etc/bumblebee/xorg.conf.nvidia and set Option "ConnectedMonitor" to
"CRT".  Without, attaching an external monitor works, but the monitor
position and settings such as mirror do not work.  After setting to CRT,
this works fine too.

Tested everything, except writing a CD/DVD.  The only small twist is that
dimming using the keyboard works, but it frequently sets back the old
brightness.  Dimming using power management dialog works fine.

I'm very happy with this machine.   The battery lasts about 4 hours when
not doing much.   This is the model with 5200Mah.

---

### Post by Meezy on 2012-06-20
Hi JanWiel,

How is your machine running since the official release?  I installed 12.04, but my machine is constantly freezing.  I then have to reboot.

---

