---
title: "Boots well, SSH works well, but black screen"
date: 2015-04-15
forum: Hardware
---

### Post by Namnamseo on 2015-04-15
My laptop has i5-4200U with Intel HD Graphics 4400, no external VGAs.

On my  laptop, Ubuntu wouldn't show anything but black screen until I use nomodeset at boot.
I installed and have used Ubuntu always with nomodeset turned on.
But as it cannot use the hardware graphic acceleration, it was really slow.

At first glance, I thought the system wouldn't boot up properly without nomodeset.
The screen was all black, but it flickered a little when I alter between tty1 and tty7(Ctrl+Alt+F1/F7).
(I didn't know if it actually worked, as there was no video.)
So, one day, I presumed the system was properly booted, logged into tty1, typed sudo shutdown 0 -r,
and typed in the password. Surprisingly, it really rebooted!

Then I continued my experiment. With SSH, I found X server and desktop manager was properly running.
From looking at logs in /var/log/Xorg.0.log , I also found it recognized the graphic card and the screen pretty well.

```
[FONT=Courier]root@A34X:~# xrandr --display :0.0 :
[/FONT][FONT=Courier]Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767[/FONT]
[FONT=Courier]eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 282mm x 165mm[/FONT]
[FONT=Courier]   1920x1080      60.0*+   59.9     40.0  [/FONT]
[FONT=Courier]   1680x1050      60.0     59.9  [/FONT]
[FONT=Courier]   1600x1024      60.2  [/FONT]
[FONT=Courier]   1400x1050      60.0  [/FONT]
[FONT=Courier]   1280x1024      60.0  [/FONT]
[FONT=Courier]   1440x900       59.9  [/FONT]
[FONT=Courier]   1280x960       60.0  [/FONT]
[FONT=Courier]   1360x768       59.8     60.0  [/FONT]
[FONT=Courier]   1152x864       60.0  [/FONT]
[FONT=Courier]   1024x768       60.0  [/FONT]
[FONT=Courier]   800x600        60.3     56.2  [/FONT]
[FONT=Courier]   640x480        59.9  [/FONT]
[FONT=Courier]HDMI1 disconnected (normal left inverted right x axis y axis)[/FONT]
[FONT=Courier]VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/FONT]
```
From above, it sees the screen and actually drawing at 1920x1080. So I can't understand why it's not drawing.
I currently have no monitors avail to test HDMI. But I will be able to in a few days.
I'm not that good at reading logs, but logs like Xorg.0.log or gdm/* doesn't seem strange. Just a few fails loading module "fbdev" and "modesetting".
But if you need anything from the logs, please ask me.
I copied a few fresh log files only containing logs just after the boot or GDM restart.

---

