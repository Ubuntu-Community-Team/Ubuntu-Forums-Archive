---
title: "upgraded to 9.10, now am forced to login MULTIPLE times after bootup"
date: 2009-11-09
forum: Installation &amp; Upgrades
---

### Post by neutron68 on 2009-11-09
My upgraded Mythbuntu 9.10 system is forcing me to login (gdm?) no matter if I have the system set to auto-login with my username or not.
It's like it is ignoring the /etc/dgm/custom.conf file contents - which I had set to auto-login.

Forcing me to login with my password wouldn't be so bad, but the system often forces me to login at least 2 times before I will see the Ubuntu desktop. At one point earlier this week, the system made me login 10 TIMES before it FINALLY booted into Ubuntu!

I had Mythbuntu 9.04 running fine and performed the upgrade to Mythbuntu 9.10 by typing the command line "sudo update-manager -d".  The upgrade seemed to go ok.  

SYMPTOMS:

At each login, I see the black Mythbuntu splash screen with the animated white line under the word, then the screen goes black, then I get the Ubuntu login window. If I enter the password for my username, the screen goes back to the black Mythbuntu splash screen with the animated white line under the word, then the screen goes black and then I get the Ubuntu login window agian, etc.

I'm not enough of a Ubuntu expert to know what would cause multiple logins to occur. Perhaps some part of gdm is crashing and causing a restart of gdm (the black screen I mentioned), and thus the multiple logins??

I went into the Mytyhbuntu Control Center and disabled the autostart of Mythtv - thinking it might help narrow down the search for the cause. So, after the multiple logins I end up at the Mythbuntu desktop.

Are there any logs I can check to get some clues as to what is going on?

I read about this gdm bug in Ubuntu 9.10:
[https://bugs.launchpad.net/ubuntu/+s...dm/+bug/447226](https://bugs.launchpad.net/ubuntu/+s...dm/+bug/447226)

Could this be what is happening to me? gdm and upstart are fighting each other and respawing gdm?

I need some help to fix this one.
Eric

---

### Post by DominicF on 2009-11-09
I also see this issue from today after rebuilding my box and apply all available updates.

---

### Post by DominicF on 2009-11-10
Hi,

Have you managed to solve this?

---

### Post by DominicF on 2009-11-10
I think I solved this.  I rebuilt my system again and reproduced the issue after installation completed.

Once I logged into the desktop again I went to synaptic package manager and selected gdm to be re-installed.

so, far it seems stable, I've rebooted a few times and I'm not asked to log in multiple times.

---

### Post by neutron68 on 2009-11-10
I have not found a cure yet.  

For background, I didn't have the problem of multiple logins right after I upgraded from 9.04 to 9.10.  It happened after downloading a bunch of updates using the Update manager.
So, maybe we got a poisoned version of gdm from an update??

I'll try reinstalling gdm from the Synaptic Package Manager and see if it cures my system, too.

Eric

---

### Post by neutron68 on 2009-11-11
> **neutron68 said:**
> I have not found a cure yet.  

For background, I didn't have the problem of multiple logins right after I upgraded from 9.04 to 9.10.  It happened after downloading a bunch of updates using the Update manager.
So, maybe we got a poisoned version of gdm from an update??

I'll try reinstalling gdm from the Synaptic Package Manager and see if it cures my system, too.

Eric
I tried reinstalling gdm and 4 other gdm packages using the Synaptic Package Manager.  It didn't work on my system.  

I've also downloaded updates with the Update Manager and that has not helped either.

I just used "sudo thunar" to activate the Thunar File Manager, and was able to view the gdm log files.  
I'm not sure if there are any smoking guns here.  I do see that gdm splash is choosing a 2560x1600 background, and my monitor is only a 1920x1080 LCD.

xsplash-gdm.log
```
[16:24:34:467828962 - MSG] xsplash started
[16:24:34:467829083 - MSG] get_logo_filename(): looking for the best logo for screen width...
[16:24:34:467829098 - MSG]  ** Chose `large'
[16:24:34:467829108 - MSG]  ** logo filename is: /usr/share/images/xsplash/logo_large.png
[16:24:34:467829119 - MSG] get_throbber_filename(): looking for the best throbber for screen width...
[16:24:34:467829131 - MSG]  ** Chose `large'
[16:24:34:467829141 - MSG]  ** throbber filename is: /usr/share/images/xsplash/throbber_large.png
[16:24:34:467829151 - MSG] background_image = /usr/share/images/xsplash/bg_2560x1600.jpg
[16:24:34:467829162 - MSG] logo_image = /usr/share/images/xsplash/logo_large.png
[16:24:34:467829172 - MSG] throbber_image = /usr/share/images/xsplash/throbber_large.png
[16:24:35:466233389 - MSG] get_logo_filename(): user provided a logo on the command line; using that
[16:24:35:466235520 - MSG] get_throbber_filename(): user provided a throbber on the command line; using that
[16:24:35:466250613 - MSG] throbber started (50 frames)
[16:24:35:467008969 - MSG] received signal: gdm
[16:24:35:467009029 - MSG] gdm mode: fading out
[16:24:36:465836962 - MSG] fade finished
[16:24:36:465837129 - MSG] exiting...
```

xsplash-user.log
```
[16:24:42:459696935 - MSG] xsplash started
[16:24:42:459697065 - MSG] get_logo_filename(): looking for the best logo for screen width...
[16:24:42:459697079 - MSG]  ** Chose `large'
[16:24:42:459697090 - MSG]  ** logo filename is: /usr/share/images/xsplash/logo_large.png
[16:24:42:459697101 - MSG] get_throbber_filename(): looking for the best throbber for screen width...
[16:24:42:459697113 - MSG]  ** Chose `large'
[16:24:42:459697123 - MSG]  ** throbber filename is: /usr/share/images/xsplash/throbber_large.png
[16:24:42:459697133 - MSG] background_image = /usr/share/images/xsplash/bg_2560x1600.jpg
[16:24:42:459697143 - MSG] logo_image = /usr/share/images/xsplash/logo_large.png
[16:24:42:459697154 - MSG] throbber_image = /usr/share/images/xsplash/throbber_large.png
[16:24:43:458170119 - MSG] get_logo_filename(): user provided a logo on the command line; using that
[16:24:43:458172271 - MSG] get_throbber_filename(): user provided a throbber on the command line; using that
[16:24:43:458187838 - MSG] throbber started (50 frames)
[16:24:43:458488975 - MSG] received a new signal to wait for: xfdesktop
[16:24:43:458489037 - MSG] adding signal `xfdesktop'
[16:24:43:458968977 - MSG] received signal: xfdesktop
[16:24:43:458969031 - MSG] received signal xfdesktop
[16:24:44:457786963 - MSG] fade finished
[16:24:44:457787212 - MSG] exiting...
```

0.log file
```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux Mythbuntu8 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: root=UUID=cd96068d-ce8c-4263-acd3-30fe2815dc76 ro quiet splash 
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 11 16:24:33 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(--) using VT number 7

(--) PCI:*(0:0:5:0) 10de:0240:1043:81cd nVidia Corporation C51PV [GeForce 6150] rev 162, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6150 (C51) at PCI:0:5:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.51.22.26.07
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6150 at PCI:0:5:0:
(--) NVIDIA(0):     ACER X233H (CRT-0)
(--) NVIDIA(0): ACER X233H (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): No valid modes for "1280x720"; removing.
(WW) NVIDIA(0): No valid modes for "720x480"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0):     "1920x1080"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(**) NVIDIA(0): DPI set to (100, 100); computed from "DPI" X config option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing extension GLX
(II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
(**) ImPS/2 Generic Wheel Mouse: always reports core events
(**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
(II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
(II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
(II) ImPS/2 Generic Wheel Mouse: Found scroll wheel(s)
(II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
(**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
(**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
(**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
(**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
(**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
(**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0
(II) ImPS/2 Generic Wheel Mouse: initialized for relative axes.
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) NVIDIA(0): Setting mode "1920x1080_60_0"
```

0-greeter.log file
```
gnome-session[2446]: WARNING: Could not launch application 'metacity.desktop': Unable to start application: Failed to execute child process "metacity" (No such file or directory)
** (process:2459): DEBUG: Greeter session pid=2459 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-4LKmyj/database
```

0-slave.log file
```
gdm-session-worker[2460]: pam_unix(gdm:session): session opened for user eric by (uid=0)
gdm-session-worker[2460]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
```

Maybe a gdm expert can see something significant here?

Eric

---

### Post by neutron68 on 2009-11-15
Something has changed and I am not getting the forced multiple logins any more!  

I'm not sure if it was due to something I did, or if it was the update via the Ubuntu Update Manager from yesterday afternoon (Nov.14, 2009) that fixed it.

In case it is something I helped facilitate, here is what I did...

Yesterday, I changed my video card from an nvidia 6150 display chip (built-on to the motherboard) to an nvidia 8400GS PCI-Express video card.  I was doing this to try out VDPAU.  Before changing to the 8400GS card, I was able to choose 1920x1080 resolution and xorg-Ubuntu could identify that they were talking to an ACER LCD monitor.  After changing to the 8400GS card, I lost my ability to use select the full resolution (1920x1080) of my Acer 23 inch LCD monitor, and xorg-Ubuntu could not identify what kind of monitor was connected, any more.  I was stuck with resolutions of 1360x768 or less.  During my struggles with that resolution problem, the multiple logins problem stopped.  The procedure below did fix the resolution problem, by the way.

Here's what I did to try and fix the resolution problem:

1.  I copied an old backup of the xorg.config file (contents shown below) to xorg.conf (did a "sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf)
2.  Then I restarted the pc
3.  Then I started the nvidia-settings program (did a "sudo nvidia-settings")
4.  All of a sudden the monitor was communicated with and Ubuntu and xorg knew it was an Acer X233H!?
5.  Then, I tried to change resolutions and this time, the full list of choices was available - including 1920x1080.  I chose 1920x1080 with 60Hz refresh and clicked the APPLY button.
6.  The display changed size to 1920x1080 and worked fine.
7.  I clicked the "Save to X Configuration File" button and it did (new file contents quoted below).
8.  I restarted the computer to be sure the resolution and monitor communication would continue.  Both continued to work at the 1920x1080 resolution.

Did something in that list of steps slap Ubuntu into submission?  Maybe?

The former xorg.conf file was this:
```
Section "Monitor"
	Identifier     "Configured Monitor"
EndSection

Section "Screen"
	Identifier     "Default Screen"
	Device         "Configured Video Device"
	Monitor        "Configured Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth       24
		Modes      "nvidia-auto-select" "1920x1080" "1280x720" "1024x768" "720x480" "800x600" "640x480"
	EndSubSection
EndSection

Section "Module"
	Load           "glx"
EndSection

Section "Device"
	Identifier     "Configured Video Device"
	Option         "DPI" "100x100"
	Option         "UseEvents" "1"
	Option         "AddARGBVisuals" "1"
	Option         "AddARGBGLXVisuals" "1"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection
```

The new xorg.conf file is this:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "DontZap" "False"
    Option         "Xinerama" "0"
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
    ModelName      "ACER X233H"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "DPI" "100x100"
    Option         "UseEvents" "1"
    Option         "AddARGBVisuals" "1"
    Option         "AddARGBGLXVisuals" "1"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select" "1920x1080" "1280x720" "1024x768" "720x480" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1920x1080_60 +0+0; nvidia-auto-select +0+0; 1920x1080 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

You can see that the nvidia-settings program changed and added information to the xorg.conf file.

Feedback from others should help us determine if an Update Manager update fixes the multi-login problem or if changes in the xorg.conf file fixes the multi-login problem.

Eric

---

### Post by deralex on 2009-11-18
Unfortunately updating did not change anything for me. I still have to login multiple times. The last time I logged in yesterday evening it took more than 20! attempts... :(

I also tried changing some settings using the nvidia-settings program. But that didn't help. Some other topic in the german ubuntu forums also indicated that it might have something to do with graphic card drivers / settings. But I did not find a real solution yet. I will try without proprietary drivers to check that.

Any further hints greatly appreciated!

---

### Post by neutron68 on 2009-11-18
Maybe my change from the nvidia 6150 display chip to an nvidia 8400GS display card was the change that made the difference??

My nvidia video driver was version 185 [Recommended] before and after my nvidia card change.

I wonder how many people have the multiple-login problem?  

I don't see much talk about it on these forums, and the developers/experts aren't responding to the questions.

Eric

---

### Post by graza on 2009-11-18
Just upgraded from 9.04 to 9.10 - same problem

It gets boring typing in the same password several times

Not a problem if nothing goes wrong, but this is going to get me into trouble if mythtv crashes while I'm out at work :(

---

### Post by neutron68 on 2009-11-18
> **graza said:**
> Just upgraded from 9.04 to 9.10 - same problem

It gets boring typing in the same password several times

Not a problem if nothing goes wrong, but this is going to get me into trouble if mythtv crashes while I'm out at work :(
Maybe there is a pattern with the video cards?  What display card do you have?  Nvidia?  Which chip?  
If nvidia, are you also using driver version - 185?

Eric

---

### Post by deralex on 2009-11-19
I disabled the nvidia drivers... and had no problems logging in. 
tried version 173 after that, but it caused the same problems. then I switched to 96 which seems to work at the moment.

---

### Post by Varingo on 2009-11-20
> **neutron68 said:**
> Maybe my change from the nvidia 6150 display chip to an nvidia 8400GS display card was the change that made the difference??

My nvidia video driver was version 185 [Recommended] before and after my nvidia card change.

I wonder how many people have the multiple-login problem?  


I have a clean mythbuntu 9.10 install, 8500 GT card, running 190.42, I also get the multiple login problem, I was using the default xorg.conf.  Interestingly this was faulty and would not allow an update.  I have updated it now and will test and report back.

I had changed the screen resolution from the monitor default of 1920x1080 to 1440x900, not sure where this was saved as it wasn't in xorg.conf!

An xorg.conf copy / pasted from a PC of much the same spec was overwritten, and now I can save xorg.conf files using nvidia-settings.  Possibly a faulty default xorg.conf?

---

### Post by Varingo on 2009-11-20
Since changing the xorg.conf (presumably into a valid one?!) I've not had to login at all (That was original setup also) and certainly not three times, that is on power on and reboot.  No updates were available or applied.  

Reboot curiously also starts mythtv whereas power on does not.  (!)

---

### Post by neutron68 on 2009-11-21
> **Varingo said:**
> I have a clean mythbuntu 9.10 install, 8500 GT card, running 190.42, I also get the multiple login problem, I was using the default xorg.conf.  Interestingly this was faulty and would not allow an update.  I have updated it now and will test and report back.

I had changed the screen resolution from the monitor default of 1920x1080 to 1440x900, not sure where this was saved as it wasn't in xorg.conf!

An xorg.conf copy / pasted from a PC of much the same spec was overwritten, and now I can save xorg.conf files using nvidia-settings.  Possibly a faulty default xorg.conf?
There seems to be a pattern that includes the xorg.conf file as part or all of the solution.  It would be interesting to see your before and after versions of the xorg.conf file.  We may see a common change jump out at us!  

It may be that part of the 9.10 upgrade was a change in xorg versions and thus the xorg files need to change to fit the new xorg server??

---

### Post by Varingo on 2009-11-21
> **neutron68 said:**
> It would be interesting to see your before and after versions of the xorg.conf file.  We may see a common change jump out at us!  

Mythbuntu 9.04 default:
> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "UseEvents"    "1"
    Option    "DPI"    "100x100"
    Option    "NoLogo"    "1"
EndSection


Mythbuntu 9.10 default xorg.conf:
> 
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "UseEvents"     "1"
        Option  "DPI"   "100x100"
        Option  "NoLogo"        "1"
EndSection


Working xorg.conf:
> 
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
# Seems important for both screens to function set 0
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
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
    ModelName      "ViewSonic VX2260WM"
    HorizSync       24.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "TV-0"
    HorizSync       24.0 - 82.0
    VertRefresh     50.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
#    Option         "UseEvents" "0"
    Option         "DPI" "100x100"
#??    Option         "NoLogo" "1"
#    Option         "UseEvents" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          0
#    Option         "UseEvents" "0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"
#    Option "metamodes" "CRT: nvidia-auto-select +0+0"
# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0, TV: nvidia-auto-select +1920+0"
# Removed Option "metamodes" "CRT: 1920x1080 +0+0, TV: nvidia-auto-select +1920+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "CRT: 1280x1024 +0+0, TV: nvidia-auto-select +1280+0"
# Removed Option "metamodes" "CRT: 1280x1024 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "NoLogo" "True"
# NOT SURE IF THIS IS REQUIRED AS XINERAMA AND VDPAU NOT COMPATIBLE?
#    Option         "TwinViewXineramaInfoOrder" "CRT-1"
# This did not work!  ?delete+0+0
#    Option         "metamodes" "CRT: 1600x900 +0+0"
    Option         "metamodes" "CRT: 1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
#Apparently Overscan does not work when 1080i selected?
#    Option        "TVOverScan" "0.75"
#    Option        UseEDID" "False"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "TV: 1920x1080"
# Removed Option "metamodes" "TV: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "ConnectedMonitor" "TV"
#    Option         "metamodes" "TV: 1920x1080 +0+0"
#    Option         "TVStandard" "HD1080i"
    Option         "TVStandard" "HD720p"
    Option         "TVOutFormat" "COMPONENT"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TwinView" "0"
    Option         "metamodes" "TV: 1280x720 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection




> **neutron68 said:**
> It may be that part of the 9.10 upgrade was a change in xorg versions and thus the xorg files need to change to fit the new xorg server??

This does seem a possibility!

---

### Post by neutron68 on 2009-11-22
It looks like the pattern of changes I saw in my xorg.conf file is holding true for you, too.  

Specifically, you now have "Device0" rather than "Configured Video Device", and "Screen0", rather than "Default Screen", and "Monitor0", rather than "Configured Monitor".

At this point, I'm not sure if we need to make these changes for the sake of xorg or for the sake of the nvidia driver?

It would be good for xorg and Ubuntu experts to examine and verify what we've found.  The fix seems to lie in these clues!

Eric

---

### Post by Ransak on 2009-11-23
Ran into the same problem with an upgrade from 9.04 to 9.10.

This does not pass the wife test :(

I tried using a previous xorg.conf and then using the nvidia-settings app to save changes. It didn't work for me.

If it matters, I'm using an nVidia GeForce 6200 and an DVI to HDMI cable to drive a Panasonic plasma HDTV.

---

### Post by neutron68 on 2009-11-23
> **Ransak said:**
> Ran into the same problem with an upgrade from 9.04 to 9.10.

This does not pass the wife test :(

I tried using a previous xorg.conf and then using the nvidia-settings app to save changes. It didn't work for me.

If it matters, I'm using an nVidia GeForce 6200 and an DVI to HDMI cable to drive a Panasonic plasma HDTV.
Are you willing to edit your xorg.conf file?  Some command line activity is necessary.  From the feedback we've seen, that seems to be the solution.  

Does my list of xorg.conf file modification steps earlier in this thread make sense to you?  

Before you start, you should make a backup copy of your current xorg.conf file.
From a Terminal window, do a "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup" command.  Then, start playing with adjusting the file using the nvidia-settings program to help you.  In order for the nvidia-settings program to be allowed to edit the xorg.conf file, you have to call it with a sudo command, like I did.

Eric

---

### Post by Raptor Ramjet on 2009-11-25
I've got something like the same issue too.  After upgrading to 9.10 I can't log in via GDM as it just keeps restarting.  However I can log in fine to an alternate terminal by using "Ctrl+Alt+F2" which logs me in just fine.

However the 9.04 to 9.10 "upgrade" has also killed HDMI and as that was a total PITA to get working under 9.04 it's been a deal breaker for me. Ubuntu is now only staying on that box until I get enough free time to put something else on it.

Sadly 9.10 really does seem to have been a poor release.

---

### Post by neutron68 on 2009-11-27
[QUOTE=Raptor Ramjet]I've got something like the same issue too.  After upgrading to 9.10 I can't log in via GDM as it just keeps restarting.  However I can log in fine to an alternate terminal by using "Ctrl+Alt+F2" which logs me in just fine.[/QUOTE]
Sounds familiar - like the multiple-login problem.  It may take 10 to 20 trys before you finally get logged in via the graphic login window!

[QUOTE=Raptor Ramjet]
However the 9.04 to 9.10 "upgrade" has also killed HDMI and as that was a total PITA to get working under 9.04 it's been a deal breaker for me. [/QUOTE]
Have you checked to see if your /etc/X11/xorg.conf file got altered from the previous working version?
It may be that you need to edit/alter the xorg.conf file so it will work in 9.10 as it did in 9.04.

[QUOTE=Raptor Ramjet]Ubuntu is now only staying on that box until I get enough free time to put something else on it.

Sadly 9.10 really does seem to have been a poor release.[/QUOTE]
Yes, I think Ubuntu/Mythbutu 9.10 is the most buggy version I've ever experienced, also.

That said...I'm optimistic that the bugs will get fixed, eventually.

Eric

---

### Post by czarek_t on 2009-12-13
What solved the issue for me was changing the /usr/share/xsessions/xfce.desktop from:

```
...
Exec=startxfce4
...
```into:
```
...
Exec=/usr/bin/startxfce4
TryExec=/usr/bin/startxfce4
...
```

---

### Post by nunrgguy on 2009-12-19
I have this problem but only with the account that myth is installed from and tries to log into on startup. I can log into any other account fine. Any ideas?

Looking into it further I see that the difference in the accounts is that myth front end  is not set to boot in the other accounts. I've removed this from the boot list of the problem account and now it boots into the account automatically. Manually starting the f/e is fine and causes no problems - I wonder what the boot issue is...

---

### Post by polc1410 on 2009-12-20
I'm no expert but I think the Screen section of your xorg.conf file always needs to identify the device it is to use which is achieved by adding:

Device "device name" # where device name is the idetifier in the device section

Seemed to work for me - although I have made other tweaks to my xorg.conf file which may be necessary too..

---

### Post by polc1410 on 2009-12-20
Oh and I also did a kernel update to 2.6.31-16 (was 31-14) perhaps that helped

---

### Post by nunrgguy on 2009-12-20
There's very little at all in the xorg conf file. What I can't figure out is why it logs into two accounts fine but not the other - the mythfrontend thing unfortundately was a fluke, I'm still having the same problem with auto start of the f/e disabled.

---

### Post by Ram-Z on 2009-12-21
I solved this issue by disabling Composite. Either add this to /etc/X11/xorg.conf:
```
Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```or run:
```
sudo nvidia-xconfig --no-composite
```I hope this helps,
cheers

---

### Post by capnjim on 2010-01-01
I have the same problem. I replaced my xorg.conf with my version from 9.04, but has not fixed the problem. Sometimes it auto-boots fine, other times I have to enter a user name and password, usually only once, but sometimes several times. I checked the gdm logs, and on a failed login I get the following:

(II) Jan 02 02:54:20 NVIDIA(0): Setting mode "1360x768_60_1"
(II) Jan 02 02:54:23 NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select+0+0"

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x3b) [0x8133d6b]
1: /usr/bin/X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xb784d400]
3: /usr/bin/X [0x80f99f0]
4: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0xb5a0b0e7]
Saw signal 11.  Server aborting.
(II) Logitech USB Receiver: Close
(II) Genius LM810: Close
(II) Power Button: Close
(II) Power Button: Close
(II) Genius LM810: Close
(II) Macintosh mouse button emulation: Close
(II) iMON PAD IR Mouse (15c2:0038): Close
(II) Logitech USB Receiver: Close
(WW) xf86CloseConsole: VT_WAITACTIVE failed: Interrupted system call
 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 11


Can anyone tell me what this means?

---

### Post by thinkren on 2010-01-04
I don't use Mythbuntu, but I am encountering the same issue on a fresh install of Xubuntu. Based on my experience and the others here, it seems there are a few critical thing we have in common:

*Nvidia video cards
*user-selected screen resolution due to faulty auto-detected settings.
*the presence of an xorg.conf file in liu of auto configuration by X
*XFCE as the desktop environment (both Mythbuntu and Xubuntu uses XFCE)

things that don't seem to matter:

*monitor type/model (I have a ViewSonic CRT)
*upgrade vs. install (I didn't upgrade as some here did)
*OSS vs. proprietary X driver (I haven't used Nvidia's binary drivers)

my xorg.conf file was auto generated with "Xorg -configure". With some tweaks, I was able to eliminate one of the possible culprits (undetected monitor - my ViewSonic PF790 is now being recognized). Some of it contains code that were cited previously as possible solutions (device names/identifiers). Unfortunately it isn't working for me. My Kernel is up to date and so is everything else to the best of my knowledge.  I've also observed that the resolution of the login screen changes randomly from one attempt to the next.  This is being tracked as Bug #463314 on launchpad.net

---

### Post by kubug on 2010-01-22
I had the same issue a while ago, with every Myth Frontend I build. There is something wrong with the automatic NVIDIA driver install in either Xfce or Mythbuntu. 

What I did to fix it was move the old xorg.conf

```
sudo mv /etc/X11/xorg.conf xorg.conf.old
```

And then I let the nvidia driver create a new xorg.conf

```
sudo nvidia-xconfig --no-composite
```

If you want to use compiz, you may want to remove the composite part of that last command. Otherwise it seems to run better without the composite part.

Of course there are other things you can do to optimise it a bit more, like adding the UseEvents flag.

---

### Post by typos1 on 2010-01-24
I ve been having similar probs with login since upgrading to Karmic-didnt have them with Jaunty. I might be lucky and login first time (only happened twice since upgrading!), but usually its 2-20 attempts to login (takes 8 on average). After the ubuntu start screen with the animated line, the screen goes blank, then I get the start screen again (this time at the wrong resolution), then back to login etc etc. Sometimes I might briefly get an nVidia screen momentarily, sometimes the music might start to play, then stop, then back to the start up screen and the animated white line, then back to login etc etc sometimes the cursor might change from an arrow to the whirly circle, briefly, then go back to the start up screen, sometimes I might get a combination of some or all of these things.

I thought it was something to do with Gnome panel as there are as many gnome panel running entries in system monitor as attempts it takes me to login and (even if I successfully logged in on the second attempt) system monitor shows the processor running at 100% and each entry for gnome panel has to be stopped, then processor usage drops to nothing and everything is fine, but there are sporadic gnome panel error messages whenever I m using the pc.

Posted about it before, but no answers:
[http://ubuntuforums.org/showthread.php?t=1386932](http://ubuntuforums.org/showthread.php?t=1386932)

This is just for the record-going to try some of the things suggested in this thread...

---

### Post by MusicMonkey5555 on 2010-02-14
I have the same problem. Upgraded to the latest version and it seems I have to login multiple times. I log in with the correct username and password and it goes black then back to the login screen. It does this several times, one time it stayed black and I had to force restart.

Also it seems that shows haven't been getting recorded, has an error. Or part of a show will be recorded, but not all. Not sure if this is related, but it didn't happen until I upgraded. I really like being able to mark MythVideo's as watched, but these other bugs almost make the upgrade not worth it. I have thought about doing a clean install but there are a couple shows I don't want to loose.

Maybe I will figure out how to make them into a file I can just put in the video folder then try that. Let me know if you figure out how to fix it or anyone else does, I would love to have everything working again, without having to start from scratch, setting up the tv guide stuff and fitting everything to my tv (Menus are cut off) took some time and grabbing all the recorded shows may be a pain as well.

---

### Post by MusicMonkey5555 on 2010-02-14
Hey I just lunched the recover menu (hit Esc when booting and then select recovery) and it did a check disk, I then selected fix broken packages (or something like that) and did an auto-remove because one of the packages didn't need to be there. I rebooted and it looks like it auto logs in now so I don't get the multiple logins. I am not sure if there are any other issues this caused, but I figured it was probably an issue with some bad sectors or something since that tends to cause bootup issues. I was thinking about running spinrite, but I would have to connect the drives to a windows machine or something since there is no linux version.

Anyway hopefully this fixes my issues, I will let you know if I have any more issues. Figured I would let you know incase it helps you as well.

---

### Post by GigiCestone on 2010-04-08
Does anyone know if this issue is solved yet? I have 2 machines running Ubuntu 9.10 with gnome config and they both have this problem. Thank you...

---

### Post by typos1 on 2010-04-08
Still got it on mine, though not as bad as before, not got around to trying solutions on this thread yet. Have you tried any of them? The one above for instance?

---

### Post by GigiCestone on 2010-05-19
Hi Typos,
          I have tried the solutions above, but they did not resolve the issue. I did an upgrade/update to 10.04 Lucid and it seems to have gone away(I hope). I might suggest this for you as well to clear the problem. Good Luck and I hope it works for you...

---

