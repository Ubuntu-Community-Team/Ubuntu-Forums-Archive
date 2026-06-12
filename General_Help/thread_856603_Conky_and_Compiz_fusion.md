---
title: "Conky and Compiz fusion"
date: 2008-07-11
forum: General Help
---

### Post by Fixman on 2008-07-11
After much, much, suffering, I made my Conky to work on Compiz. However, I note that, if I have a window at fullscreen (like this FF window right now), every 20 seconds or so Conky blinks on the screen. It may not see so, but its VERY DISTURBING. Can anybody help me?

By the way,
[INDENT]**·** I know how to turn off Compiz[/INDENT]
[INDENT]**·** I know how to kill conky[/INDENT]
[INDENT]**·** I know that I must make a script that sleeps some secs and then calls conky (and so conky stays on my desktop except for these cases)[/INDENT]


And here goes my .conkyrc file..

```


# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
xftfont Terminus:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 5 5
maximum_width 500

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 40

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes


# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no
#Note: doesn't work in conky 1.2 =(

TEXT
${alignc}${color #0077ff}INFO

${color #888888}martin@$nodename ${color #CCCCCC}- ${color #888888}$machine
${color #888888}$sysname $kernel 
${color #888888}UpTime: ${color }$uptime
${color #0077ff}${time %a-%d/%b/%y}${alignr}${time %k:%Mh}
${color}${hr 2}

${alignc}${color #0077ff}CPU

${voffset 5}${color #888888}Freq: ${color}2 x ${freq_dyn}MHz
${color #888888}${cpugraph 20 160 ff0000 0000ff}
${color }$cpu% ${color #ff0000}${cpubar 4}
${voffset 5}${color #888888}Load: ${color }$loadavg
${color #888888}Temp:${color #ff0000} ${i2c temp 1} ${i2c temp 2} ${color}${i2c temp 3} C
${color #888888}Fan:${color }  ${i2c fan 1} RPM
${color #888888}Int:${alignr}${color }  ${i2c in 0}  ${i2c in 1}  ${i2c in 2}  ${i2c in 3}  ${i2c in 4}  A 
${alignr}${color }${i2c in 5}  ${i2c in 6}  ${i2c in 7}  ${i2c in 8}  A 
${color #888888}Processes: ${color}$processes${alignr}${color #888888}Runing: ${color}$running_processes
${color white}${stippled_hr 2 1}

${color #0077ff}${alignc}MEMORY

${voffset 5}${color #10DFED}RAM: ${color } $memperc%${alignr}$mem${color #888888}/$memmax
${color #10DFED}${membar 4,160}
${color #10DFED}SWAP: ${color }$swapperc%${alignr}$swap${color #888888}/$swapmax
${color #10DFED}${swapbar 4,160}
${voffset 5}${color #888888}Name${alignr}RAM     CPU% 
${color #B60000}${top name 1}${alignr}${top mem 1}    ${top cpu 1}
${color #D17D00}${top name 2}${alignr}${top mem 2}    ${top cpu 2}
${color #B2B200}${top name 3}${alignr}${top mem 3}    ${top cpu 3}
${color #187B18}${top name 4}${alignr}${top mem 4}    ${top cpu 4}
${color #3A9191}${top name 5}${alignr}${top mem 5}    ${top cpu 5}
${color white}${stippled_hr 2 1}

${color #0077ff}${alignc}DISK DRIVES

${voffset 5}${color #E2E22D}HOME:${alignr}${color }${fs_free /}${color #888888}/${fs_size /}
${color #E2E22D}${fs_bar 4,160 /}
${if_mounted /media/Vista}${color #E2E22D}Vista:${alignr}${color }${fs_free /media/Vista}${color #888888}/${fs_size /media/Vista}
${color #E2E22D}${fs_bar 4,160 /media/Vista}
$endif${color #888888}Disk I/O: $color$diskio
${voffset -5}${color white}${stippled_hr 2 1}

${color #0077ff}${alignc}NETWORK

${voffset 5}${color #888888}Up: ${color #55B350}${upspeed eth0}k/s${alignr}${color #55B350} ${totalup eth0}
${color #888888}Down: ${color #55B350}${downspeed eth0}k/s${alignr}${color #55B350} ${totaldown eth0}
${color #888888}${downspeedgraph eth0 160BE9 00ff00 300}
${color #888888}Total connecions:${alignr}$color ${tcp_portmon 1 65535 count}
${color #888888}Out: $color${tcp_portmon 32768 61000 count}${alignr}${color #888888}In: $color${tcp_portmon 1 32767 count}
${alignc}${color #0077ff}IP: $color${execi 10000 curl www.whatismyip.com/automation/n09230945.asp}
${voffset -5}${color white}${stippled_hr 2 1}

${color #0077ff}${alignc}AMAROK

${color #CC6600}${alignc}${execi 10 dcop amarok player artist}
${alignc}${execi 10 dcop amarok player album}
${alignc}${execi 10 dcop amarok player title} 
${alignc}${execi 5 dcop amarok player currentTime}/${execi 10 dcop amarok player totalTime}
${color #CC6600}Bitrate:${execi 10 dcop amarok player bitrate}kbps${alignr}Vol:${execi 10 dcop amarok player getVolume}%


```

---

### Post by Fixman on 2008-07-14
Help!

---

### Post by Execute_Method on 2008-07-14
You may need to load the DBE module in your xorg.conf. It is said to reduce flickering.

```
sudo gedit /etc/X11/xorg.conf
```

then in the "module" section:

```
Load    "dbe"
```

---

### Post by Fixman on 2008-07-14
> **Execute_Method said:**
> You may need to load the DBE module in your xorg.conf. It is said to reduce flickering.

```
sudo gedit /etc/X11/xorg.conf
```

then in the "module" section:

```
Load    "dbe"
```

Its arleady loaded.

---

### Post by Execute_Method on 2008-07-14
> **Fixman said:**
> Its arleady loaded.

OK, I loaded your config on my desk and it doesn't flicker at all, which means that more than likely it's not your conky config. Can you provide more info as to your setup (ie. compiz effects loaded, video card, WM, etc.). Also, post your xorg.conf. and xorg.0.log

---

### Post by Fixman on 2008-07-14
> **Execute_Method said:**
> OK, I loaded your config on my desk and it doesn't flicker at all, which means that more than likely it's not your conky config. Can you provide more info as to your setup (ie. compiz effects loaded, video card, WM, etc.). Also, post your xorg.conf. and xorg.0.log

```

Enhaced Zoom Desktop, Negative, Desktop Cube, Expo, Rotate Cube, Animations, Cube Reflection, Fading windows, Paint Fire on Screen, Reflection, Water Effect, Window Decoration, Wobbly Windows, Screenshot, Window Previews, the 4 iamge loading effects, Crash Handler, Cube Caps, DBus, GLib, INotify, Mouse Position Polling, Regex matching, resize info, Scale Addons, Scale iwndow Tile Filter, Session Management, Video Playback, Workaruonds, Application Switcher, Extra WM actions, Place Windows, Put, Resize Window, Ring switcherm Scale, Shift switcher, Move Window

```

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
        Load            "dbe"
EndSection

```


I have an NVidia Geforce 8600 GS.

---

### Post by Execute_Method on 2008-07-14
Try changing:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_type override

```

to

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type desktop
own_window_hints below
```

in your conkyrc

---

