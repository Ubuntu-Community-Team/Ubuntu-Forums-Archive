---
title: "Laptop Internal &amp; External Screen Problems"
date: 2021-01-20
forum: Hardware
---

### Post by UrbanSlayer on 2021-01-20
I have an Elitebook 840 G5 and am using a HP Ultraslim docking station with it and 1 external monitor via Displayport.  On a clean and new install of Kubuntu 20.10 (with default drivers etc), I am having issues with screens working/not working depending on the lid being open or closed.

I have amended the KDE monitor settings to turn off suspend when the lid is closed, on power.

Laptop screen - eDP-1
External monitor - DP-2-2

_Docked/Lid Closed (on boot) -_ 

If the laptop is docked and the screen closed, on boot, I see the GRUB menu and then the initial KDE loading screen, but then the external screen goes to sleep.  If I open the laptop lid, nothing happens.  The laptop is up, as I can SSH in.  If I do the following - 

```
export DISPLAY=:0.0 && xrandr
```

I get this - 

```
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
eDP-1 connected (normal left inverted right x axis y axis)
   15360x8640    15.83    28.85  
   7680x4320     15.83    59.99    59.99    59.99  
   5120x2880     59.99    59.99  
   4096x2304     59.99    59.98  
   3840x2160     60.00    60.01    59.98    59.97  
   3200x1800     59.96    59.94  
   2880x1620     59.96    59.97  
   2560x1600     59.99    59.97  
   2560x1440     59.99    59.99    59.96    59.95  
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   2048x1152     59.99    59.98    59.90    59.91  
   1920x1200     59.88    59.95  
   1920x1080     60.01    59.97    59.96    59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-2-1 disconnected (normal left inverted right x axis y axis)
DP-2-2 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
   1920x1080     60.00*+
   1680x1050     59.88  
   1400x1050     59.95  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00  
   1024x768      75.03    60.00  
   832x624       74.55  
   800x600       75.00    60.32    56.25  
   640x480       75.00    59.94  
   720x400       70.08  
```

The mode settings for the laptop screen are incorrect.  If I boot with the lid open, the modes are correct.  I have added an xorg file 10-monitor.conf with the following in to add the correct mode (this is based on the contents of the Xorg.0.log when it boots with lid open) - 

```
Section "Monitor"
    Identifier "eDP-1"
    Modeline "1920x1080_120.1" 280.00  1920 1944 1992 2120  1080 1090 1095 1100 -hsync -vsync
    Option "PreferredMode" "1920x1080_120.1"
EndSection
```

If I then, in the same ssh session attempt to activate the external screen (DP-2-2), nothing happens.  I can run the command - 

```
xrandr --output DP-2-2 --auto
```  OR ```
xrandr --output DP-2-2 --mode 1920x1080 --rate 60
```
Nothing happens at all, no message, the screen doesn't do anything etc.

If I then try (with the lid open) - 

```
xrandr --output eDP-1 --auto
```

I get - 

```
xrandr: Configure crtc 1 failed
```

But then the external screen comes up and works as expected.  If I undock the laptop with the lid open, the internal screen does not activate, but redocking will bring the external screen back.

_Docked/Lid Open (on boot) - _

Everything works as expected.  The correct modes for the laptop screen are detected, I can undock and dock as necessary, all works.  

I have checked /etc/systemd/logind.conf, and the defaults look correct.

My Xorg log has been uploaded here - [https://pastebin.com/fEtQQj7Z](https://pastebin.com/fEtQQj7Z)

I can workaround the problem by leaving the screen open on boot, but this doesn't happen on an older, Elitebook 820 G1, which is using a Intel HD4400 GPU instead of the newer Intel HD 620 (Iris) GPU in the 840, so I know it *should* work.

Any assistance would be greatly appreciated!

---

### Post by UrbanSlayer on 2021-01-21
Small update.  I had set KDE to auto login, but turned this off to test to see if SDDM did display, as the external screen disabled on the KDE splash screen.

After a reboot, SDDM did display, but the mouse pointer did not come up and when moving it, there was some serious screen distortion.  I moved to a different TTY, and then back to the primary and the mouse was there, and I was able to login.  This didn't resolve the laptop screen itself not being detected correctly however (didn't expect it to), but potentially indicates this is a KDE issue on login?

I need to test a few more times with SDDM to see if the mouse issue is still present, and try and workout why that is as well.

---

