---
title: "Cannot get my laptop to use built in screen with two external ones"
date: 2022-03-27
forum: Hardware
---

### Post by Yuval_Khalifa on 2022-03-27
Hi,

I have a Dell G3 15" running Ubuntu 20.04.4 LTS. It has two external monitors attached to it: one via HDMI and the other via DP and they all worked just fine - If they were connected I could use all three and if I disconnected them I could use only the built-in laptop screen. Due to some unrelated issue I had decided to re-install Ubuntu on it on a separate partition and now things are not working as expected. If I connect the two monitors I can use ONLY the external monitors and the laptop screen is blacked out, even if I disconnect the external monitors the built in is still blacked out. If I run the command "sudo prime-select intel" and then reboot, it would use ONLY the built in monitor and won't show anything on the two external ones. 


Some information (currently it is using ONLY the external monitors):
```
~ sudo lshw -c video
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
       resources: irq:180 memory:82000000-82ffffff memory:70000000-7fffffff memory:80000000-81ffffff ioport:4000(size=128) memory:83080000-830fffff
  *-display
       description: VGA compatible controller
       product: UHD Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: driver=i915 latency=0
       resources: iomemory:600-5ff iomemory:400-3ff irq:179 memory:6022000000-6022ffffff memory:4000000000-400fffffff ioport:5000(size=64) memory:c0000-dffff

```
```
~  xrandr                  Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 65535 x 65535
HDMI-3 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm
   1920x1080     60.00*+  50.00    59.94  
   1680x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x800      59.81  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94  
DP-3 connected primary 1920x1080+1920+0 (normal left inverted right x axis y axis) 527mm x 296mm
   1920x1080     60.00*+
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94
```  




Any thoughts?

---

### Post by Yuval_Khalifa on 2022-03-27
Hi. 

I'm happy to say that I have solved my own problem :)
I changed the server ubuntu uses to download updates from my regional server (Israel) in the "Software & Updates" screen to the main server and then I ran ```
sudo apt install nvidia-driver-470
```…and it seems to work now without any issues. Thanks a lot anyway.

---

### Post by DuckHook on 2022-03-27
Glad to hear you solved it. I have marked your thread "solved", using the thread tools menu at the top of the thread.

---

