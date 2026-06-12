---
title: "s2disk does not work"
date: 2007-04-10
forum: Hardware &amp; Laptops
---

### Post by sam.wan on 2007-04-10
Dear all,

     I installed Kubuntu 7.04 on a brand new laptop with Core 2 Duo and NVIDIA Geforce Go 7300. I upgraded to latest kernel 2.6.20-14-generic and nvidia driver 1.0-9755 and made below configuration:

      o add agp=off  to kernel line in /boot/grub/menu.lst
      o add "options nvidia NVreg_Mobile=1" to /etc/modprobe.d/options
      o add  'Option  "NvAGP" "1"' to  /etc/X11/xorg.conf  
 
     but s2disk does not always work.  s2disk may succeed for the 1st time after reboot aud then it will fail just after the screen goes black.
     
 Below is the content of /proc/driver/nvidia/registry
-------------------------------------
VideoMemoryTypeOverride: 1
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3           ( don't know why NvAGP is still 3 )
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
SoftEDIDs: 1
Mobile: 1
ResmanDebugLevel: 4294967295
FlatPanelMode: 0
DevicesConnected: 0
RmLogonRC: 1
VbiosFromROM: 0
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UseCPA: 4294967295
DetectPrimaryVga: 1
SaveVBios: 0
EnableBrightnessControl: 0
PanelPWMFrequency: 1018
PanelBrightnessLimits: 65280
UseVBios: 1
RMEdgeIntrCheck: 1
------------------------------------------------------------
        I don't know what's wrong. Any pointer or help would be very appreciated.
  
    Thanks and regards

Sam

---

### Post by zoltan140 on 2007-04-22
o add  'Option  "NvAGP" "1"' to  /etc/X11/xorg.conf  
 
try to add --> Option "NoLogo" = "True" to  /etc/X11/xorg.conf

---

