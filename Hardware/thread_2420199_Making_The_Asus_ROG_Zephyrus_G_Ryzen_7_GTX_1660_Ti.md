---
title: "Making The Asus ROG Zephyrus G Ryzen 7 GTX 1660 Ti Usuable"
date: 2019-06-01
forum: Hardware
---

### Post by andrewfer000 on 2019-06-01
[FONT=arial][SIZE=2][B][SIZE=5]NEW AND IMPROVED POST. USE THIS INSTEAD.
[https://ubuntuforums.org/showthread.php?t=2440670](https://ubuntuforums.org/showthread.php?t=2440670)[/SIZE][/B]

I have recently purchased a Asus Zephyrus-G-GU502DU-GA502DU and I like it a lot

[/SIZE][SIZE=1][SIZE=2]**Pros-**
Ubuntu works with some workarounds
Battery life is great
GPU is great
System is quiet-*ish *when gaming
Screen is top of the line
[B]
Cons-[/B]
Keyboard back light does not work on any GNU/Linux and if it is enabled on windows the sound will have issues on all GNU/Linux platforms
Keyboard special functions like back light controls and manual fan controls don't work
System can go into sleep mode but cannot resume :(
The system can get very hot
It has no webcam (but does any real GNU/Linux user care about that?!)[/SIZE]

[/SIZE][SIZE=3]
Out of the box, The system has only one major issue and that is the Realtek WiFi Driver. Follow this post here for fix - [https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04](https://askubuntu.com/questions/1071299/how-to-install-wi-fi-driver-for-realtek-rtl8821ce-on-ubuntu-18-04) But here is the Answer anyway
[/SIZE]```
[SIZE=3]sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)[/SIZE]
[SIZE=3]git clone https://github.com/tomaspinho/rtl8821ce[/SIZE]
[SIZE=3]cd rtl8821ce[/SIZE]
[SIZE=3]chmod +x dkms-install.sh[/SIZE]
[SIZE=3]chmod +x dkms-remove.sh[/SIZE]
[SIZE=3]sudo ./dkms-install.sh[/SIZE]

```[SIZE=3]
[/SIZE]
[SIZE=3]For the Kernel config. I suggest putting the following in the **/etc/default/grub **after the word *splash*
```
 nouveau.modeset=0 tpm_tis.interrupts=0 acpi_osi=Linux i915.preliminary_hw_support=1 idle=nomwait 
``` 
[SIZE=4]
**You will need to install the Nvidia GPU driver **the instructions change sometimes so I suggest doing a search on it. But its mostly just adding the graphics PPA and installing nvidia-utils-440 Once you follow the instructions and the driver as well as the xserver settings is installed go on to the next step.

Nvidia wont be the default video driver when OS is first installed. paste this in **/etc/X11/xorg.conf **This is not a PRIME config and your GPU will always use NVIDIA. This will also allow you to use the DP on the USB-C port. I would suggest having an adapter for USB-C to HDMI so you can set up other DEs such as KDE since the laptop screen wont work by default! (it will after display setup through KDE's settings) [/SIZE]

OLD
[/SIZE]```
[SIZE=3]Section "Module"[/SIZE]
[SIZE=3]    Load "modesetting"[/SIZE]
[SIZE=3]EndSection[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]Section "Device"[/SIZE]
[SIZE=3]    Identifier "nvidia"[/SIZE]
[SIZE=3]    Driver "nvidia"[/SIZE]
[SIZE=3]    BusID "1:0:0"[/SIZE]
[SIZE=3]    Option "AllowEmptyInitialConfiguration"[/SIZE]
[SIZE=3]    Option "ModeValidation" "NoDFPNativeResolutionCheck"[/SIZE]
[SIZE=3]    Option "ConnectedMonitor" "DFP-0"[/SIZE]
[SIZE=3]EndSection[/SIZE][SIZE=3]
[/SIZE]
```[SIZE=4]

Look here for alt config for Nvidia Prime use. I heard this disables the USB-C display port function so look out!
[https://devtalk.nvidia.com/default/topic/1067083/linux/nvidia-xconfig-doesnt-do-what-i-want-it-to-nor-does-nvidia-settings/post/5404726/#5404726](https://devtalk.nvidia.com/default/topic/1067083/linux/nvidia-xconfig-doesnt-do-what-i-want-it-to-nor-does-nvidia-settings/post/5404726/#5404726)
[SIZE=2]
At the moment I am happy but I hope this posts gets to all people who want to use Linux on a Asus AMD gaming laptop. I am also hoping AMD and Nvidia continue to work on their open source (and maybe proprietary) drivers to grow support on the GNU/Linux Platform. The keyboard lighting thing may be hard to fix but the sleep and resume feature is most likely due to the AMD CPU and should be fixed in a (not so future) kernel update

  If anyone has a NEW answer to fix the sleep issue and/or keyboard lighting issue please leave it in the comments with newbie like explanations and commands. (I want this to be accessible to everyone)

[SIZE=3]WARNING: Do not update to BIOS 208! Your CPU will slow down after 15 minutes due to fan control issues in Linux. Stay on or downgrade to 207! (I had 208 and downgraded to 207, It should be safe. 206 is a mess, don't downgrade that far!) Try to stick with Kernel 5.0 and Ubuntu 19.04. Sleep mode and power on seem to have issues and or very slow on newer kernels.

This laptop is still not the best for Linux but damn its gotten much better! I am hoping for more improvements in 2020 especially since AMD/NVIDIA hybrids are becoming more popular. Thank you all for the comments and I hope that we can continue making this laptop awesome.   
[/SIZE]
[/SIZE][/SIZE]
[/FONT]

---

### Post by test9900 on 2019-08-03
Hi:

As you suggested, I look for a way to install the nvidia drivers on the laptop, the first step was to run the following command:
ubuntu-drivers devices

in order to get device id. But in my device the command does not show any information at all.

Do you suggest to just run the following command:


sudo apt install nvidia-driver-418

---

### Post by test9900 on 2019-08-03
update: 
installed the nvidia-driver-418, and the same seems to be installed fine, but nvidia-detector, still shows none as an output.
Also the system is barely getting 2.30 hours of battery life. Any clues.. I am currently running ubuntu 19.04, kernel 5.0.0-23-generic. 

Next step, trying to update the kernel to see if this solves anything or the machine explodes :)

---

### Post by test9900 on 2019-08-03
update: 
installed the nvidia-driver-418, and the same seems to be installed fine, but nvidia-detector, still shows none as an output.
Also the system is barely getting 2.30 hours of battery life. Any clues.. I am currently running ubuntu 19.04, kernel 5.0.0-23-generic. 

Next step, trying to update the kernel to see if this solves anything or the machine explodes :)

---

### Post by andrewfer000 on 2019-08-05
[SIZE=1]Reply to test9900: Sorry IDK what to do about the nvidia issues. When i run Nvidia Detector it shows nothing. But if you run *glxinfo |grep "OpenGL"* it should show up. You CAN add Coolbit serrings in the xorg.conf to change fan and clock speeds. I have never tried it personally though :) arch wiki has good info on it but be careful and make backups!

[/SIZE][FONT=arial]**UPDATE: **[/FONT][SIZE=1][FONT=arial]Sleep now works! All you need to do is a BIOS update. downlad it from asus's support page and put it on a flash drive then use EZ Fash to put it into your BIOS. It works great and even comes with a cool power-on sound. Now all that's left is keyboard shortcuts + backlight! [/FONT]**[FONT=arial black][/FONT]**[/SIZE]

---

### Post by nkhthe2nd on 2019-09-28
I have the asus zephyrus ga502du-br7n6. It has the ryzen 7 with both amd and nvidia gpus.

One workaround to the keyboard backlight issue is to first boot into windows, leave the keyboard light on, the do a soft restart into ubuntu. The backlight stays on every time. If I shut down the laptop and then boot straight into Ubuntu, no backlight.

After doing some research on the issue, I believe the issue is a missing file called kbd_backlight. I am currently searching for a way to manually inject it, but I'm not a power user.

---

### Post by computerhavoc on 2019-09-28
[SIZE=3][FONT=arial][COLOR=#000000][SIZE=3]Kinda new to the hole forum stuff. Linux user for 9 years.
I also have the asus zephyrus ga502du-br7n6 and the keyboard backlight is really being a problem. I have read over 20 different asus keyboard backlight forums and all where a bust. As far as I can figure out everything relies on [/SIZE][/COLOR][/FONT][SIZE=3][FONT=monospace][COLOR=#000000][FONT=comic sans ms]asus::kbd_backlight.[/FONT] [FONT=arial]So[/FONT][/COLOR][/FONT][COLOR=#000000] lets try to summarize what I've done.[/COLOR]

[/SIZE][FONT=arial][COLOR=#000000][SIZE=3]asus zephyrus ga502du-br7n6[/SIZE]
[/COLOR][/FONT][COLOR=#000000][FONT=arial]uefi ver. 208[/FONT]
[FONT=arial]originally tried everything on pop os 19.04 kernel ver. 5.0-29something [/FONT]
[FONT=arial]currently: kubuntu 19.10 kernel ver. 5.3.0.12 as of writing this[/FONT]

[/COLOR][FONT=arial]I added the grub options [/FONT][/SIZE][COLOR=#000000][FONT=&amp] [SIZE=3][FONT=comic sans ms]nouveau.modeset=0 tpm_tis.interrupts=0 acpi_osi=Linux i915.preliminary_hw_support=1 idle=nomwait [/FONT][/SIZE][/FONT][/COLOR][SIZE=3]and did the wifi successfully, but[/SIZE]
[SIZE=3][FONT=monospace][FONT=arial]my display name is eDP-1 and I had to create the /etc/X11/xorg.conf[/FONT]

[/FONT][/SIZE][FONT=comic sans ms][SIZE=3]Section "Module"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Load "modesetting"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]EndSection[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]Section "Device"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Identifier "nvidia"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Driver "nvidia"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    BusID "1:0:0"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option "AllowEmptyInitialConfiguration"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option "ModeValidation" "NoDFPNativeResolutionCheck"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option "ConnectedMonitor" "eDP-1"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]EndSection[/SIZE][/FONT]
[SIZE=3]
**[FONT=arial]Then I [/FONT]**[/SIZE][SIZE=3]**[FONT=arial]ran[/FONT] **[FONT=comic sans ms]$ sudo nvidia-xconfig [/FONT]
[FONT=arial]and the end result of xorg.conf looks like this :
[/FONT]
[/SIZE][FONT=comic sans ms][SIZE=3]# nvidia-xconfig: X configuration file generated by nvidia-xconfig[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]# nvidia-xconfig:  version 435.21[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]Section "ServerLayout"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Identifier     "Default Layout"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Screen         "Default Screen" 0 0[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    InputDevice    "Keyboard0" "CoreKeyboard"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    InputDevice    "Mouse0" "CorePointer"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]EndSection[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]Section "Module"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Load           "modesetting"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Load           "glx"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]EndSection[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]Section "InputDevice"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    # generated from default[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Identifier     "Keyboard0"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Driver         "kbd"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]EndSection[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]Section "InputDevice"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    # generated from default[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Identifier     "Mouse0"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Driver         "mouse"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option         "Protocol" "auto"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option         "Device" "/dev/psaux"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option         "Emulate3Buttons" "no"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option         "ZAxisMapping" "4 5"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]EndSection[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]Section "Monitor"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Identifier     "Monitor0"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    VendorName     "Unknown"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    ModelName      "Unknown"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option         "DPMS"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]EndSection[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]Section "Device"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Identifier     "nvidia"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Driver         "nvidia"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]EndSection[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]
[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]Section "Screen"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Identifier     "Default Screen"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Device         "nvidia"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Monitor        "Monitor0"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    DefaultDepth    24[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option         "AllowEmptyInitialConfiguration"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option         "ModeValidation" "NoDFPNativeResolutionCheck"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    Option         "ConnectedMonitor" "eDP-1"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    SubSection     "Display"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]        Depth       24[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]        Modes      "nvidia-auto-select"[/SIZE][/FONT]
[FONT=comic sans ms][SIZE=3]    EndSubSection[/SIZE][/FONT]
[SIZE=3][FONT=comic sans ms]
[/FONT]
[FONT=arial]Ok so that seems better but don't try to play a 1080p 60fps youtube video in firefox or chrome It drops a heavy amount of frames, also I get a 
[/FONT][/SIZE][SIZE=3][FONT=comic sans ms]Desktop effects were restarted due to a graphics reset [/FONT][FONT=arial] notification when the laptop is coming out of sleep[/FONT]


[FONT=arial]Ok so now let's just continue onto the keyboard.

[FONT=comic sans ms]$ xev[/FONT] does not detect the fn keys for keyboard backlight or display brightness. [/FONT]

[FONT=comic sans ms][COLOR=#000000]$ sudo /etc/acpi/asus-keyboard-backlight.sh.[FONT=arial].........yup didn't work, no output in the terminal either.[/FONT][/COLOR]

[COLOR=#000000]$ sudo echo 3 > /sys/class/leds/asus::kbd_backlight/brightness[/COLOR]
bash: /sys/class/leds/asus::kbd_backlight/brightness: No such file or directory

[/FONT][/SIZE]
[SIZE=3][FONT=comic sans ms][COLOR=#000000]$ ls /sys/devices/platform/asus-nb-wmi/leds/[/COLOR]
[B]asus::lightbar

[/B][/FONT][FONT=monospace][FONT=comic sans ms][COLOR=#000000]$ ls /sys/class/leds/            [/COLOR]
**asus::lightbar**           **input26::kana**        **input4::numlock**     **input8::kana**        **input9::compose**
**asus-wireless::airplane**  **input26::numlock**     **input4::scrolllock**  **input8::numlock**     **input9::kana**
**input26::capslock**        **input26::scrolllock**  **input8::capslock**    **input8::scrolllock**  **input9::numlock**
**input26::compose**         **input4::capslock**     **input8::compose**     **input9::capslock**    **input9::scrolllock**
[/FONT]

[/FONT][FONT=comic sans ms][FONT=arial]asus::lightbar has a trigger file, [/FONT][/FONT][/SIZE][FONT=arial]here's[/FONT][SIZE=3][FONT=comic sans ms][FONT=arial] what that shows:[/FONT]

[none] usb-gadget usb-host rfkill-any rfkill-none kbd-scrolllock kbd-numlock kbd-capslock kbd-kanalock kbd-shiftlock kbd-altgrlock kbd-ctrllock kbd-altlock kbd-shiftllock kbd-shiftrlock kbd-ctrlllock kbd-ctrlrlock AC0-online BAT0-charging-or-full BAT0-charging BAT0-full BAT0-charging-blink-full-solid disk-activity disk-read disk-write ide-disk mtd nand-disk cpu cpu0 cpu1 cpu2 cpu3 cpu4 cpu5 cpu6 cpu7 cpu8 cpu9 cpu10 cpu11 cpu12 cpu13 cpu14 cpu15 panic bluetooth-power hci0-power rfkill0 rfkill1 audio-mute audio-micmute r8169-400:00:link r8169-400:00:1Gbps r8169-400:00:100Mbps r8169-400:00:10Mbps hid-34:88:5d:3e:8b:57-battery-charging-or-full hid-34:88:5d:3e:8b:57-battery-charging hid-34:88:5d:3e:8b:57-battery-full hid-34:88:5d:3e:8b:57-battery-charging-blink-full-solid [/FONT]

[FONT=arial]I also tried github project Hummer12007/brightnessctl. It did not display anything for the keyboard either[/FONT]

[FONT=arial]Yup I'm lost, I would really like to see my keyboard[/FONT][/SIZE][SIZE=3][FONT=arial], I'm possibly thinking something is needed in grub or xorg.[/FONT]
[FONT=arial]Any help is appreciated.[/FONT]

[/SIZE]

---

### Post by javiercano on 2019-12-24
Hello!
I've got exactly the same computer but I can not get it... I've done the changes in the xorg.conf file and the X freezes...
I change the grup parameters also...

I send you some information just in case someone could help me... 
I am using the latest snap of Ubuntu 20.04, using 440.44 driver. The driver looks perfectly installed. The problem is the system is not  using it. It is using the AMD integrated graphics card (AMD® Ryzen 7  3750h with radeon vega mobile). And [B]nvidia-settings answers the same problem you described (an empty window).

[/B]```
$ inxi -Gx
Graphics:  Device-1: NVIDIA TU116M [GeForce GTX 1660 Ti Mobile] vendor: ASUSTeK driver: nvidia 
           v: 440.44 bus ID: 01:00.0 
           Device-2: AMD Picasso vendor: ASUSTeK driver: amdgpu v: kernel bus ID: 05:00.0 
           Display: x11 server: X.Org 1.20.5 driver: amdgpu,ati 
           unloaded: fbdev,modesetting,nouveau,nvidia,vesa tty: N/A 
           OpenGL: renderer: AMD RAVEN (DRM 3.33.0 5.3.0-24-generic LLVM 9.0.0) 
           v: 4.5 Mesa 19.2.4 direct render: Yes 

```

```
$ glxinfo | egrep "OpenGL vendor|OpenGL renderer"
OpenGL vendor string: X.Org
OpenGL renderer string: AMD RAVEN (DRM 3.33.0, 5.3.0-24-generic, LLVM 9.0.0)

```

```
$ sudo nvidia-smi 
[sudo] contraseña para javier: 
Tue Dec 24 11:51:15 2019       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 440.44       Driver Version: 440.44       CUDA Version: 10.2     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 166...  Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   51C    P0    15W /  N/A |      0MiB /  5944MiB |      0%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+

```

It looks to be selected but the system does not use it:
```
[I]$ sudo prime-select query
nvidia[/I]
```

```
[I]$ sudo lshw -C display
  *-display                 
       descripción: VGA compatible controller
       producto: TU116M [GeForce GTX 1660 Ti Mobile]
       fabricante: NVIDIA Corporation
       id físico: 0
       información del bus: pci@0000:01:00.0
       versión: a1
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress vga_controller bus_master cap_list rom
       configuración: driver=nvidia latency=0
       recursos: irq:73 memoria:f6000000-f6ffffff  memoria:c0000000-cfffffff memoria:d0000000-d1ffffff  ioport:f000(size=128) memoria:f7000000-f707ffff
  *-display
       descripción: VGA compatible controller
       producto: Picasso
       fabricante: Advanced Micro Devices, Inc. [AMD/ATI]
       id físico: 0
       información del bus: pci@0000:05:00.0
       versión: c1
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm pciexpress msi msix vga_controller bus_master cap_list
       configuración: driver=amdgpu latency=0
       recursos: irq:72 memoria:e0000000-efffffff memoria:f0000000-f01fffff ioport:c000(size=256) memoria:f7600000-f767ffff[/I] 
```

```
[I]$ dmesg|grep nvidia
[    0.429930] nvidia-gpu 0000:01:00.3: enabling device (0000 -> 0002)
[    1.577924] nvidia: loading out-of-tree module taints kernel.
[    1.577931] nvidia: module license 'NVIDIA' taints kernel.
[    1.626905] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    1.636119] nvidia-nvlink: Nvlink Core is being initialized, major device number 236
[    1.636552] nvidia 0000:01:00.0: enabling device (0000 -> 0003)
[    1.636656] nvidia 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=none
[    1.688843] audit: type=1400 audit(1577154230.838:3):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="nvidia_modprobe" pid=617 comm="apparmor_parser"
[    1.689201] audit: type=1400 audit(1577154230.838:4):  apparmor="STATUS" operation="profile_load" profile="unconfined"  name="nvidia_modprobe//kmod" pid=617 comm="apparmor_parser"
[    1.804534] nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver  for UNIX platforms  440.44  Sun Dec  8 03:29:48 UTC 2019
[    1.936386] [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver
[    1.936388] [drm] Initialized nvidia-drm 0.0.0 20160202 for 0000:01:00.0 on minor 1
[    2.086768] nvidia-uvm: Loaded the UVM driver, major device number 234.
[  118.288044] nvidia-gpu 0000:01:00.3: i2c timeout error f0000100[/I]
```

**I can not access to nvidia-settings:**
```
[I]$ sudo nvidia-settings 

ERROR: Unable to load info from any available system


(nvidia-settings:9370): GLib-GObject-CRITICAL **: 01:55:15.799: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 01:55:15.804: PRIME: No offloading required. Abort
** Message: 01:55:15.804: PRIME: is it supported? n[/I]
```

Any advice? Thank you very much on advance!

---

### Post by javiercano on 2019-12-24
I found a solution here (thanks to generix!):
[https://devtalk.nvidia.com/default/topic/1067083/linux/nvidia-xconfig-doesnt-do-what-i-want-it-to-nor-does-nvidia-settings/post/5404726/#5404726](https://devtalk.nvidia.com/default/topic/1067083/linux/nvidia-xconfig-doesnt-do-what-i-want-it-to-nor-does-nvidia-settings/post/5404726/#5404726)

---

### Post by victor7095 on 2020-02-22
Hi, I followed your instructions, and I can see nvidia-settings window. But since I installed Ubuntu, sometimes the system gets slow. Sometimes after coding in vscode or even only using Firefox the system gets slow without explanation (even if I close everything, simple programs like Firefox with only 1 tab runs slow). Everything becomes laggy like scrolling and I can notice lag even on typing. 

BUT, if I suspend and turn on again, everything works well and fast as expected. I would like to know if anyone have the same problem and how can I solve it.

Also, the battery takes around 3 hours to discharge and I would like to know if its normal or if yours have more time before discharging.

UPDATE 1:

BIOS version 207 not available anymore. Only versions 208 and 300. I will update and see if it helps

---

### Post by mörgæs on 2020-02-22
First let's see that you actually have the same hardware as other people in the thread. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by victor7095 on 2020-02-23
Here is the output of **sudo lshw -sanitize > lshw.txt**:
```

computer
    description: Notebook
    product: Zephyrus G GU502DU_GA502DU
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.2.1 dmi-3.2.1 smp vsyscall32
    configuration: boot=normal chassis=notebook family=Zephyrus uuid=[REMOVED]
  *-core
       description: Motherboard
       product: GU502DU
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: [REMOVED]
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: GU502DU.300
          date: 12/23/2019
          size: 64KiB
          capacity: 16MiB
          capabilities: pci upgrade shadowing cdboot bootselect  socketedrom edd int13floppy1200 int13floppy720 int13floppy2880  int5printscreen int14serial int17printer acpi usb smartbattery  biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 16GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2667 MHz (0,4 ns)
             product: 8ATF1G64HZ-2G6E1
             vendor: Micron Technology
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
        *-bank:1
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2667 MHz (0,4 ns)
             product: M471A1K43DB1-CTD
             vendor: Samsung
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
     *-cache:0
          description: L1 cache
          physical id: c
          slot: L1 - Cache
          size: 384KiB
          capacity: 384KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: d
          slot: L2 - Cache
          size: 2MiB
          capacity: 2MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: e
          slot: L3 - Cache
          size: 4MiB
          capacity: 4MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: AMD Ryzen 7 3750H with Radeon Vega Mobile Gfx
          vendor: Advanced Micro Devices [AMD]
          physical id: f
          bus info: cpu@0
          version: AMD Ryzen 7 3750H with Radeon Vega Mobile Gfx
          serial: [REMOVED]
          slot: FP5
          size: 1592MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae  mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2  ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc  rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq  monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c  rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse  3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext  perfctr_llc mwaitx cpb hw_pstate sme ssbd sev ibpb vmmcall fsgsbase bmi1  avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec  xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv svm_lock nrip_save  tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold  avic v_vmsave_vmload vgif overflow_recov succor smca cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci:0
          description: Host bridge
          product: Raven/Raven2 Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: Raven/Raven2 IOMMU
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: Raven/Raven2 PCIe GPP Bridge [6:0]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:f000(size=4096) memory:f6000000-f70fffff ioport:c0000000(size=303038464)
           *-display
                description: VGA compatible controller
                product: TU116M [GeForce GTX 1660 Ti Mobile]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:74 memory:f6000000-f6ffffff  memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:f000(size=128)  memory:f7000000-f707ffff
           *-multimedia
                description: Audio device
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:67 memory:f7080000-f7083fff
           *-usb
                description: USB controller
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.2
                bus info: pci@0000:01:00.2
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: msi pciexpress pm xhci cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:32 memory:d2000000-d203ffff memory:d2040000-d204ffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.3.0-40-generic xhci-hcd
                   physical id: 0
                   bus info: usb@1
                   logical name: usb1
                   version: 5.03
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.3.0-40-generic xhci-hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 5.03
                   capabilities: usb-3.10
                   configuration: driver=hub slots=4 speed=10000Mbit/s
           *-serial
                description: Serial bus controller
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0.3
                bus info: pci@0000:01:00.3
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: msi pciexpress pm bus_master cap_list
                configuration: driver=nvidia-gpu latency=0
                resources: irq:52 memory:f7084000-f7084fff
        *-pci:1
             description: PCI bridge
             product: Raven/Raven2 PCIe GPP Bridge [6:0]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:f7900000-f79fffff
           *-storage
                description: Non-Volatile memory controller
                product: SSDPEKNW020T8 [660p, 2TB]
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:54 memory:f7900000-f7903fff
        *-pci:2
             description: PCI bridge
             product: Raven/Raven2 PCIe GPP Bridge [6:0]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:e000(size=4096) memory:f7800000-f78fffff
           *-network
                description: Wireless interface
                product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 00
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8821ce ip=[REMOVED] latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:66 ioport:e000(size=256) memory:f7800000-f780ffff
        *-pci:3
             description: PCI bridge
             product: Raven/Raven2 PCIe GPP Bridge [6:0]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:d000(size=4096) memory:f7700000-f77fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 15
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd  autonegotiation
                configuration: autonegotiation=on broadcast=yes  driver=r8169 firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no  multicast=yes port=MII
                resources: irq:53 ioport:d000(size=256) memory:f7704000-f7704fff memory:f7700000-f7703fff
        *-pci:4
             description: PCI bridge
             product: Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus A
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:c000(size=4096) memory:f7200000-f76fffff ioport:e0000000(size=270532608)
           *-display
                description: VGA compatible controller
                product: Picasso
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:05:00.0
                version: c1
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
                configuration: driver=amdgpu latency=0
                resources: irq:72 memory:e0000000-efffffff  memory:f0000000-f01fffff ioport:c000(size=256) memory:f7600000-f767ffff
           *-multimedia:0
                description: Audio device
                product: Raven/Raven2/Fenghuang HDMI/DP Audio Controller
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:71 memory:f7688000-f768bfff
           *-generic:0 UNCLAIMED
                description: Encryption controller
                product: Family 17h (Models 10h-1fh) Platform Security Processor
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:05:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix cap_list
                configuration: latency=0
                resources: memory:f7500000-f75fffff memory:f768e000-f768ffff
           *-usb:0
                description: USB controller
                product: Raven USB 3.1
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:05:00.3
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:33 memory:f7400000-f74fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.3.0-40-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 5.03
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb:0
                      description: Keyboard
                      product: N-KEY Device
                      vendor: ASUSTeK Computer Inc.
                      physical id: 1
                      bus info: usb@3:1
                      version: 0.02
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
                 *-usb:1
                      description: Mouse
                      product: Razer Lancehead Wireless
                      vendor: Razer
                      physical id: 2
                      bus info: usb@3:2
                      version: 2.00
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=500mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.3.0-40-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 5.03
                   capabilities: usb-3.10
                   configuration: driver=hub slots=4 speed=10000Mbit/s
           *-usb:1
                description: USB controller
                product: Raven USB 3.1
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.4
                bus info: pci@0000:05:00.4
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:24 memory:f7300000-f73fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.3.0-40-generic xhci-hcd
                   physical id: 0
                   bus info: usb@5
                   logical name: usb5
                   version: 5.03
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
                 *-usb
                      description: Bluetooth wireless interface
                      product: Bluetooth Radio
                      vendor: Realtek
                      physical id: 2
                      bus info: usb@5:2
                      version: 1.10
                      serial: [REMOVED]
                      capabilities: bluetooth usb-1.10
                      configuration: driver=btusb maxpower=500mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.3.0-40-generic xhci-hcd
                   physical id: 1
                   bus info: usb@6
                   logical name: usb6
                   version: 5.03
                   capabilities: usb-3.10
                   configuration: driver=hub slots=1 speed=10000Mbit/s
           *-multimedia:1
                description: Audio device
                product: Family 17h (Models 10h-1fh) HD Audio Controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.6
                bus info: pci@0000:05:00.6
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:55 memory:f7680000-f7687fff
           *-generic:1
                description: Non-VGA unclassified device
                product: Raven/Raven2/Renoir Non-Sensor Fusion Hub KMDF driver
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.7
                bus info: pci@0000:05:00.7
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix cap_list
                configuration: driver=i2c_amd_mp2 latency=0
                resources: irq:33 memory:f7200000-f72fffff memory:f768c000-f768dfff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 61
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 51
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:08.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10a
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pnp00:00
          product: PnP device PNP0c01
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0b00
          physical id: 2
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:02
          product: PnP device ATK3001
          physical id: 3
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 4
          capabilities: pnp
          configuration: driver=system
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: docker0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=[REMOVED] link=no multicast=yes

```

---

### Post by mörgæs on 2020-02-24
The only thing I can suggest is trying a live boot of 20.04 to see if a newer kernel makes a difference.

---

### Post by victor7095 on 2020-02-24
Tried live session on 20.04 (with and without safe graphics mode enabled). The battery still drains very fast and the laptop gets pretty hot too.

---

### Post by edricus2 on 2020-03-12
Don't update to bios v300 it doesn't solve the problem. Also who have the file for bios v207 ? I can't find it anywhere and I have to stick on Windows... please someone
edit: found it, you just have to guess the URL
[https://dlcdnets.asus.com/pub/ASUS/GamingNB/GU502DU/GU502DUAS207.zip](https://dlcdnets.asus.com/pub/ASUS/GamingNB/GU502DU/GU502DUAS207.zip)
and if the link is not available anymore, I have uploaded a mirror link
[https://mega.nz/#!g0x3QRLQ!BPKslDeUUkFyQjNh18zixDcLnApeScmYB_E1pGv_3hk](https://mega.nz/#!g0x3QRLQ!BPKslDeUUkFyQjNh18zixDcLnApeScmYB_E1pGv_3hk)

To downgrade simply do the same than updating. Put the file in a USB stick, reboot to bios, start easy flash and choose the file.

---

### Post by orientino on 2020-03-17
Did you figure out how to make the battery last longer, does anybody know if using another distribution the battery life will be the same? It's a waste that on windows it can go on for 7/8 hours and linux barely got half of it :(

---

### Post by andrewfer000 on 2020-03-19
Yes please let me know how BIOS 300 is working on this system. I want to see if it fixes issues.

---

### Post by datascientistkg on 2020-03-26
what about keyboard backlights? does bios 300 fix this problem?

---

### Post by datascientistkg on 2020-04-05
URGENT! Help please! Can somebody give a dump of your bios? 207, 208 or 300?

---

### Post by albator1932 on 2020-04-14
I do have the same laptop (and the same issues obviously) and currently running Pop!OS 19.10 (which is Ubuntu based). I'd be happy to help but I don't know how to dump the BIOS (I'm using 207 because of the 400MHz speed issue I had with 208, didn't try the 300 though)

---

### Post by orientino on 2020-04-17
How is the battery performing in Pop!OS? Is it the same as in Ubuntu which has only 2/3 hours?

---

### Post by datascientistkg on 2020-04-19
> **orientino said:**
> How is the battery performing in Pop!OS? Is it the same as in Ubuntu which has only 2/3 hours?

I have PopOS, it's the same as Ubuntu 2/3 hours

---

### Post by albator1932 on 2020-04-20
Yes, 2/3 hours (I don't any precise measurement but it feels more like 2 hours to me)

---

### Post by MemoNick on 2020-06-09
> **victor7095 said:**
> Hi, I followed your instructions, and I can see nvidia-settings window. But since I installed Ubuntu, sometimes the system gets slow. Sometimes after coding in vscode or even only using Firefox the system gets slow without explanation (even if I close everything, simple programs like Firefox with only 1 tab runs slow). Everything becomes laggy like scrolling and I can notice lag even on typing. 


BUT, if I suspend and turn on again, everything works well and fast as expected. I would like to know if anyone have the same problem and how can I solve it.


Also, the battery takes around 3 hours to discharge and I would like to know if its normal or if yours have more time before discharging.


UPDATE 1:


BIOS version 207 not available anymore. Only versions 208 and 300. I will update and see if it helps


I have the same problem as the quoted comment. The problem is very high CPU usage for anything, including gnome-shell. I'm not sure what to do about it. Now I've switched from gdm3 to lightdm and Ubuntu is running smoother, but I don't know if this will last. When Ubuntu is slow, it's straight from login and as the original comment said, closing everything doesn't really help. I noticed that nvidia-smi shows "no running processes found." I am using the latest nvidia drivers. Any ideas?


This is my lshw.txt:


```
computer    description: Notebook
    product: Zephyrus G GU502DU_GA502DU
    vendor: ASUSTeK COMPUTER INC.
    version: 1.0
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-3.2.1 dmi-3.2.1 smp vsyscall32
    configuration: boot=normal chassis=notebook family=Zephyrus uuid=[REMOVED]
  *-core
       description: Motherboard
       product: GU502DU
       vendor: ASUSTeK COMPUTER INC.
       physical id: 0
       version: 1.0
       serial: [REMOVED]
       slot: MIDDLE
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: GU502DU.208
          date: 08/01/2019
          size: 64KiB
          capacity: 16MiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int14serial int17printer acpi usb smartbattery biosbootspecification uefi
     *-memory
          description: System Memory
          physical id: a
          slot: System board or motherboard
          size: 8GiB
        *-bank:0
             description: SODIMM DDR4 Synchronous Unbuffered (Unregistered) 2667 MHz (0.4 ns)
             product: 8ATF1G64HZ-2G6E1
             vendor: Micron Technology
             physical id: 0
             serial: [REMOVED]
             slot: DIMM 0
             size: 8GiB
             width: 64 bits
             clock: 2667MHz (0.4ns)
        *-bank:1
             description: [empty]
             product: Unknown
             vendor: Unknown
             physical id: 1
             serial: [REMOVED]
             slot: DIMM 0
     *-cache:0
          description: L1 cache
          physical id: c
          slot: L1 - Cache
          size: 384KiB
          capacity: 384KiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: d
          slot: L2 - Cache
          size: 2MiB
          capacity: 2MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=2
     *-cache:2
          description: L3 cache
          physical id: e
          slot: L3 - Cache
          size: 4MiB
          capacity: 4MiB
          clock: 1GHz (1.0ns)
          capabilities: pipeline-burst internal write-back unified
          configuration: level=3
     *-cpu
          description: CPU
          product: AMD Ryzen 7 3750H with Radeon Vega Mobile Gfx
          vendor: Advanced Micro Devices [AMD]
          physical id: f
          bus info: cpu@0
          version: AMD Ryzen 7 3750H with Radeon Vega Mobile Gfx
          serial: [REMOVED]
          slot: FP5
          size: 3770MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: lm fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 constant_tsc rep_good nopl nonstop_tsc cpuid extd_apicid aperfmperf pni pclmulqdq monitor ssse3 fma cx16 sse4_1 sse4_2 movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb hw_pstate sme ssbd sev ibpb vmmcall fsgsbase bmi1 avx2 smep bmi2 rdseed adx smap clflushopt sha_ni xsaveopt xsavec xgetbv1 xsaves clzero irperf xsaveerptr arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif overflow_recov succor smca cpufreq
          configuration: cores=4 enabledcores=4 threads=8
     *-pci:0
          description: Host bridge
          product: Raven/Raven2 Root Complex
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-generic UNCLAIMED
             description: IOMMU
             product: Raven/Raven2 IOMMU
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 0.2
             bus info: pci@0000:00:00.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: msi ht bus_master cap_list
             configuration: latency=0
        *-pci:0
             description: PCI bridge
             product: Raven/Raven2 PCIe GPP Bridge [6:0]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 ioport:f000(size=4096) memory:f6000000-f70fffff ioport:c0000000(size=303038464)
           *-display
                description: VGA compatible controller
                product: TU116M [GeForce GTX 1660 Ti Mobile]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:65 memory:f6000000-f6ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:f000(size=128) memory:f7000000-f707ffff
           *-multimedia
                description: Audio device
                product: TU116 High Definition Audio Controller
                vendor: NVIDIA Corporation
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:67 memory:f7080000-f7083fff
           *-usb
                description: USB controller
                product: TU116 USB 3.1 Host Controller
                vendor: NVIDIA Corporation
                physical id: 0.2
                bus info: pci@0000:01:00.2
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: msi pciexpress pm xhci cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:32 memory:d2000000-d203ffff memory:d2040000-d204ffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.4.0-26-generic xhci-hcd
                   physical id: 0
                   bus info: usb@1
                   logical name: usb1
                   version: 5.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.4.0-26-generic xhci-hcd
                   physical id: 1
                   bus info: usb@2
                   logical name: usb2
                   version: 5.04
                   capabilities: usb-3.10
                   configuration: driver=hub slots=4 speed=10000Mbit/s
           *-serial
                description: Serial bus controller
                product: TU116 [GeForce GTX 1650 SUPER]
                vendor: NVIDIA Corporation
                physical id: 0.3
                bus info: pci@0000:01:00.3
                version: a1
                width: 32 bits
                clock: 33MHz
                capabilities: msi pciexpress pm bus_master cap_list
                configuration: driver=nvidia-gpu latency=0
                resources: irq:52 memory:f7084000-f7084fff
        *-pci:1
             description: PCI bridge
             product: Raven/Raven2 PCIe GPP Bridge [6:0]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:27 memory:f7900000-f79fffff
           *-storage
                description: Non-Volatile memory controller
                product: SSD 660P Series
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 03
                width: 64 bits
                clock: 33MHz
                capabilities: storage pm msi pciexpress msix nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:54 memory:f7900000-f7903fff
        *-pci:2
             description: PCI bridge
             product: Raven/Raven2 PCIe GPP Bridge [6:0]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:28 ioport:e000(size=4096) memory:f7800000-f78fffff
           *-network
                description: Wireless interface
                product: RTL8821CE 802.11ac PCIe Wireless Network Adapter
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlp3s0
                version: 00
                serial: [REMOVED]
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8821ce ip=[REMOVED] latency=0 multicast=yes wireless=IEEE 802.11AC
                resources: irq:73 ioport:e000(size=256) memory:f7800000-f780ffff
        *-pci:3
             description: PCI bridge
             product: Raven/Raven2 PCIe GPP Bridge [6:0]
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:29 ioport:d000(size=4096) memory:f7700000-f77fffff
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 15
                serial: [REMOVED]
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=MII
                resources: irq:53 ioport:d000(size=256) memory:f7704000-f7704fff memory:f7700000-f7703fff
        *-pci:4
             description: PCI bridge
             product: Raven/Raven2 Internal PCIe GPP Bridge 0 to Bus A
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 8.1
             bus info: pci@0000:00:08.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:30 ioport:c000(size=4096) memory:f7200000-f76fffff ioport:e0000000(size=270532608)
           *-display
                description: VGA compatible controller
                product: Picasso
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:05:00.0
                version: c1
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix vga_controller bus_master cap_list
                configuration: driver=amdgpu latency=0
                resources: irq:66 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:c000(size=256) memory:f7600000-f767ffff
           *-multimedia:0
                description: Audio device
                product: Raven/Raven2/Fenghuang HDMI/DP Audio Controller
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0.1
                bus info: pci@0000:05:00.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:69 memory:f7688000-f768bfff
           *-generic:0 UNCLAIMED
                description: Encryption controller
                product: Family 17h (Models 10h-1fh) Platform Security Processor
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.2
                bus info: pci@0000:05:00.2
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix cap_list
                configuration: latency=0
                resources: memory:f7500000-f75fffff memory:f768e000-f768ffff
           *-usb:0
                description: USB controller
                product: Raven USB 3.1
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.3
                bus info: pci@0000:05:00.3
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:33 memory:f7400000-f74fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.4.0-26-generic xhci-hcd
                   physical id: 0
                   bus info: usb@3
                   logical name: usb3
                   version: 5.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=4 speed=480Mbit/s
                 *-usb
                      description: Keyboard
                      product: N-KEY Device
                      vendor: ASUSTeK Computer Inc.
                      physical id: 1
                      bus info: usb@3:1
                      version: 0.02
                      capabilities: usb-2.00
                      configuration: driver=usbhid maxpower=100mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.4.0-26-generic xhci-hcd
                   physical id: 1
                   bus info: usb@4
                   logical name: usb4
                   version: 5.04
                   capabilities: usb-3.10
                   configuration: driver=hub slots=4 speed=10000Mbit/s
           *-usb:1
                description: USB controller
                product: Raven USB 3.1
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.4
                bus info: pci@0000:05:00.4
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix xhci bus_master cap_list
                configuration: driver=xhci_hcd latency=0
                resources: irq:24 memory:f7300000-f73fffff
              *-usbhost:0
                   product: xHCI Host Controller
                   vendor: Linux 5.4.0-26-generic xhci-hcd
                   physical id: 0
                   bus info: usb@5
                   logical name: usb5
                   version: 5.04
                   capabilities: usb-2.00
                   configuration: driver=hub slots=2 speed=480Mbit/s
                 *-usb
                      description: Bluetooth wireless interface
                      product: Bluetooth Radio
                      vendor: Realtek
                      physical id: 2
                      bus info: usb@5:2
                      version: 1.10
                      serial: [REMOVED]
                      capabilities: bluetooth usb-1.10
                      configuration: driver=btusb maxpower=500mA speed=12Mbit/s
              *-usbhost:1
                   product: xHCI Host Controller
                   vendor: Linux 5.4.0-26-generic xhci-hcd
                   physical id: 1
                   bus info: usb@6
                   logical name: usb6
                   version: 5.04
                   capabilities: usb-3.10
                   configuration: driver=hub slots=1 speed=10000Mbit/s
           *-multimedia:1
                description: Audio device
                product: Family 17h (Models 10h-1fh) HD Audio Controller
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.6
                bus info: pci@0000:05:00.6
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi bus_master cap_list
                configuration: driver=snd_hda_intel latency=0
                resources: irq:71 memory:f7680000-f7687fff
           *-generic:1
                description: Non-VGA unclassified device
                product: Raven/Raven2/Renoir Non-Sensor Fusion Hub KMDF driver
                vendor: Advanced Micro Devices, Inc. [AMD]
                physical id: 0.7
                bus info: pci@0000:05:00.7
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix cap_list
                configuration: driver=i2c_amd_mp2 latency=0
                resources: irq:33 memory:f7200000-f72fffff memory:f768c000-f768dfff
        *-serial
             description: SMBus
             product: FCH SMBus Controller
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 61
             width: 32 bits
             clock: 66MHz
             configuration: driver=piix4_smbus latency=0
             resources: irq:0
        *-isa
             description: ISA bridge
             product: FCH LPC Bridge
             vendor: Advanced Micro Devices, Inc. [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 51
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
     *-pci:1
          description: Host bridge
          product: Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 101
          bus info: pci@0000:00:01.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Family 17h (Models 00h-1fh) PCIe Dummy Host Bridge
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 102
          bus info: pci@0000:00:08.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 0
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 103
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 1
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 104
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 2
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 105
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 3
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 106
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k10temp
          resources: irq:0
     *-pci:7
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 4
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 107
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 5
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 108
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 6
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 109
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: Raven/Raven2 Device 24: Function 7
          vendor: Advanced Micro Devices, Inc. [AMD]
          physical id: 10a
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pnp00:00
          product: PnP device PNP0c01
          physical id: 1
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0b00
          physical id: 2
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:02
          product: PnP device ATK3001
          physical id: 3
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 4
          capabilities: pnp
          configuration: driver=system
```

---

### Post by faresbaresmares on 2021-05-04
Does anyone else have a freezing problem where the laptop gets bricked after an unexpected shutdown when installing linux on a 2nd SSD?
Tried on BIOS 207, 306, ubuntu 20.04/18.04, with windows 10 as dual boot and without (only linux).

It's driving me crazy...

---

