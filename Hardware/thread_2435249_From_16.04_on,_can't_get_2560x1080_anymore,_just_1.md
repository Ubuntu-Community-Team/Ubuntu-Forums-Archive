---
title: "From 16.04 on, can't get 2560x1080 anymore, just 1920x1080"
date: 2020-01-18
forum: Hardware
---

### Post by claudiocapobianchi on 2020-01-18
Hi all, I have an LG 25UM58 ultrawide monitor connected via HDMI to an ATI 5770. On Ubuntu 14.04 it works well at desired resolution (21:9 2560x1080 @ 60Hz), so cable,VGA and monitor are fine. I know that *fgrlx* is not used anymore (now ubuntu uses *amdgpu*) and latest proprietary drivers for my graphics card are for 14.04.
I am ok with open drivers shipped with ubuntu 16.04+, I don't need performance, the only thing I care about is using my monitor at full resolution.
Things I tried to reach 2560x1080 with no luck, mainly looking for a working modeline on ubuntu, linux mint and debian:
[LIST]
[*]add custom resolution with cvt and gtf 
[*]add to xorg.conf: ```

SubSection "Display"
Virtual 2560 1080

``` 
[*]extract modeline from xorg.conf used in 14.04, which is ```
Modeline "2560x1080"  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync 
``` 
[*]*get-edid | parse-edid *to read modelines, interestingly, it found more resolutions on 16.04 than 14.04, here you have both outputs ([14.04]("https://pastebin.com/w5VzfV0P") and [16.04]("https://pastebin.com/wfdvVNHN")) 
[*]software Powerstrip on windows 7 to copy its modelines which provides:
```
"2560x1080" 185,850 2560 2624 2688 2784 1080 1083 1093 1111 -hsync -vsync
``` 
[*]or software umc with:
```
Modeline "2560x1080x59.98"  181.250000  2560 2608 2640 2720  1080 1083 1087
1111  +HSync -VSync
``` 
[*]installed some random driver deleting pre-installed ones, which caused  a bricked system. 
[*]copied working xorg.conf and changing it from
```
Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection
```

to
```
Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
EndSection

``` 
[/LIST]

Here you have my [Xorg.log.0]("https://pastebin.com/9rnRY7cP") and [xorg.conf]("https://pastebin.com/8QSD07qK"), both from 14.04.

Any suggestions?
Thank you in advance!

---

### Post by Autodave on 2020-01-19
Since no one else has jumped in, let me suggest to you what I would try.  Download and burn the .iso of 18.04 to a USB stick or DVD.  Boot from that and see if you can get the resolution you want.  If you can, then it might be to do a clean install.

---

### Post by claudiocapobianchi on 2020-01-19
thanks for your reply, I installed several OSes on a spare hard drive (latest is Ubuntu mate 18.04), with lo luck.
I edited xorg.conf with modeline "Mode 0" but it simply doesn't work, black screen until it comes back to 1920x1080.

---

### Post by thehipho on 2020-01-19
What's the output of ```
xrandr -q
```

Try this in your xorg.conf:

Section "Monitor"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "PreferredMode" "2560x1080"
EndSection

---

### Post by claudiocapobianchi on 2020-01-22
from 14.04 (it uses DFP1:confused:):```
Screen 0: minimum 320 x 200, current 2560 x 1080, maximum 8192 x 8192
DFP1 connected 2560x1080+0+0 (normal left inverted right x axis y axis) 673mm x 284mm
   2560x1080      60.0*+
   1920x1080      50.0     60.0     59.9     50.0     60.1     60.0  
   1776x1000      50.0     59.9     50.0     60.0  
   1680x1050      60.0  
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      75.0     60.0  
   1440x900       60.0  
   1280x960       75.0     60.0  
   1152x864       60.0     75.0  
   1280x768       75.0     60.0  
   1280x720       50.0     60.0     59.9  
   1024x768       75.0     60.0  
   1152x648       50.0     59.9  
   800x600        75.0     60.3  
   720x480        60.0     59.9  
   640x480        75.0     60.0     59.9  
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 disconnected (normal left inverted right x axis y axis)

```

from 16.04 (instead it now  uses HDMI-0):```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 673mm x 284mm
   2560x1080     60.00 +
   1920x1080     60.00*   50.00    59.94  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  
DVI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 disconnected (normal left inverted right x axis y axis)



```

no way with "PreferredMode", aticonfig parts come from xorg on 14.04:
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
    
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option "ModelName" "Generic Autodetecting Monitor"
    Modeline     "2560x1080" 185.58 2560 2624 2688 2784 1080 1083 1093 1111 -hsync -vsync 
    Option      "PreferredMode" "2560x1080"
    Option        "DPMS" "true"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    Virtual 2560 1080
    EndSubSection
EndSection



```

with this xorg.conf, I can just boot to 1080.

---

### Post by thehipho on 2020-01-22
> 
Here you have my [Xorg.log.0]("https://pastebin.com/9rnRY7cP") and [xorg.conf]("https://pastebin.com/8QSD07qK"), both from 14.04.


You have the following errors in  [Xorg.log.0:]("https://pastebin.com/9rnRY7cP")

```
[     8.437] (EE) AIGLX error: failed to open  /usr/X11R6/lib64/modules/dri/fglrx_dri.so,  error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared  object file: No such file or directory]
 [     8.437] (EE) AIGLX error: failed to open  /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot  open shared object file: No such file or directory]
 [     8.437] (EE) AIGLX error: failed to open  /usr/X11R6/lib/modules/dri/fglrx_dri.so,  error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object  file: No such file or directory]

```

Which driver is loaded, can you post output of:
```
inxi -Gx

```

To find further errors  use:

```
grep WW /var/log/Xorg.0.log
```  and 
```
grep EE /var/log/Xorg.0.log
```


Also try these in xorg.conf?

Section "Monitor"
        Identifier   "HDMI-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option "ModelName" "Generic Autodetecting Monitor"
        /* Modeline     "2560x1080" 185.58 2560 2624 2688 2784 1080 1083 1093 1111 -hsync -vsync */
Option      "PreferredMode" "2560x1080"     
Option        "DPMS" "true"
EndSection

---

### Post by claudiocapobianchi on 2020-01-26
I am sorry for the late reply, I had to fix a python problem first that prevented me to run inxi -Gx:

```
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Juniper XT [Radeon HD 5770] bus-ID: 01:00.0 
           X.Org: 1.15.1 driver: fglrx Resolution: 2560x1080@60.0hz 
           GLX Renderer: AMD Radeon HD 5700 Series GLX Version: 4.5.13416 - CPC 15.201.1151 Direct Rendering: Yes
```

EE:
```
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     7.081] Initializing built-in extension MIT-SCREEN-SAVER
[     8.111] (EE) AIGLX error: failed to open /usr/X11R6/lib64/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib64/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     8.111] (EE) AIGLX error: failed to open /usr/lib64/dri/fglrx_dri.so, error[/usr/lib64/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
[     8.111] (EE) AIGLX error: failed to open /usr/X11R6/lib/modules/dri/fglrx_dri.so, error[/usr/X11R6/lib/modules/dri/fglrx_dri.so: cannot open shared object file: No such file or directory]
```

WW:
```
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     7.080] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     7.080] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     7.080] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     7.080] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     7.080] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     7.081] (WW) "xmir" is not to be loaded by default. Skipping.
[     7.116] (WW) Falling back to old probe method for fglrx
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:0:0) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:4:0) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:9:0) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:10:0) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:0) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:1) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:2) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:21:3) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:0) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@0:22:2) found
[     7.514] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[     7.524] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[     8.046] (WW) fglrx(0): Option "VendorName" is not used
[     8.046] (WW) fglrx(0): Option "ModelName" is not used
```

This my xorg as you suggested (replaced /* with #):
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "radeon"
    BusID       "PCI:1:0:0"
    
EndSection

Section "Monitor"
**Identifier "HDMI-0"**
Option "VendorName" "ATI Proprietary Driver"
Option "ModelName" "Generic Autodetecting Monitor"
#Modeline "2560x1080" 185.58 2560 2624 2688 2784 1080 1083 1093 1111 -hsync -vsync 
Option "PreferredMode" "2560x1080"
Option "DPMS" "true"
EndSection 

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    **Monitor    "HDMI-0"**
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    Virtual 2560 1080
    EndSubSection
EndSection


```

but it doesn't do the job, even commenting Option "PreferredMode" "2560x1080".

Thank you for you help!

---

### Post by thehipho on 2020-01-26
Try using the radeon drivers Kernel 4.x, should work with your videocard, instead fglrx.

This link provides more: [https://community.amd.com/thread/196514](https://community.amd.com/thread/196514)

---

### Post by claudiocapobianchi on 2020-01-31
well, if I read it correctly  they are talking about Crimson driver 15.302. So I downloaded it, but my Xorg is too new:
```
error: Detected X Server version 'XServer 1.20.5_64a' is not supported. Supported versions are X.Org 6.9 or later, up to XServer 1.10 (default:v2:x86_64:lib:XServer 1.20.5_64a:none:4.4.8-040408-generic:)
```

same issue trying to use [this]("https://github.com/llazzaro/catalyst_15.9_kernel4.4") to install Catalyst 15.9

Using DVI to HDMI converter didn't help either. Display doesn't even show POST.

---

### Post by thehipho on 2020-02-03
Hi, driver already enabled, you do not  need install it manually!

---

### Post by claudiocapobianchi on 2020-02-06
do you mean that shipped with ubuntu, right?
I was trying to install proprietary one, without success.
connected DVI to HDMI adapter again and selected Ubuntu 18.04 as default OS to boot (since monitor is black), but even when it is loaded, VGA does not send signals through DVI.

---

### Post by thehipho on 2020-02-06
> **claudiocapobianchi said:**
> do you mean that shipped with ubuntu, right?
I was trying to install proprietary one, without success.
connected DVI to HDMI adapter again and selected Ubuntu 18.04 as default OS to boot (since monitor is black), but even when it is loaded, VGA does not send signals through DVI.

Hi, If there is no proprietary driver for a graphics card, installing such a  driver will only prevent the Open Source driver from functioning  correctly. 
Please see this page: [https://help.ubuntu.com/community/VideoDriverHowto](https://help.ubuntu.com/community/VideoDriverHowto)

Then do:
```
sudo apt-get install xserver-xorg-video-nouveau
```

---

### Post by claudiocapobianchi on 2020-03-14
First of all, sorry for my absence.

Is nouveau suitable for nvidia cards?
Anyway, this is the output:
```
sudo apt-get install xserver-xorg-video-nouveau
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-video-nouveau : Depends: xorg-video-abi-23
                              Depends: xserver-xorg-core (>= 2:1.18.99.901)
E: Unable to correct problems, you have held broken packages.

```

After searching around I decided to risk and ran:

```
sudo apt-get install xserver-xorg linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libxatracker2 libxvmc1 linux-generic-hwe-18.04
  linux-headers-generic-hwe-18.04 linux-image-generic-hwe-18.04
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.15.0-72-generic linux-modules-4.15.0-72-generic
  linux-modules-extra-4.15.0-72-generic xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-input-libinput
Suggested packages:
  fdutils linux-doc-4.15.0 | linux-source-4.15.0 linux-tools
  linux-headers-4.15.0-72-generic xfonts-100dpi | xfonts-75dpi
Recommended packages:
  xserver-xorg-video-all xserver-xorg-input-wacom
The following packages will be REMOVED:
  xserver-xorg-core-hwe-18.04 xserver-xorg-hwe-18.04
  xserver-xorg-input-all-hwe-18.04 xserver-xorg-input-libinput-hwe-18.04
  xserver-xorg-input-wacom-hwe-18.04 xserver-xorg-video-all-hwe-18.04
  xserver-xorg-video-amdgpu-hwe-18.04 xserver-xorg-video-ati-hwe-18.04
  xserver-xorg-video-fbdev-hwe-18.04 xserver-xorg-video-intel-hwe-18.04
  xserver-xorg-video-nouveau-hwe-18.04 xserver-xorg-video-qxl-hwe-18.04
  xserver-xorg-video-radeon-hwe-18.04 xserver-xorg-video-vesa-hwe-18.04
  xserver-xorg-video-vmware-hwe-18.04
The following NEW packages will be installed:
  linux-image-4.15.0-72-generic linux-image-generic
  linux-modules-4.15.0-72-generic linux-modules-extra-4.15.0-72-generic
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-libinput
0 upgraded, 8 newly installed, 15 to remove and 246 not upgraded.
Need to get 55,2 MB of archives.
After this operation, 238 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 xserver-xorg amd64 1:7.7+19ubuntu7.1 [65,2 kB]
Err:2 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 xserver-xorg-core amd64 2:1.19.6-1ubuntu4.3
  404  Not Found [IP: 90.147.160.70 80]
Get:3 http://it.archive.ubuntu.com/ubuntu bionic/main amd64 xserver-xorg-input-libinput amd64 0.27.1-1 [33,2 kB]
Get:4 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 xserver-xorg-input-all amd64 1:7.7+19ubuntu7.1 [4.112 B]
Get:5 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-modules-4.15.0-72-generic amd64 4.15.0-72.81 [13,0 MB]
Get:6 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-image-4.15.0-72-generic amd64 4.15.0-72.81 [7.991 kB]
Get:7 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-modules-extra-4.15.0-72-generic amd64 4.15.0-72.81 [32,7 MB]
Ign:8 http://it.archive.ubuntu.com/ubuntu bionic-updates/main amd64 linux-image-generic amd64 4.15.0.72.74                                                                                                        
Err:8 http://security.ubuntu.com/ubuntu bionic-updates/main amd64 linux-image-generic amd64 4.15.0.72.74                                                                                                          
  404  Not Found [IP: 90.147.160.70 80]
Fetched 53,8 MB in 38s (1.415 kB/s)                                                                                                                                                                               
E: Failed to fetch http://it.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.19.6-1ubuntu4.3_amd64.deb  404  Not Found [IP: 90.147.160.70 80]
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_4.15.0.72.74_amd64.deb  404  Not Found [IP: 90.147.160.70 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Due to this error, after updating repository the above command didn't work anymore,  I had to remove manually first:

```
sudo apt-get purge xserver-xorg-hwe-18.04 linux-image-generic-hwe-18.04 xserver-xorg-legacy-hwe-18.04 xserver-xorg-core-hwe-18.04 xserver-xorg-video-intel-hwe-18.04
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  amd64-microcode intel-microcode iucode-tool libegl1-mesa libxatracker2 libxfont2 libxvmc1 linux-headers-generic-hwe-18.04 thermald x11-apps x11-session-utils xfonts-base xfonts-encodings xfonts-scalable
  xfonts-utils xinit xinput xserver-common
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic-hwe-18.04* linux-image-generic-hwe-18.04* ubuntu-mate-core* ubuntu-mate-desktop* xorg* xserver-xorg-core-hwe-18.04* xserver-xorg-hwe-18.04* xserver-xorg-input-all-hwe-18.04*
  xserver-xorg-input-libinput-hwe-18.04* xserver-xorg-input-wacom-hwe-18.04* xserver-xorg-legacy-hwe-18.04* xserver-xorg-video-all-hwe-18.04* xserver-xorg-video-amdgpu-hwe-18.04*
  xserver-xorg-video-ati-hwe-18.04* xserver-xorg-video-fbdev-hwe-18.04* xserver-xorg-video-intel-hwe-18.04* xserver-xorg-video-nouveau-hwe-18.04* xserver-xorg-video-qxl-hwe-18.04*
  xserver-xorg-video-radeon-hwe-18.04* xserver-xorg-video-vesa-hwe-18.04* xserver-xorg-video-vmware-hwe-18.04*
0 upgraded, 0 newly installed, 21 to remove and 299 not upgraded.
After this operation, 9.863 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 166751 files and directories currently installed.)
Removing linux-generic-hwe-18.04 (5.0.0.23.80) ...
Removing linux-image-generic-hwe-18.04 (5.0.0.23.80) ...
Removing ubuntu-mate-desktop (1.225) ...
Removing ubuntu-mate-core (1.225) ...
Removing xorg (1:7.7+19ubuntu7.1) ...
Removing xserver-xorg-hwe-18.04 (1:7.7+19ubuntu8~18.04.2) ...
Removing xserver-xorg-video-all-hwe-18.04 (1:7.7+19ubuntu8~18.04.2) ...
Removing xserver-xorg-video-amdgpu-hwe-18.04 (19.0.1-1~18.04.1) ...
Removing xserver-xorg-input-wacom-hwe-18.04 (1:0.36.1-0ubuntu1~18.04.1) ...
Removing xserver-xorg-video-ati-hwe-18.04 (1:19.0.1-0ubuntu1~18.04.1) ...
Removing xserver-xorg-video-radeon-hwe-18.04 (1:19.0.1-0ubuntu1~18.04.1) ...
Removing xserver-xorg-input-all-hwe-18.04 (1:7.7+19ubuntu8~18.04.2) ...
Removing xserver-xorg-input-libinput-hwe-18.04 (0.28.1-1~18.04.1) ...
Removing xserver-xorg-legacy-hwe-18.04 (2:1.20.4-1ubuntu3~18.04.1) ...
Removing xserver-xorg-video-fbdev-hwe-18.04 (1:0.5.0-1ubuntu1~18.04.1) ...
Removing xserver-xorg-video-intel-hwe-18.04 (2:2.99.917+git20171229-1ubuntu1~18.04.1) ...
Removing xserver-xorg-video-nouveau-hwe-18.04 (1:1.0.16-1~18.04.1) ...
Removing xserver-xorg-video-qxl-hwe-18.04 (0.1.5-2build2~18.04.1) ...
Removing xserver-xorg-video-vesa-hwe-18.04 (1:2.4.0-1~18.04.1) ...
Removing xserver-xorg-video-vmware-hwe-18.04 (1:13.3.0-2build1~18.04.1) ...
Removing xserver-xorg-core-hwe-18.04 (2:1.20.4-1ubuntu3~18.04.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
(Reading database ... 166417 files and directories currently installed.)
Purging configuration files for xserver-xorg-video-intel-hwe-18.04 (2:2.99.917+git20171229-1ubuntu1~18.04.1) ...
Purging configuration files for xserver-xorg-legacy-hwe-18.04 (2:1.20.4-1ubuntu3~18.04.1) ...
Purging configuration files for xserver-xorg-hwe-18.04 (1:7.7+19ubuntu8~18.04.2) ...
Purging configuration files for xserver-xorg-core-hwe-18.04 (2:1.20.4-1ubuntu3~18.04.1) ...
rm: cannot remove '/var/log/Xorg.*.log.old': No such file or directory
```

and then:
```
sudo apt-get install xserver-xorg linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-generic-hwe-18.04 x11-apps x11-session-utils xinit
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.15.0-88-generic linux-modules-4.15.0-88-generic linux-modules-extra-4.15.0-88-generic xserver-common xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput
  xserver-xorg-input-wacom xserver-xorg-legacy xserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-nouveau
  xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
Suggested packages:
  fdutils linux-doc-4.15.0 | linux-source-4.15.0 linux-tools linux-headers-4.15.0-88-generic xfonts-100dpi | xfonts-75dpi firmware-amd-graphics xserver-xorg-video-r128 xserver-xorg-video-mach64
  firmware-misc-nonfree
The following NEW packages will be installed:
  linux-image-4.15.0-88-generic linux-image-generic linux-modules-4.15.0-88-generic linux-modules-extra-4.15.0-88-generic xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput
  xserver-xorg-input-wacom xserver-xorg-legacy xserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-nouveau
  xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware
The following packages will be upgraded:
  xserver-common
1 upgraded, 20 newly installed, 0 to remove and 298 not upgraded.
Need to get 56,5 MB/56,6 MB of archives.
After this operation, 253 MB of additional disk space will be used.
```

and checked with 
```
sudo apt-get install --install-recommends xserver-xorg-video-nouveau
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-nouveau is already the newest version (1:1.0.15-2).
xserver-xorg-video-nouveau set to manually installed.

```

Always getting 1920*1080.

---

### Post by claudiocapobianchi on 2020-03-21
Installed 18.04 on virtualbox (14.04 as host), and guess what, it does run @2560*1080 out of the box.
Here are timings (output from xrandr is VGA-1, even if physical cable is HDMI as always):
 ```
xvidtune- show
"2560x1080" 230.09 2560 2720 2992 3424 1080 1083 1093 1120 -hsync +vsync
```
same output from xrandr.

My xvidtune from 14.04 instead:
```
"2560x1080"   185.58   2560 2624 2688 2784   1080 1083 1093 1111 -hsync -vsync
```
A modeline with this timigs in 18.04 didn't fix it.
I noticed that my monitor ratio was set on: "wide" (i.e. showing 1920*1080 stretched), my hopes of solve by changing it to "1:1" faded away within seconds.
Fun fact, the ratio on monitor menu becomes greyed out once fglrx is loaded.

---

