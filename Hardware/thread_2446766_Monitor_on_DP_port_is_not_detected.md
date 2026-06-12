---
title: "Monitor on DP port is not detected"
date: 2020-07-06
forum: Hardware
---

### Post by st62791ev on 2020-07-06
[COLOR=#242729][FONT=Arial]It seems to be a common issue but I could not find a solution.[/FONT][/COLOR]

[LIST]
[*]I just clean installed Ubuntu 20.04 Desktop and updated it with the "Software & updates" tool.
[*]PC:HP ProDesk 400 G4 Desktop-Mini-PC
[*]The monitor attached on one of the DisplayPort ports: HP EliteDisplay E243
[*]Video card (lspci -k | grep -A 2 -i "VGA") :
[/LIST]
[FONT=courier new]00:02.0 VGA compatible controller: Intel Corporation 8th Gen Core Processor Gaussian Mixture Model
    DeviceName: Onboard IGD
    Subsystem: Hewlett-Packard Company 8th Gen Core Processor Gaussian Mixture Model[/FONT]

[LIST]
[*]output of command seen on other related questions/answers :
[/LIST]
[FONT=courier new]xrandr --query
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 16384 x 16384
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-3 connected primary 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+
   1920x1080     60.00  
   1600x1200     60.00  
   1680x1050     59.95  
   1280x1024     60.02  
   1280x960      60.00  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
   720x400       70.08  
HDMI-3 disconnected (normal left inverted right x axis y axis)
[/FONT]

[LIST]
[*]The configuration was working out-of-the-box on Windows 10 (on another disk) and Debian 10 Buster (on an usb stick live install).
[*]I could not find anything obviously wrong in the dmesg output.
[*]I also tried to change grub to add nomodeset it does not make any difference.
[*]I tried switching to lightDM (and back to gdm, +reboot) but no difference noticed.
[*]I also did an update with sudo apt update ; sudo apt upgrade but no change.
[*]I upgraded the kernel to the last stable (5.6.16) and booted on but without effect.
[/LIST]
[FONT=inherit][COLOR=#242729][FONT=Arial]Then I tried reverting to Windows 10 (by switching to the old drive) or Debian 10 (by booting on the live usb stick) but no monitor plug on the DP port is found anymore.

I suppose for the some reason the DP ports have been fried during the Ubuntu install, hence there is probably no solution. 

But just in case someone has some tricks to resuscitate the DP port, I thought I should post.
if more info is needed please let me know.

[/FONT][/COLOR]


[/FONT]

---

