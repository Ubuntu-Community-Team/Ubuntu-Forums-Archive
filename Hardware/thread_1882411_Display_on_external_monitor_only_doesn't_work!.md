---
title: "Display on external monitor only doesn't work!"
date: 2011-11-17
forum: Hardware
---

### Post by kumardeepu on 2011-11-17
Hello everyone, 

In Ubuntu 11.10 (Oneiric) when I try to have display only on the external monitor it doesn't work. Both my laptop's and monitor screen goes blank and after 15 seconds or so it falls back to the display on both screens (extended). 

I wonder if anyone else is having the same problem as me. I tried to google around and go through our forum but so far I have not found any solution. 

I have Dell latitude E6400 and my graphic card is: VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Please let me know if you have any ideas how to solve this. 

thanks in advance!

---

### Post by kumardeepu on 2011-11-23
No comments??

---

### Post by matt_symes on 2011-11-23
Hi

Have you tried using xrandr with the --primary switch to set your external monitor as the primary output. You may get some feedback as to why it's failing.

You can also use xrandr wit the -off switch to disable your laptop screen.

Kind regards

---

### Post by kumardeepu on 2011-11-23
First of all thank you so much for your reply. I am sorry but I didn't understand your comments. Could you please elaborate for me. do I use CLI or use the GUI from the display settings option?

---

### Post by kumardeepu on 2011-11-23
Also I tried with xrandr but I don't know how to put the options you asked me to as nothing happens when I say xrandr --primary switch.

---

### Post by matt_symes on 2011-11-23
Hi

Open a terminal and type

```
xrandr
```

Post back the results.

Kind regards

---

### Post by mlaughlin on 2011-11-23
I have the same Chipset and I have an issue where my max resolution is 1280x800

When I run xrandr I get:


user@the-test:~$ xrandr
Can't open display



user@the-test:~$ xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
Can't open display

---

### Post by mlaughlin on 2011-11-23
user@the-test:~$ sudo lshw -C display
  *-display:0
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f6c00000-f6ffffff memory:e0000000-efffffff ioport:ef98(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f6b00000-f6bfffff

---

### Post by matt_symes on 2011-11-24
Hi

@[mlaughlin]("http://ubuntuforums.org/member.php?u=1499796")

Try

```
DISPLAY=:0 xrandr
```

Copy and past the entire output back here.

Kind regards

---

### Post by kumardeepu on 2011-11-29
Sorry that I took so long to reply. 

This is the output of my xrandr:

```
[ajeet]@[oldleaf][~]: xrandr
Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 8192 x 8192
LVDS1 connected 1280x800+0+250 (normal left inverted right x axis y axis) 303mm x 189mm
   1280x800       60.1*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1680x1050+1280+0 (normal left inverted right x axis y axis) 459mm x 296mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

```

---

### Post by kumardeepu on 2011-11-29
This is the output of "DISPLAY=:0 xrandr

```
[ajeet]@[oldleaf][~]: DISPLAY=:0 xrandr
Screen 0: minimum 320 x 200, current 2960 x 1050, maximum 8192 x 8192
LVDS1 connected 1280x800+0+250 (normal left inverted right x axis y axis) 303mm x 189mm
   1280x800       60.1*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 connected 1680x1050+1280+0 (normal left inverted right x axis y axis) 459mm x 296mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)

```

---

### Post by matt_symes on 2011-11-29
Hi

HDMI eh ? I know this has been problematic for some people.

Let's try this.

To set the primary screen as the external screen

```
xrandr --output HDMI1 --primary
```
To turn the laptop screen off.

```
xrandr --output LVDS1 --off
```

To reset everything.

```
xrandr --auto
```

Post back results.

Kind regards

---

### Post by kumardeepu on 2011-11-29
When I put this "xrandr --output HDMI1 --primary" in my terminal, nothing happens. No output, nothing.

At the same time when I try

xrandr --output LVDS1 --off

my extended desktop becomes primary and the my laptop screen is switched off. This is what I wanted but through the display settings it was not possible. 

Do you think that I would have to write this command every time if I want to have output only on the extended desktop or can I change the settings of the "display" settings? 

Thanks for your kind help.

---

### Post by matt_symes on 2011-11-29
Hi

> **kumardeepu said:**
> When I put this "xrandr --output HDMI1 --primary" in my terminal, nothing happens. No output, nothing.

That is correct. You will not see any output. It just makes you HDMI output the primary output.

> At the same time when I try

xrandr --output LVDS1 --off

my extended desktop becomes primary and the my laptop screen is switched off. This is what I wanted but through the display settings it was not possible. 

That's good. That's what i expected to happen.

> 
Do you think that I would have to write this command every time if I want to have output only on the extended desktop or can I change the settings of the "display" settings? 

You can write a very simple script and run that each time you want to change the display. That way you will not have to type it in every time.

From the terminal, type (or copy and paste) this

```
echo "xrandr --output LVDS1 --off" >> ~/Desktop/switch_to_external.sh && chmod 755 switch_to_external.sh
```

Run the file generated by the command above on your desktop to switch to the external monitor only.

```
echo "xrandr --auto" >> ~/Desktop/switch_to_normal.sh && chmod 755 switch_to_normal.sh
```

Run the above to set it back.

> Thanks for your kind help.

I am not sure why it's not working when you use the GUI. Maybe something in the logs may point to the problem.

Try to change it as you were before. When the screen kick back to both being on, open a terminal and type

```
tail -n30 /var/log/Xorg.0.log
```

Post back the results. Also post back the results of this command

```
tail -n 30 ~/.xsession-errors
```

Kind regards

---

### Post by kumardeepu on 2011-11-29
Here are the outputs: 
```
[ajeet]@[oldleaf][~]: tail -n30 /var/log/Xorg.0.log
[  5898.661] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[  5898.661] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  5898.661] (**) Dell WMI hotkeys: always reports core events
[  5898.661] (**) Dell WMI hotkeys: Device: "/dev/input/event5"
[  5898.661] (--) Dell WMI hotkeys: Found keys
[  5898.661] (II) Dell WMI hotkeys: Configuring as keyboard
[  5898.661] (**) Option "config_info" "udev:/sys/devices/virtual/input/input5/event5"
[  5898.661] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[  5898.661] (**) Option "xkb_rules" "evdev"
[  5898.661] (**) Option "xkb_model" "pc105"
[  5898.661] (**) Option "xkb_layout" "us"
[  5899.205] (II) intel(0): EDID vendor "AUO", prod id 21316
[  5899.205] (II) intel(0): Printing DDC gathered Modelines:
[  5899.205] (II) intel(0): Modeline "1280x800"x0.0   70.50  1280 1328 1360 1426  800 803 809 823 +hsync -vsync (49.4 kHz)
[  5900.528] (II) intel(0): EDID vendor "AUO", prod id 21316
[  5900.529] (II) intel(0): Printing DDC gathered Modelines:
[  5900.529] (II) intel(0): Modeline "1280x800"x0.0   70.50  1280 1328 1360 1426  800 803 809 823 +hsync -vsync (49.4 kHz)
[  5903.273] (II) intel(0): EDID vendor "AUO", prod id 21316
[  5903.273] (II) intel(0): Printing DDC gathered Modelines:
[  5903.273] (II) intel(0): Modeline "1280x800"x0.0   70.50  1280 1328 1360 1426  800 803 809 823 +hsync -vsync (49.4 kHz)
[  5903.534] (II) intel(0): EDID vendor "AUO", prod id 21316
[  5903.534] (II) intel(0): Printing DDC gathered Modelines:
[  5903.534] (II) intel(0): Modeline "1280x800"x0.0   70.50  1280 1328 1360 1426  800 803 809 823 +hsync -vsync (49.4 kHz)
[  5903.829] (II) intel(0): EDID vendor "AUO", prod id 21316
[  5903.829] (II) intel(0): Printing DDC gathered Modelines:
[  5903.829] (II) intel(0): Modeline "1280x800"x0.0   70.50  1280 1328 1360 1426  800 803 809 823 +hsync -vsync (49.4 kHz)
[  5904.941] (II) intel(0): EDID vendor "AUO", prod id 21316
[  5904.941] (II) intel(0): Printing DDC gathered Modelines:
[  5904.941] (II) intel(0): Modeline "1280x800"x0.0   70.50  1280 1328 1360 1426  800 803 809 823 +hsync -vsync (49.4 kHz)
[  5905.709] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm

```

and 

```
[ajeet]@[oldleaf][~]: tail -n 30 ~/.xsession-errors
Setting Update "run_command_terminal_key"
Setting Update "left_button"
Setting Update "right_button"
Setting Update "open_durations"
Setting Update "close_effects"
Setting Update "close_durations"
Setting Update "close_matches"
Setting Update "minimize_effects"
Setting Update "minimize_durations"
Setting Update "fullscreen_visual_bell"
Setting Update "icon_size"
** (process:3991): DEBUG: Telepathy Indicator started
WARN  2011-11-29 18:58:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/files does not exist
WARN  2011-11-29 18:58:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/files does not exist
WARN  2011-11-29 18:58:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/music does not exist
WARN  2011-11-29 18:58:55 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/music does not exist
WARN  2011-11-29 18:58:56 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-11-29 18:58:56 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/commands does not exist
WARN  2011-11-29 18:58:56 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method InfoRequest proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-11-29 18:58:56 unity.glib.dbusproxy GLibDBusProxy.cpp:255 Cannot call method SetActive proxy /com/canonical/unity/lens/applications does not exist
WARN  2011-11-29 18:58:57 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-installed.svg: Error opening file: No such file or directory
WARN  2011-11-29 18:58:57 unity.iconloader IconLoader.cpp:509 Unable to load contents of file:///usr/share/icons/unity-icon-theme/places/svg/category-available.svg: Error opening file: No such file or directory
** (nm-applet:3837): DEBUG: foo_client_state_changed_cb
** (nm-applet:3837): DEBUG: foo_client_state_changed_cb
** (nm-applet:3837): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:3837): DEBUG: foo_client_state_changed_cb

** (process:4271): WARNING **: zeitgeist-datahub.vala:218: Unable to get name "org.gnome.zeitgeist.datahub" on the bus!
Created new window in existing browser session.
** (deja-dup-monitor:5039): DEBUG: monitor.vala:221: Automatic backups disabled.  Not scheduling a backup.

```

Thanks,

---

### Post by matt_symes on 2011-12-01
Hi

I cannot see anything in your logs that would stop you changing the resolution. Without being at your PC and looking through it, i am not really sure what to suggest.

At least you have a work around.

Kind regards

---

