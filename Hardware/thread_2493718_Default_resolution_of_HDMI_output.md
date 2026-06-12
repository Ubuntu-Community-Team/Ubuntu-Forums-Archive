---
title: "Default resolution of HDMI output"
date: 2023-12-22
forum: Hardware
---

### Post by agarding on 2023-12-22
Hi,

I have a laptop with HDMI output running Xubuntu. Mirroring the laptop's own display to a TV works out of the box except for one thing: The default output resolution is the native resolution of the TV, which is double the FullHD. Because of this, after plugging in the cable, I can only use the top left quarter of the TV. When I change the output resolution of HDMI to FullHD, whole TV display area becomes useful.

Is there a way to make 1920x1080 the default output resolution of HDMI and to get rid of the need to change it manually everytime I plug in the TV?

---

### Post by TheFu on 2023-12-22
> **agarding said:**
>  
Is there a way to make 1920x1080 the default output resolution of HDMI and to get rid of the need to change it manually everytime I plug in the TV?

Yes.  If you use X11 (sometimes called Xorg), you can setup the output for specific GPU ports to be specific resolutions using **xrandr**.  Running that command alone will show which resolutions and frequencies are supported on which ports.
For example, I have a VGA 15-pin port and an HDMI port on my GPU.  I want two different resolutions. xrandr tells me the names of those GPU ports for my GPU+driver is VGA-1 and HDMI-1. From the list from each of those in the xrandr output, with no options, I see approved resolutions and pick the native resolution for each of my monitors:
```

xrandr  --output [COLOR="#008000"]VGA-1[/COLOR] --mode  1920x**1200**
xrandr  --output [COLOR="#008000"]HDMI-1[/COLOR] --mode  1920x**1080**

```

I run this before login, but after X11 has started. [https://linuxconfig.org/how-to-configure-your-monitors-with-xrandr-in-linux](https://linuxconfig.org/how-to-configure-your-monitors-with-xrandr-in-linux) and [https://askubuntu.com/questions/793089/set-default-resolution-system-wide](https://askubuntu.com/questions/793089/set-default-resolution-system-wide)  has more details.

None of this works with Wayland, but I suspect there's an equivalent tool for that as well, I just don't know it. Depending on the DE used, you can probably find a GUI tool for this. I know Gnome has one.  Don't know about XFCE, Mate, Cinnamon, or others, sorry.

---

### Post by #&amp;thj^% on 2023-12-22
Along with what TheFu suggests just add the proper line to "~/.profile"
ie:
```
xrandr --current
Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
[COLOR="#0000FF"]HDMI-0 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 698mm x 392mm[/COLOR]
   1920x1080     60.00*+  59.94    29.97    23.98  
   1680x1050     59.95  
   1440x900      59.89  
   1360x768      60.02  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1280x800      59.81  
   1280x720      60.00    60.00    59.94    29.97    23.98  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32  
   720x480       59.94  
   640x480       75.00    72.81    59.94    59.93  
DP-4 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080    120.21*+

```
and:
```
 tac .profile
xrandr  --output HDMI-0 --mode  1920x1080*
export QT_QPA_PLATFORMTHEME="qt5ct"

```
Just ignore the QT line serves no purpose for this/your thread.

---

### Post by agarding on 2023-12-22
The xrandr command does the job when I give the command, but when I unplug and replug the cable, the default setting hasn't change and I have to give the command again. Am I wrong assuming that the default I set should remain until I restart X?

---

### Post by #&amp;thj^% on 2023-12-22
> **agarding said:**
> Am I wrong assuming that the default I set should remain until I restart X?

Or until you pull the plug and replug, then it "will" revert to it's default setting, just as it should do.

---

### Post by agarding on 2023-12-22
> **1fallen said:**
> Or until you pull the plug and replug, then it "will" revert to it's default setting, just as it should do.

Ok, I see. The point of my original question was if I could somehow change that default setting.

---

### Post by #&amp;thj^% on 2023-12-22
> **agarding said:**
>  The point of my original question was if I could somehow change that default setting.

I thought we did that....did you add the ~./profile in your /home/user directory?
If that is not good enough, and your fairly savvy on fixing your system when it won't boot correctly or at all.
Then have a look at this: [https://bbs.archlinux.org/viewtopic.php?id=260982](https://bbs.archlinux.org/viewtopic.php?id=260982)

EDIT: Dang I just don't use many GUI's anymore but "Arandr" might be useful for your needs.
```
install arandr
```
Right click on your HDMI screen, tick the resolution you want "1920x1080"
Next hit Apply and Save, you should have it set now.
Nvidia drivers can interfere with that setting, just a heads up if you have a nVidia card.

---

