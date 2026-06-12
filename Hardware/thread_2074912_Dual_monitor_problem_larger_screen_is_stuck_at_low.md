---
title: "Dual monitor problem: larger screen is stuck at lower than maximum resolution"
date: 2012-10-22
forum: Hardware
---

### Post by ZgOu7 on 2012-10-22
I have two monitors attached to my computer. My problem is that the largest available resolution in System Settings, Displays, is less than the maximum that the larger monitor is capable of, so the picture quality is not as good as it should be. 

I have been using Ubuntu for about two years, so I am fine with general use, but don't understand very much about using the terminal, except simple commands.

I am running Ubuntu 12.10 as a dual boot with Windows 7. 

I have recently installed a new graphics card and monitor so that I can have two monitors. Before this I just had one VGA socket in the back of the computer. 

The new graphics card is a GForce GT610. When I run

lspci | grep VGA 

in the terminal, I get 

01:00.0 VGA compatible controller: NVIDIA Corporation Device 104a (rev a1)

The monitors are as follows:

1) Compaq Q2022A  20" LCD  1600x900 resolution  

2) BenQ G950  19" Monitor  1366x768 resolution  

When I first installed the new graphics card card, the screens were very flickery, so I installed the Nvidia driver from System Settings, Additional Drivers. Now it is perfectly usable, but the larger monitor is not at its maximum resolution, and hence the picture is not as clear as it should be. 

(When I opened up Windows, it installed the drivers and then I was able to choose the maximum resolution of 1600x1900 for the Compaq monitor in Nvidia settings, and it works fine.)

When I enter 

xrandr

in the terminal, I get: 

Screen 0: minimum 8 x 8, current 2726 x 768, maximum 16384 x 16384
DVI-I-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0 +
   1360x768       60.0*    59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   512x384       120.0  
   400x300       144.4  
   320x240       120.1  
VGA-0 connected 1366x768+1360+0 (normal left inverted right x axis y axis) 410mm x 230mm
   1366x768       59.8*+
   1280x720       75.0     60.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)

The Compaq is plugged into the DVI socket on the new card via an adapter, and the BenQ is plugged straight into the VGA socket on the new card.

Here is a screenshot of the nvidia-settings X Server Display Configuration for the Compaq screen:

[IMG]http://i1128.photobucket.com/albums/m481/high56/ubuntu%20query%2022%20October%202012/nvidia-settingsCompaq1.png[/IMG]

The resolution shown is the highest in the drop-down menu. Here is a similar screenshot, but for the BenQ monitor:

[IMG]http://i1128.photobucket.com/albums/m481/high56/ubuntu%20query%2022%20October%202012/nvidia-settingsBenQ1.png[/IMG]

The highest resolution available for the Compaq in System Settings, Displays is 1360x768.

---

### Post by ZgOu7 on 2012-10-23
After hours and hours of messing around, I've finally solved this problem. All I did was to swap the plugs round so that the larger screen was plugged directly into the VGA socket, and the smaller screen is plugged into the DVI-I via the adapter. It works! I'm so pleased. I don't know why it works, but it does.

---

