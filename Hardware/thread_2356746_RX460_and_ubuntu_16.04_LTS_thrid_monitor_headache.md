---
title: "RX460 and ubuntu 16.04 LTS thrid monitor headache"
date: 2017-03-26
forum: Hardware
---

### Post by Kuro_Kitsune on 2017-03-26
I am sorry if I have posted this in the wrong area. I very very Rarely make fourm posts as I can normally find most solutions with some googling. However this rx 460 has been the bane of my existince when it comes to ubuntu. I finally resintalled 16.04 LTS (as i was running 16.10 with too new of a kernel ) got the driver working, Although i had some artifacts on the second screen that cleared up later. So now everything is working driver wise (no screen tearing in firefox, 3D accleration ect was even playing arma 3) however. I have three monitors. 1 HDMI, 1 DVI , and 1 DisplayPort. the HDMI and DVI displays work just fine showing up in the display settings as on and set to 1080p and they work as seprate screens. However the Display port monitor only mirrors the HDMI monitor and shows as off in the display settings. trying to switch it on just causes the settings app to lock up and then give a timeout error. I can't seem to get the display port monitor to run at the correct resolution nor as a seprate display. In windows this works fine. The insault to injury is this new AMDGPU-PRO Drivers doesn't have any AMD app for managing things. Not even sure where to start with this issue. Thank you for your time! 

Also note the HDMI and DVI montiors are 1080p monitors and the DisplayPort is a Dell monitor with a res of 1280x1024

also the output of xrandr is

```
kain@kain-Inspiron-3650:~$ xrandr
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 16384 x 16384
DisplayPort-0 connected (normal left inverted right x axis y axis)
   1280x1024     60.02 +  75.02  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08  
HDMI-A-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 880mm x 490mm
   1920x1080     60.00*+  50.00    59.94    24.00    23.98  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1600x900      60.00  
   1280x1024     75.02  
   1440x900      59.90  
   1360x768      60.02  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    60.00    59.94  
   720x400       70.08  
DVI-D-0 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 497mm x 292mm
   1920x1080     60.00*+
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
   720x400       70.08 
``` 
```
kain@kain-Inspiron-3650:~$ lspci | grep 'VGA'
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 67ef (rev cf)
```
```
kain@kain-Inspiron-3650:~$ dpkg -l amdgpu-pro
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                            Version              Architecture         Description
+++-===============================-====================-====================-====================================================================
ii  amdgpu-pro                      16.40-348864         amd64                Meta package to install amdgpu Pro components.
```

---

### Post by Kuro_Kitsune on 2017-03-31
bump

---

