---
title: "conky covers icons"
date: 2008-08-04
forum: General Help
---

### Post by Technoviking on 2008-08-04
I love conky, but I hate when it covers my desktop icons. I have tried disabling own_window_hints sticky in the conkyrc with no luck. Any other ideas on how I can fix this.

Ubuntu 8.04.1 running compiz.

conkyrc:
```
# conky configuration
# edited by kaivalagi

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
#xftfont Bitstream Vera Sans Mono:size=9
#xftfont Terminus:size=9
xftfont Liberation Mono:size=9
#xftfont Liberation Mono:size=9
#xftfont DS9cr:size=9
#xftfont Zekton:style:Italics:size=10

# Text alpha when using Xft
xftalpha 0.8

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 300 0
#maximum_width 300

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

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 13
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

# Add spaces to keep things from moving about?  This only affects certain object
s.
use_spacer left

# colours
color1 white
# light blue
color2 6892C6
# orange
#E77320
color3 FC8820
# green
color4 78BF39
# red
color5 CC0000
# tan
color6 CBC0A2

text_buffer_size 2048

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen


TEXT
${color4}${font openlogos:size=24}u$color${font}
${font arial black:size=9}${voffset -38}${goto 40}$sysname  $kernel on $machine$
{voffset -18}
${font arial black:size=9}${voffset 16}${goto 40}${exec cat /etc/issue.net} on $
nodename ${font arial black:size=9}UP: $font$uptime ${voffset -18}


${color6}Current CPU usage & Temp:${alignr}${color1}${cpu}%${color6} - ${color1}
${acpitemp}C ${color6}/${color1}${acpitempf}F
${color6}Load average:${color1} $loadavg${alignr}${color6}Freq: ${color1}${freq_
dyn} Mhz

${color6}CPU Usage         ${alignr}PID      CPU%     MEM%
${color1} ${top name 1}${alignr}${top pid 1}   ${top cpu 1}   ${top mem 1}
${color1} ${top name 2}${alignr}${top pid 2}   ${top cpu 2}   ${top mem 2}
${color1} ${top name 3}${alignr}${top pid 3}   ${top cpu 3}   ${top mem 3}

${color6}Mem Usage
${color1} ${top_mem name 1}${alignr}${top_mem pid 1}   ${top_mem cpu 1}   ${top_
mem mem 1}
${color1} ${top_mem name 2}${alignr}${top_mem pid 2}   ${top_mem cpu 2}   ${top_
mem mem 2}
${color1} ${top_mem name 3}${alignr}${top_mem pid 3}   ${top_mem cpu 3}   ${top_
mem mem 3}

${color6}RAM Usage:${color1} $mem/$memmax - $memperc% $membar
${color6}Swap Usage:${color1} $swap/$swapmax - $swapperc% ${swapbar}
${color6}Processes:${color1} $processes  ${color6}${alignr}Running:${color1} $ru
nning_processes ${color6}

${color6}Hard disks:
 ${color6}/boot   ${color1}${fs_used /boot}/${fs_size /boot} ${fs_bar /boot}
 ${color6}/root   ${color1}${fs_used /}/${fs_size /} ${fs_bar /}
 ${color6}/home   ${color1}${fs_used /home}/${fs_size /home} ${fs_bar /home}

${color6}Wireless Networking:
 ${color6}ESSID: ${color1}${wireless_essid wlan0} ${alignr}${color6}Local IP: ${
color1}${addr wlan0}
 ${color6}Bitrate: ${color1}${wireless_bitrate wlan0}${alignr}${color6}Signal ST
R: ${color1}${wireless_link_qual_perc wlan0}%
 ${color6}Total Download: ${color1}${totaldown wlan0}${alignr}${color6}Total Upl
oad: ${color1}${totalup wlan0}
 ${color6}Download Speed: ${color1}${downspeed wlan0} k/s${alignr}${color6}Uploa
d Speed: ${color1}${upspeed wlan0} k/s
 ${color1}${downspeedgraph wlan0 15,150 ff0000 0000ff} $alignr${color1}${upspeed
graph wlan0 15,150 0000ff ff0000}

${color6}Wired Networking:
 ${color6}Local IP: ${color1}${addr eth0} ${color6}
 ${color6}Total Download: ${color1}${totaldown eth0}${alignr}${color6}Total Uplo
ad: ${color1}${totalup eth0}
 ${color6}Download Speed: ${color1}${downspeed eth0} k/s${alignr}${color6}Upload
 Speed: ${color1}${upspeed eth0} k/s
 ${color1}${downspeedgraph eth0 15,150 ff0000 0000ff} $alignr${color1}${upspeedg
raph eth0 15,150 0000ff ff0000}

```

---

### Post by easybake on 2008-08-04
> **Mike said:**
> I love conky, but I hate when it covers my desktop icons. I have tried disabling own_window_hints sticky in the conkyrc with no luck. Any other ideas on how I can fix this.


If you use own_window_type override it ignores the own_window_hints list anyway. 

This is what I use. It makes a transparent conky, where icons can not be placed in the same area as conky. This just uses the default own_window_type so I dont even have the line in my RC.

```
own_window yes
own_window_hints undecorated, sticky, below, skip_pager, skip_taskbar
own_window_transparent yes
```

---

