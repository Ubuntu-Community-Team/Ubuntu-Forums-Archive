---
title: "NVIDIA gforce 7300 go x server issues"
date: 2009-09-13
forum: Hardware
---

### Post by themadjester on 2009-09-13
I installed 9.04 and got everything working mostly how I wanted it, unfortunately my beautiful 23' flat-screen was not being recognized by the nvidia v180 graphics driver (otherwise 180 was working well).

So, I reading somewhere that newer versions of drivers solve the problem I went to nvidia's site, got an 185.?? version and went about installing that...:
1) ctnl+alt+f2
2) etc/init.d/gdm stop
3) sh install driver as route, it says it needs to do some kernal compiling I don't understand the purpose of - so I hit ok... >.>
4) attempt to restart the x server: etc/init.d/gdm restart
but no dice... thing crashes, and now I am stuck with low graphics mode.

Now, I think part of the problem was that their gforce go 7x series driver for notebooks, excludes my 7300, as they apparently do not like me, but I felt inclined to try it anyway since they are likely lazy with their documentation (the way they are apparently also lazy in supporting the products they launch).

So basically, I am kind of over my head here as I do not know so much about what that this xconf stuff does, its scope etc.. anyone mind helping me? Ideally I would like to use the newer driver if the error is not what I think it is. If not I do not know how to get back to 180.x ... the installation thinks its using the 180 driver right now.

here are some logs that are apparently useful for debugging this stuff from my reading:
p   nvidia-173-kernel-source                 - NVIDIA binary kernel module source                
i   nvidia-173-modaliases                    - Modaliases for the NVIDIA binary X.Org driver     
i A nvidia-180-kernel-source                 - NVIDIA binary kernel module source                
i A nvidia-180-libvdpau                      - Video Decode and Presentation API for Unix        
p   nvidia-180-libvdpau-dev                  - Video Decode and Presentation API for Unix develop
i   nvidia-180-modaliases                    - Modaliases for the NVIDIA binary X.Org driver     
p   nvidia-71-kernel-source                  - NVIDIA binary kernel module source                
i   nvidia-71-modaliases                     - Modaliases for the NVIDIA binary X.Org driver     
p   nvidia-96-kernel-source                  - NVIDIA binary kernel module source                
i   nvidia-96-modaliases                     - Modaliases for the NVIDIA binary X.Org driver     
p   nvidia-cg-toolkit                        - NVIDIA Cg Toolkit Installer                       
i   nvidia-common                            - Find obsolete NVIDIA drivers                      
v   nvidia-glx                               -                                                   
p   nvidia-glx-173                           - NVIDIA binary Xorg driver                         
p   nvidia-glx-173-dev                       - NVIDIA binary Xorg driver development files       
i   nvidia-glx-180                           - NVIDIA binary Xorg driver                         
p   nvidia-glx-180-dev                       - NVIDIA binary Xorg driver development files       
p   nvidia-glx-71                            - NVIDIA binary Xorg driver                         
p   nvidia-glx-71-dev                        - NVIDIA binary Xorg driver development files       
p   nvidia-glx-96                            - NVIDIA binary Xorg driver                         
p   nvidia-glx-96-dev                        - NVIDIA binary Xorg driver development files       
v   nvidia-glx-dev                           -                                                   
p   nvidia-kernel-common                     - NVIDIA binary kernel module common files          
v   nvidia-kernel-source                     -                                                   
i A nvidia-settings                          - Tool of configuring the NVIDIA graphics driver   

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
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

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

log that show up when it failed to launch the first time:
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux - 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep 13 12:07:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
Error: API mismatch: the NVIDIA kernel module has version 180.44,
but this NVIDIA driver component has version 185.18.36.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the
(EE) NVIDIA(0):     system's kernel log for additional error messages and
(EE) NVIDIA(0):     consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

---

### Post by themadjester on 2009-09-17
looks like I solved part of this...

for anyone who comes across this:
essentially my problem was that I could not backdate the drivers because the old ones would still always be installed... so I google around for "removing nvidia xorg drivers"  and found some dangerous commands that go through directories and delete files...

at that point I was able to get back to 180. I also noted that my VGA cable works, so I dropped DVI and the monitor is now usable. It is too bad however that I cannot use DVI but I haven't noticed a difference really. 

Now to fix the mic problems... /sigh

---

