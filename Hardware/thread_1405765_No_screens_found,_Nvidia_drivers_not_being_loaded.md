---
title: "No screens found, Nvidia drivers not being loaded"
date: 2010-02-13
forum: Hardware
---

### Post by Xog on 2010-02-13
I just tried to install the recommended Nvidia driver.
Nvidia card: GeForce 9800 GTX+
OS: 32-bit Ubuntu 9.10, FRESH install.

Here's the error when I try logging in after restarting the "sudo nvidia-xconfig" and "sudo service gdm restart":

Ubuntu logs me out as expected, then when it tries logging back in, the screen flashes several times. I see a side of my desktop for a split second, and then it all goes black and I'm presented with a box that says:

The following error was encountered. You may need to update your configuration to solve this.

(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your systems's kernel log for additional error messages.
(EE) NVIDIA: Failed to load module "nvidia" (module-specific error, 0)
No drivers available.

Clicked OK.

I'm taken to a screen that presents:
What would you like to do?
- Run ubuntu in low-graphics mode for one session only
- Reconfigure graphics
- Troubleshoot the error
- Exit to console login

When I click "Troubleshoot the error" I'm given:
- Review the xserver log file
- Review the startup errors
- Edit configuration file
- Archive configurations and logs
I chose Archive Configurations and Logs. I have it saved on my computer.

There's several different logs, but here's the one most pertaining:
```


X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux logan-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-20-generic root=UUID=342badfd-40c1-4528-8fd5-f6d76da89ac6 ro quiet splash
Build Date: 14 November 2009  05:48:26PM
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Feb 13 01:57:34 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:3:0:0) 10de:0612:1682:2373 nVidia Corporation G92 [GeForce 9800 GTX] rev 162, Mem @ 0xf8000000/16777216, 0xa0000000/536870912, 0xf6000000/33554432, I/O @ 0x0000df00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

Help?

---

### Post by lukaszr on 2010-02-13
Here is my Xorg.conf file with SLi WORKING!!

[IMG]http://nrzkvg.blu.livefilestore.com/y1pqQzE5Xi-WzqaX07-QW1InJnrec4t2aNV8X_RJ12gtXLSAuX76adWjecW5muHPBd6awIrUNzEStmvqm1btPmRAVrQfv5HlU4X/Screenshot-NVIDIA%20X%20Server%20Settings.png[/IMG]

> 
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Aug 14 18:33:37 PDT 2009

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX/9800 GTX+"
    BusID          "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    Option         "SLI" "auto"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


---

### Post by lukaszr on 2010-02-13
Not sure if you need SLI or if you are trying to configure just one 9800 GTX so here is my xorg.conf file before i enabled SLI. 

> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@crested)  Sun Feb  1 20:25:37 UTC 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Fri Aug 14 18:33:37 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
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
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX/9800 GTX+"
    BusID          "PCI:4:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Xog on 2010-02-13
this is my current Xorg.conf file

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
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

---

### Post by Xog on 2010-02-13
I think the important part here in my log file is this:

(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

Fatal server error:
no screens found (which is why I have a blank screen)

---

### Post by lukaszr on 2010-02-13
> **Xog said:**
> this is my current Xorg.conf file

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Fri Aug 14 17:54:58 PDT 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
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
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
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

Ok in terminal run this command

"lspci | grep vga"

Mine shows
03:00.0
04:00.0

Then you want to add the line 

BusID          "PCI:4:0:0" under Device > Vendor Name

so should look like this for you...

> Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX/9800 GTX+"
    **BusID          "PCI:4:0:0"**
EndSection

---

### Post by Xog on 2010-02-13
logan@logan-desktop:~$ lspci | grep vga
logan@logan-desktop:~$

edit:
By the way, I followed instructions from someone else's thread [http://ubuntuforums.org/showthread.php?t=213409&page=3](http://ubuntuforums.org/showthread.php?t=213409&page=3) and entered recovery mode. I did 

dpkg-reconfigure xserver-xorg
and then
reboot

then my PC couldn't even find my hard drives. I popped in my LiveCD and it saw NO HARD DRIVES AT ALL. So I shut down, took out the CD, and waited 20 seconds..

Powered on.. everything seems to be OK for now (concerning the hard drives)..

still having the video problems. But this time I went on to one of the kernels that I said was broken and just leaving me at a black screen, popped up the error message again and now I can login using "minimal video settings" again. I swear to god I would have strangled somebody if my hard drives were completely wiped because of ubuntu. I don't know what kind of freak accident happened there.

---

### Post by lukaszr on 2010-02-13
> **Xog said:**
> logan@logan-desktop:~$ lspci | grep vga
logan@logan-desktop:~$

edit:
By the way, I followed instructions from someone else's thread [http://ubuntuforums.org/showthread.php?t=213409&page=3](http://ubuntuforums.org/showthread.php?t=213409&page=3) and entered recovery mode. I did 

dpkg-reconfigure xserver-xorg
and then
reboot

then my PC couldn't even find my hard drives. I popped in my LiveCD and it saw NO HARD DRIVES AT ALL. So I shut down, took out the CD, and waited 20 seconds..

Powered on.. everything seems to be OK for now (concerning the hard drives)..

still having the video problems. But this time I went on to one of the kernels that I said was broken and just leaving me at a black screen, popped up the error message again and now I can login using "minimal video settings" again. I swear to god I would have strangled somebody if my hard drives were completely wiped because of ubuntu. I don't know what kind of freak accident happened there.

if you get no output of the command "lspci | grep VGA" then that means ubuntu isn't recognising your video cards. What OS were you using before Ubuntu? 

I know this may sound stupid, but i would make sure your video card is installed correctly...and make sure you connected the powersupply pci-e cables to the card, should be 2 of them. 


By the way, did you try the xorg.conf file configuration i suggested?

---

### Post by Xog on 2010-02-13
Would you like me to just copy over your xorg.conf into mine, replacing it? (creating a backup first, ofcourse?)

---

### Post by Xog on 2010-02-13
interesting little thing here.

just a regular lspci displays:

..cut..
03:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX] (rev a2)
..cut..

---

### Post by Xog on 2010-02-13
I tried your xorg.conf file and it didn't work. Same problem.

I was able to catch another part though that I forgot to add, when I do ```
sudo service gdm restart
``` I'm presented with the following after the X server reboots:

usplash: Setting mode 1152 x 864 failed
usplash: Using mode 1024 x 768

then I'm given the command line to login. It's just all terminal from there. No ubuntu desktop. So I reboot and sure enough I come up with the error message again, so I choose Login to ubuntu using minimal settings...

---

### Post by Xog on 2010-02-13
neither of us caught this.

logan@logan-desktop:~$ lspci | grep VGA
03:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GTX] (rev a2)
logan@logan-desktop:~$ 

Had to use CAPS for vga. Sometimes it slips my mind that commands are case sensitive.

---

### Post by lukaszr on 2010-02-13
Did you manage to get it working?

---

### Post by Xog on 2010-02-13
Nope. :(

edit: Just woke up. Gonna try doing this

dpkg-reconfigure nvidia-185-kernel-source

brb

---

### Post by Xog on 2010-02-13
```

logan@logan-desktop:~$ dpkg-reconfigure nvidia-185-kernel-source
/usr/sbin/dpkg-reconfigure must be run as root
logan@logan-desktop:~$ sudo dpkg-reconfigure nvidia-185-kernel-source
[sudo] password for logan: 
Removing all DKMS Modules
Done.
Loading new nvidia-185.18.36 DKMS files...
Building for architecture i686
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
logan@logan-desktop:~$ 

```

sigh.

---

### Post by Xog on 2010-02-13
I think I may have found the problem.

[http://typethinker.blogspot.com/2010/02/ubuntu-fails-to-load-nvidia-kernel.html](http://typethinker.blogspot.com/2010/02/ubuntu-fails-to-load-nvidia-kernel.html)

> As much a note to myself, as a warning to others…

After a kernel upgrade, my Ubuntu Karmic started the X server in low-resolution mode. My Xorg.0.log said:

(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Video Driver
(EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
(EE) NVIDIA:     system's kernel log for additional error messages.
(II) UnloadModule: "nvidia"
(II) Unloading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(EE) Failed to load module "nvidia" (module-specific error, 0)
(EE) No drivers available.

I tried modprobe nvidia and such, but it seemed that the module actually did not exist. This module should be installed by the package nvidia-185-kernel-source, which was present on my system. However, it turns out that the kernel module is compiled on-the-fly by a program called jockey which controls DKMS, the Dynamic Kernel Module Support.

It is possible to force a recompile using dpkg-reconfigure:

$ sudo dpkg-reconfigure nvidia-185-kernel-source
Removing all DKMS Modules
Done.
Loading new nvidia-185.18.36 DKMS files...
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

I need the kernel source, eh? Why the hell is that not a dependency, if the driver package is useless without it? Anyway, let's install the kernel source then:

$ uname -r
2.6.31-19-generic
$ sudo apt-get install linux-source-2.6.31

Installs fine, but makes no difference. Turns out that dpkg-reconfigure was lying: I just need the headers. Here we go:

$ sudo apt-get install linux-headers-2.6.31-19-generic
...
$ sudo dpkg-reconfigure nvidia-185-kernel-source
Removing all DKMS Modules
Done.
Loading new nvidia-185.18.36 DKMS files...
Building for architecture x86_64
Building initial module for 2.6.31-19-generic
Done.

nvidia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.31-19-generic/updates/dkms/

depmod......

DKMS: install Completed.
$ modprobe nvidia
$

That's better.

Several bug reports indicate similar problems, but the current way this is handled is terribly inadequate. The driver package should pull in the kernel headers if it needs them. There was no warning about this when the kernel was upgraded. There was no warning when the module failed to compile on boot. A fix for a problem with the same symptoms was released back in December; another one is in the upcoming Lucid release.

Oh yeah, I ended up rebooting my system. Whatever happened to Ctrl+Alt+Backspace? 

Hah! Now, if only I can find away to bring up that error message again. I can only boot into windows :(

---

### Post by Xog on 2010-02-13
Anyone know how I can force a boot into low-graphics mode from root shell?

---

