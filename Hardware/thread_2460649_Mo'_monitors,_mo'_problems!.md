---
title: "Mo' monitors, mo' problems!"
date: 2021-04-15
forum: Hardware
---

### Post by bvargo on 2021-04-15
[B]Problems:
[/B]1. Upon boot, when getting to the "general" lock screen, the login screen shows up in landscape mode on monitor 3 which is physically in portrait right. This makes navigating the menu a PITA.
2. When waking up from screensaver, the computer fails to respond, i.e., the monitors stay black. My current workaround is to hit CTRL-ALT-F1 to bounce out to the "general" lock screen instead of my user lock screen. Unfortunately, this results in problem 1.
3. Sometimes, when waking from screen saver to the user lock screen (I think it doesn't do it on the general lock screen), there are a series of black bars and blocks that flicker on the right edge of the portrait display (see below). The workaround is the same as 2 above, i.e., go to the general lock screen but again that results in problem 1.

[B]Desired resolution:
[/B]1. The general lock/login screen should be displayed on the same monitor as the BIOS, i.e., monitor 2.
2. It would be great if I could figure out how to stop problems 2 & 3.

```
$ alias ver; ver; xrandr
alias ver='screenfetch -n; lsb_release -a; uname -a'
No value set for `/apps/metacity/general/theme'
 bvargo@gigabyte
 OS: Ubuntu 20.04 focal
 Kernel: x86_64 Linux 5.8.0-48-generic
 Uptime: 6d 14h 44m
 Packages: 2585
 Shell: bash 5.0.17
 Resolution: 7840x2560
 DE: GNOME 3.36.5
 WM: Metacity
 GTK Theme: Yaru [GTK2/3]
 Icon Theme: ubuntu-mono-light
 Font: Ubuntu 11
 Disk: 3.0T / 3.8T (84%)
 CPU: Intel Core i5-3570K @ 4x 3.8GHz [40.0°C]


 RAM: 20028MiB / 24013MiB
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:    20.04
Codename:    focal
Linux gigabyte 5.8.0-48-generic #54~20.04.1-Ubuntu SMP Sat Mar 20 13:40:25 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
Screen 0: minimum 8 x 8, current 7840 x 2560, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 2560x1440+1920+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440     59.95*+
HDMI-0 connected 1920x1080+0+360 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080     60.00*+
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
DP-0 connected 1920x1080+5920+1057 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080     60.00*+  50.00  
   1680x1050     59.95  
   1600x900      60.00  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1280x720      60.00    50.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
DVI-D-0 connected 1440x2560+4480+0 left (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440     59.95*+
DP-1 disconnected (normal left inverted right x axis y axis)

```

The [NVIDIA GeForce GTX 650 Ti Boost card]("https://www.nvidia.com/en-us/geforce/graphics-cards/geforce-gtx-650ti-boost/specifications/") drives 4 monitors as displayed below. (I wonder why screenfetch isn't displaying the graphics card anymore?*) Monitors 2 and 3 are matched 27" 2560×1440 monitors driven off the DVI-I and DVI-D ports.  Monitor 2 is normal landscape and 3 is portrait right.  (Monitor 1 and 4 are generally superfluous—and, importantly, behave properly.  But I have them so why not...both are DVI input but driven off the Display Port and HDMI port w/adapters.)
The system-recognized primary monitor, i.e., the one that BIOS/GRUB display on, is monitor 2.  It is also set as the primary monitor in Ubuntu such that the top bar is displayed on it.
 
[ATTACH=CONFIG]288316[/ATTACH]

As stated above, monitor three is portrait right (physically rotated clockwise from normal landscape):

[ATTACH=CONFIG]288317[/ATTACH]

(I cannot get into gnome-control-center at the moment but monitor 4 is a Samsung S22B300, see below.)

**Problems:**
  1.  Upon boot, when getting to the "general" lock screen, the login screen shows up in landscape mode on monitor 3 which is physically in portrait right.  This makes navigating the menu a PITA.
  2.  When waking up from screensaver, the computer fails to respond, i.e., the monitors stay black.  My current workaround is to hit CTRL-ALT-F1 to bounce out to the "general" lock screen instead of my user lock screen.  Unfortunately, this results in problem 1.
  3.  Sometimes, when waking from screen saver to the user lock screen (I think it doesn't do it on the general lock screen), there are a series of black bars and blocks that flicker on the right edge of the portrait display (see below).  The workaround is the same as 2 above, i.e., go to the general lock screen but again that results in problem 1.

[B]Desired resolution:
[/B]  1.  The general lock/login screen should be displayed on the same monitor as the BIOS, i.e., monitor 2.
  2.  It would be great if I could figure out how to stop problems 2 & 3.

This picture shows most of monitor 3 obscured:
[ATTACH=CONFIG]288318[/ATTACH]

```
 cat /var/log/Xorg.0.log |grep NVIDIA
[     6.255] (II) Module nvidia: vendor="NVIDIA Corporation"
[     6.260] (II) NVIDIA dlloader X Driver  460.39  Thu Jan 21 21:54:11 UTC 2021
[     6.260] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     6.260] (II) NOUVEAU driver for NVIDIA chipset families :
[     6.269] (II) NVIDIA(0): Creating default Display subsection in Screen section
[     6.269] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     6.269] (==) NVIDIA(0): RGB weight 888
[     6.269] (==) NVIDIA(0): Default visual is TrueColor
[     6.269] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     6.269] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
[     6.269] (**) NVIDIA(0): Enabling 2D acceleration
[     6.379] (II) Module glxserver_nvidia: vendor="NVIDIA Corporation"
[     6.379] (II) NVIDIA GLX Module  460.39  Thu Jan 21 21:51:40 UTC 2021
[     6.380] (II) NVIDIA: The X server supports PRIME Render Offload.
[     8.541] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[     8.541] (--) NVIDIA(0):     CRT-0
[     8.541] (--) NVIDIA(0):     DFP-0 (boot)
[     8.541] (--) NVIDIA(0):     DFP-1
[     8.541] (--) NVIDIA(0):     DFP-2
[     8.542] (--) NVIDIA(0):     DFP-3
[     8.542] (--) NVIDIA(0):     DFP-4
[     8.542] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 650 Ti BOOST (GK106) at PCI:1:0:0
[     8.542] (II) NVIDIA(0):     (GPU-0)
[     8.542] (--) NVIDIA(0): Memory: 1048576 kBytes
[     8.542] (--) NVIDIA(0): VideoBIOS: 80.06.59.00.52
[     8.542] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     8.569] (--) NVIDIA(GPU-0): CRT-0: disconnected
[     8.569] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     8.569] (--) NVIDIA(GPU-0): 
[     8.614] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-0): connected
[     8.614] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-0): Internal TMDS
[     8.614] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-0): 330.0 MHz maximum pixel clock
[     8.614] (--) NVIDIA(GPU-0): 
[     8.620] (--) NVIDIA(GPU-0): DELL E2414H (DFP-1): connected
[     8.620] (--) NVIDIA(GPU-0): DELL E2414H (DFP-1): Internal TMDS
[     8.620] (--) NVIDIA(GPU-0): DELL E2414H (DFP-1): 165.0 MHz maximum pixel clock
[     8.620] (--) NVIDIA(GPU-0): 
[     8.649] (--) NVIDIA(GPU-0): Samsung S22B300 (DFP-2): connected
[     8.649] (--) NVIDIA(GPU-0): Samsung S22B300 (DFP-2): Internal TMDS
[     8.649] (--) NVIDIA(GPU-0): Samsung S22B300 (DFP-2): 165.0 MHz maximum pixel clock
[     8.649] (--) NVIDIA(GPU-0): 
[     8.675] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-3): connected
[     8.675] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-3): Internal TMDS
[     8.675] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-3): 330.0 MHz maximum pixel clock
[     8.675] (--) NVIDIA(GPU-0): 
[     8.675] (--) NVIDIA(GPU-0): DFP-4: disconnected
[     8.675] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[     8.675] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[     8.675] (--) NVIDIA(GPU-0): 
[     8.682] (==) NVIDIA(0): 
[     8.682] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     8.682] (==) NVIDIA(0):     will be used as the requested mode.
[     8.682] (==) NVIDIA(0): 
[     8.682] (II) NVIDIA(0): Validated MetaModes:
[     8.682] (II) NVIDIA(0):    
[     8.682] (II) NVIDIA(0):     "DFP-0:nvidia-auto-select,DFP-1:nvidia-auto-select,DFP-2:nvidia-auto-select,DFP-3:nvidia-auto-select"
[     8.682] (II) NVIDIA(0): Virtual screen size determined to be 8960 x 1440
[     8.685] (--) NVIDIA(0): DPI set to (108, 107); computed from "UseEdidDpi" X config
[     8.685] (--) NVIDIA(0):     option
[     8.685] (II) NVIDIA: Using 6144.00 MB of virtual memory for indirect memory
[     8.685] (II) NVIDIA:     access.
[     8.705] (II) NVIDIA(0): Setting mode "DFP-0:nvidia-auto-select,DFP-1:nvidia-auto-select,DFP-2:nvidia-auto-select,DFP-3:nvidia-auto-select"
[     8.749] (==) NVIDIA(0): Disabling shared memory pixmaps
[     8.749] (==) NVIDIA(0): Backing store enabled
[     8.749] (==) NVIDIA(0): Silken mouse enabled
[     8.750] (==) NVIDIA(0): DPMS enabled
[     8.751] (II) NVIDIA(0): [DRI2] Setup complete
[     8.751] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia

&#8942;

[519989.444] (--) NVIDIA(GPU-0): CRT-0: disconnected
[519989.444] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[519989.444] (--) NVIDIA(GPU-0): 
[519989.489] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-0): connected
[519989.489] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-0): Internal TMDS
[519989.489] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-0): 330.0 MHz maximum pixel clock
[519989.489] (--) NVIDIA(GPU-0): 
[519989.495] (--) NVIDIA(GPU-0): DELL E2414H (DFP-1): connected
[519989.496] (--) NVIDIA(GPU-0): DELL E2414H (DFP-1): Internal TMDS
[519989.496] (--) NVIDIA(GPU-0): DELL E2414H (DFP-1): 165.0 MHz maximum pixel clock
[519989.496] (--) NVIDIA(GPU-0): 
[519989.525] (--) NVIDIA(GPU-0): Samsung S22B300 (DFP-2): connected
[519989.525] (--) NVIDIA(GPU-0): Samsung S22B300 (DFP-2): Internal TMDS
[519989.525] (--) NVIDIA(GPU-0): Samsung S22B300 (DFP-2): 165.0 MHz maximum pixel clock
[519989.525] (--) NVIDIA(GPU-0): 
[519989.548] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-3): connected
[519989.548] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-3): Internal TMDS
[519989.548] (--) NVIDIA(GPU-0): HYO DUAL-DVI (DFP-3): 330.0 MHz maximum pixel clock
[519989.548] (--) NVIDIA(GPU-0): 
[519989.548] (--) NVIDIA(GPU-0): DFP-4: disconnected
[519989.548] (--) NVIDIA(GPU-0): DFP-4: Internal DisplayPort
[519989.548] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[519989.548] (--) NVIDIA(GPU-0): 
[519989.565] (II) NVIDIA(0): Setting mode "DVI-I-1: nvidia-auto-select @2560x1440 +4480+0 {ViewPortIn=2560x1440, ViewPortOut=2560x1440+0+0}, HDMI-0: nvidia-auto-select @1920x1080 +7040+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, DP-0: nvidia-auto-select @1920x1080 +2560+0 {ViewPortIn=1920x1080, ViewPortOut=1920x1080+0+0}, DVI-D-0: nvidia-auto-select @2560x1440 +0+0 {ViewPortIn=2560x1440, ViewPortOut=2560x1440+0+0}"

```


*This is likely due to an NVIDIA update that pushed through at 5 this morning:
```

Start-Date: 2021-04-15  04:54:47
Commandline: apt upgrade -y
Requested-By: bvargo (1000)
Upgrade: libseccomp2:amd64 (2.4.3-1ubuntu3.20.04.3, 2.5.1-1ubuntu1~20.04.1), libnvidia-compute-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-compute-460:i386 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-encode-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-encode-460:i386 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), nvidia-kernel-common-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), xserver-xorg-video-nvidia-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-gl-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-gl-460:i386 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-fbc1-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-fbc1-460:i386 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-decode-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-decode-460:i386 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), google-chrome-stable:amd64 (89.0.4389.114-1, 90.0.4430.72-1), libjs-underscore:amd64 (1.9.1~dfsg-1, 1.9.1~dfsg-1ubuntu0.20.04.1), libnvidia-cfg1-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), nvidia-utils-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), picard:amd64 (2.6-1+git3910~ppa23~ubuntu20.04.1, 2.6-1+git3914~ppa23~ubuntu20.04.1), nvidia-dkms-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), nvidia-compute-utils-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-ifr1-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libnvidia-ifr1-460:i386 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), nvidia-driver-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), code:amd64 (1.55.1-1617808414, 1.55.2-1618307277), pciutils:amd64 (1:3.6.4-1, 1:3.6.4-1ubuntu0.20.04.1), libnvidia-common-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), libpci3:amd64 (1:3.6.4-1, 1:3.6.4-1ubuntu0.20.04.1), libpci3:i386 (1:3.6.4-1, 1:3.6.4-1ubuntu0.20.04.1), libnvidia-extra-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1), nvidia-kernel-source-460:amd64 (460.39-0ubuntu0.20.04.1, 460.56-0ubuntu0.20.04.1)
End-Date: 2021-04-15  04:57:42

```
[COLOR=#FFFFFF][FONT=&amp]
[/FONT][/COLOR]

---

### Post by slickymaster on 2021-04-15
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by bvargo on 2021-04-15
Ok, the paperclip should be readily available then...  (it is apparently not something that can be used in quick reply or edit).

[ATTACH=CONFIG]288322[/ATTACH]

Also, it is rather difficult to guess why the system did that on its own without any explanation.

See also Ubuntu forums FAQ:  Only mentions that there are size limits and linking e.g., to imgur (italics added) not your suggestion regarding file sizes.

**Attachments and _Images_**

[COLOR=#000000]**How do I attach a file to a post?**
To attach a file to your post, you need to be using the main 'New Post' or 'New Thread' page and not 'Quick Reply'. To use the main 'New Post' page, click the 'Post Reply' button in the relevant thread.
On this page, below the message box, you will find a button labelled 'Manage Attachments'. Clicking this button will open a new window for uploading attachments. You can upload an attachment either from your computer or from another URL by using the appropriate box on this page. Alternatively you can click the Attachment Icon to open this page.
To upload a file from your computer, click the 'Browse' button and locate the file. To upload a file from another URL, enter the full URL for the file in the second box on this page. Once you have completed one of the boxes, click 'Upload'.
Once the upload is completed the file name will appear below the input boxes in this window. You can then close the window to return to the new post screen.
**What files types can I use? How large can attachments be?**
In the attachment window you will find a list of the allowed file types and their maximum sizes. Files that are larger than these sizes will be rejected. There also is an overall quota limit of 5 files you can post in a reply.
**How do I add an image to a post?**
If you have uploaded an image as an attachment, you can click the arrow next to the 'Attachment Icon' and select it from the list. This will be inserted into your post and can be located where you want it displayed.
*To include an image that is not uploaded as an attachment and is located on another website, you can do so by copying the full URL to the image, (not the page on which the image is located), and either pressing the 'Insert Image' icon or by typing [img] before the URL and [/img] after it, ensuring that you do not have any spaces before or after the URL of the image.*

[/COLOR]

---

### Post by QIII on 2021-04-16
The attachment paperclip is visible in Edit -> Go Advanced if you want to edit.

Quick Reply is just that, and has few options.

---

