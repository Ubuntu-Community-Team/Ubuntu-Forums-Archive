---
title: "ASUS P5LD2 SE Temperatures?"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by e30ernest on 2007-06-20
I have an Intel Pentium D processor on an ASUS P5LD2 SE motherboard.  Everything seems to be working fine but after installing conky, I found out that my cpu temperatures can not be displayed.  Is there a way to fix this?  I know my board can read CPU temps because I have done it in Window$.

I tried lm-sensors but unfortunately it didn't work.  I'd really like to watch my cpu temperature.  Thanks in advance for your help!

---

### Post by ukripper on 2007-06-20
post your conkyrc here if ubuntu detects your temp conky will too

Can you also post output of following:

```
cat /proc/acpi/thermal_zone/THRM/temperature
```

---

### Post by e30ernest on 2007-06-20
Thanks for the reply!

Here is the output of cat /proc/acpi/thermal_zone/THRM/temperature:

```
cat: /proc/acpi/thermal_zone/THRM/temperature: No such file or directory
```

As for my conky config:

```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
sda1:  ${fs_free_perc /media/sda1}%   ${fs_bar 6 /media/sda1}$color
sdc1:  ${fs_free_perc /media/sdc1}%   ${fs_bar 6 /media/sdc1}
sdb1:  ${fs_free_perc /media/sdb1}%   ${fs_bar 6 /media/sdb1}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}
```

---

### Post by e30ernest on 2007-06-20
Update:
I think I got lm-sensors to work.  Here is my output:

```
w83627ehf-isa-0290
Adapter: ISA adapter
VCore:     +1.21 V  (min =  +0.00 V, max =  +1.74 V) 
in1:      +12.46 V  (min = +13.41 V, max = +12.94 V) ALARM
AVCC:      +3.36 V  (min =  +4.08 V, max =  +3.57 V) ALARM
3VCC:      +3.36 V  (min =  +4.08 V, max =  +3.02 V) ALARM
in4:       +1.70 V  (min =  +1.98 V, max =  +2.04 V) ALARM
in5:       +1.63 V  (min =  +2.04 V, max =  +1.91 V) ALARM
in6:       +5.22 V  (min =  +6.53 V, max =  +4.86 V) ALARM
VSB:       +3.36 V  (min =  +3.95 V, max =  +4.08 V) ALARM
VBAT:      +3.30 V  (min =  +4.02 V, max =  +4.08 V) ALARM
in9:       +1.66 V  (min =  +2.03 V, max =  +2.04 V) ALARM
Case Fan:    0 RPM  (min =   47 RPM, div = 128) ALARM
CPU Fan:  3750 RPM  (min =    0 RPM, div = 2)
Aux Fan:     0 RPM  (min =    0 RPM, div = 128)
fan5:        0 RPM  (min =    0 RPM, div = 8)
Sys Temp:    +41°C  (high =   -65°C, hyst =    -1°C)   ALARM
CPU Temp:  +42.0°C  (high = +80.0°C, hyst = +75.0°C)  
AUX Temp:  +43.5°C  (high = +80.0°C, hyst = +75.0°C)  

```

Now all that remains is making that work with conky. :)

---

### Post by e30ernest on 2007-06-20
Got it to work by replacing:

```
#${acpitemp}
```

with

```
${execi 90 sensors | grep "CPU Temp:" | cut -c12-16 ;}C
```

The temperature (or I think) is now displayed.  Did I do this correctly?

---

### Post by ukripper on 2007-06-20
> **e30ernest said:**
> Got it to work by replacing:

```
#${acpitemp}
```

with

```
${execi 90 sensors | grep "CPU Temp:" | cut -c12-16 ;}C
```

The temperature (or I think) is now displayed.  Did I do this correctly?


exec 90 would mean your conky will be updated every 90 sec. if you want it to update every sec than you have to replace it by execi 1

---

### Post by ukripper on 2007-06-20
My conkyrc you can find it on this thread:
 link is here - [http://ubuntuforums.org/showthread.php?t=281865&page=28](http://ubuntuforums.org/showthread.php?t=281865&page=28)

---

### Post by e30ernest on 2007-06-21
Thanks fixed it!  Now the only issue I have to fix is that on of the bars showing the remaining space for the drive "sdc1" is misaligned:

[IMG]http://i51.photobucket.com/albums/f361/e30ernest/Screenshot.png[/IMG]

---

### Post by Bassofondale on 2008-03-14
Hi all, you can post the conky.conf for p5ld2 please?

Ciao

---

