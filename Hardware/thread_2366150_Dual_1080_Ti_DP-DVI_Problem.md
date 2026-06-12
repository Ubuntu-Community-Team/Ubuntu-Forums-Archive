---
title: "Dual 1080 Ti DP-DVI Problem"
date: 2017-07-14
forum: Hardware
---

### Post by haldero on 2017-07-14
Hello, I have upradet my machine (ubuntu 16.04) to two 1080 Ti graphics cards, installed the repository driver from the ppa (384.47) and now have problems to detect my screens.

If i connect the "main screen", a Samsung S24C450, using a DVI-cable on any of the 3 DP using the provided DP-DVI adapter from the GPU Box does not boot.
If i connect it using VGA-HDMI adapter on the HDMI slot of the GPU he boots and i can use everything as usual. But i wanted to use the HDMI for my HDMI capable screen. I tried to configure the Graphics card using the HDMI screen, but when i connect the DVI-DP Adapter *xrandr* gives:

```
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080     60.00*+
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)

```
*nvidia-settings* does not recognize the screen, also the ubuntu built in displays option fails to recognize the screen (I tried all three DP-outlets on the GPU)

*nvidia-smi* recognizes both graphics cards:
```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 384.47                 Driver Version: 384.47                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 108...  Off  | 0000:01:00.0      On |                  N/A |
| 38%   64C    P2    68W / 250W |    665MiB / 11171MiB |      5%      Default |
+-------------------------------+----------------------+----------------------+
|   1  GeForce GTX 108...  Off  | 0000:05:00.0     Off |                  N/A |
| 34%   58C    P2    67W / 250W |    350MiB / 11172MiB |      8%      Default |
+-------------------------------+----------------------+----------------------+
```

 I could try to use the second Card's HDMI to connect my second screen and not use DP, but then why does the card have DP? Any suggestions or things i'm missing?

Thanks for your help!

---

### Post by Autodave on 2017-07-14
First off, try to never use any drivers not obtained from the repositories. I would uninstall the one from Nvidia and then go to SETTINGS -> ADDITIONAL DRIVERS and install it from there.

---

### Post by haldero on 2017-07-17
I switched to repository drivers, still the displays are not detected by nvidia-settings.

---

### Post by #&amp;thj^% on 2017-07-17
Autodave gives good advice; the downloaded drivers from nvidia site will cause you more work and grief.
There are ways to get help here when using the suggested drivers, most folks here will ignore if using the drivers downloaded from Nvidia.com. No offense meant.
Maybe you can also help in finding bugs to help make Ubuntu (Drivers) better.
```
apt policy nvidia-384
nvidia-384:
  Installed: 384.47-0ubuntu0~gpu16.04.3
  Candidate: 384.47-0ubuntu0~gpu16.04.3
  Version table:
 *** 384.47-0ubuntu0~gpu16.04.3 500
        500 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by haldero on 2017-07-17
Just edited the post above, i installed repository nvidida-384. Still no changes. Can i provide more helpful information for you?

---

### Post by #&amp;thj^% on 2017-07-17
Well lets look at few things here post back the output of this from the terminal.
Run the Below One line at a time hit enter after each.
```
cd /etc/X11/
ls
```
Lets look at this one also.
```
gedit /etc/default/grub
```
I have a few appointments today I need to tend to so I might not be around much today, but I won't leave you hanging.

---

### Post by haldero on 2017-07-17
> **1fallen said:**
> Well lets look at few things here post back the output of this from the terminal.
Run the Below One line at a time hit enter after each.
```
cd /etc/X11/
ls
```

This returns:
```
app-defaults             xkb                                Xresources
cursors                  xorg.conf                          Xsession
default-display-manager  xorg.conf.backup                   Xsession.d
fonts                    xorg.conf.nvidia-xconfig-original  Xsession.options
rgb.txt                  Xreset                             xsm
xinit                    Xreset.d                           Xwrapper.config

```
I guess X-server is properly configured. Just to eliminate any confusion: The login-loop is solved, this is only about detecting the DP again.
> **1fallen said:**
> 
Lets look at this one also.
```
gedit /etc/default/grub
```
I have a few appointments today I need to tend to so I might not be around much today, but I won't leave you hanging.
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by #&amp;thj^% on 2017-07-17
Well I suspect that it will reappear (Login Loop) sometime in the near future.
There are multiple configs in there that may or may not need some editing and/or removing.
And if that dose happen again, when it dose try adding **"nomodeset"** at grub by hitting "e" when grub is first shown, (This has to be done quickly to stop grub from auto booting) 
And at the line that reads "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash""
To read like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```

I'm going to have to leave you now for my appointments, but we will pick this back up when I return.

---

### Post by haldero on 2017-07-17
I changed GRUB to nomodeset, did update-grub and restarted, no change, still only HDMI->VGA display detected

---

### Post by #&amp;thj^% on 2017-07-17
> **haldero said:**
> I changed GRUB to nomodeset, did update-grub and restarted, no change, still only HDMI->VGA display detected

That was never meant to fix that, only suggested for your login loop.;)
Now we need to have a look at these 3 files:
```
gedit /etc/X11/xorg.conf 
```
and
```
gedit /etc/X11/xorg.conf.backup
```
also
```
gedit /etc/X11/xorg.conf.nvidia-xconfig-original
```
Paste back please using code tags separately.

---

### Post by haldero on 2017-07-18
corg.conf
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 384.47  (buildd@lcy01-23)  Thu Jun 29 22:36:13 UTC 2017

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 384.47  (buildmeister@swio-display-x86-rhel47-02)  Sun Jun 25 01:41:39 PDT 2017

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    ModelName      "Samsung S24C450"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 1080 Ti"
    BusID          "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "1280x1024 +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

xorg.conf.backup
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 384.47  (buildmeister@swio-display-x86-rhel47-02)  Sun Jun 25 01:41:39 PDT 2017


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

```

xorg.conf.nvidia-xconfig-original is empty! (file exists, but 0 characters length, with both vim and gedit.

---

### Post by #&amp;thj^% on 2017-07-19
Sorry for the delay...could not have been helped.
Lets edit your xorg.conf>> Imporant yours<< in post#11 reads_ type o_** "corg.conf"** to read like this:
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 384.47  (buildd@lcy01-23)  Thu Jun 29 22:36:13 UTC 2017

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 384.47  (buildmeister@swio-display-x86-rhel47-02)  Sun Jun 25 01:41:39 PDT 2017

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    ModelName      "Samsung S24C450"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 1080 Ti"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
And we need to rid of the other .conf files, so there is no confusion.
```
sudo rm -rf /etc/X11/xorg.conf.nvidia-xconfig-original
sudo rm -rf /etc/X11/xorg.conf.backup 
```
Now we need to re-edit your default grub file to read like this.
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nogpumanager"

```
If it were me I would use nano for this purpose via:
```
sudo nano /etc/default/grub
```
make the changes++save++close.
If you are not comfortable using nano you can also use gedit to make the above changes via:
```
gksu gedit /etc/default/grub
```
Save and close here also.
Now we update-grub via:
```
sudo update-grub
```
Now I find it best for the first time making changes with X11 that you power down your system waiting 30 to 40 seconds so the hard drive has a chance to spin down rather than a reboot.

---

