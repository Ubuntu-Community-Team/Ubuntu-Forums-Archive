---
title: "Conky flickers but only when a window is over it"
date: 2008-08-06
forum: General Help
---

### Post by timzak on 2008-08-06
I notice that when I have an app open full screen so that it covers my conky display, I see it flickering through my open app.  But when I have a windowed app that is not touching the conky display, I don't see any flicker at all.  The flicker I do see with full screen apps corresponds with the update interval of 5 seconds.  Here's my output file, can someone help me fix this?  Yes, I am using compiz.

Thanks

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
background no #Transparent background.

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 5

# Minimum size of text area
minimum_size 260 5

# Draw shades?
draw_shades no

# Draw borders around graphs
draw_graph_borders no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
xftfont Eurostile:size=9
xftalpha 0.7
#font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 23

# stuff after 'TEXT' will be formatted on screen

#${font arial black:size=8}LOCAL: $font${addr eth0} $alignr ${color} ${font arial #black:size=8}EXTERNAL: $font${execi 14400 wget -O - http://whatismyip.org/ | tail}${color}

TEXT
${font arial black:size=11}${color orange}SYSTEM ${color}${font arial black:size=10}INFORMATION${color orange} ${hr 2}$color$font
${color orange}${font openlogos:size=27}T$color${font}
${voffset -38}${goto 40}$sysname  $kernel on $machine${voffset -18}
${voffset 16}${goto 40}$nodename  ${font arial black:size=8}UP: $font$uptime ${voffset -18}
${voffset 10}${font arial black:size=28}${time %e}$font ${voffset -17}${time %A, }${time %B} ${time %G}
${voffset -2}${goto 65}${font arial black:size=9} ${time %I:%M %p}
${font arial black:size=11}${color orange}CPU ${color}${font arial black:size=10}INFORMATION${color orange} ${hr 2}$color$font
${font arial black:size=8}USAGE (AVG): $font${cpu cpu0}%
${cpugraph cpu0 FFFFFF FFFFFF}
${font arial black:size=8}CORE 1: $font${cpu cpu1}% $alignr ${font arial black:size=8}CORE 2: $font${cpu cpu2}%
${cpugraph cpu1 25,140 FFFFFF FFFFFF}  $alignr${cpugraph cpu2 25,140 FFFFFF FFFFFF}
${font arial black:size=8}TOP 3 PROCESSES:${offset 5}$font${top name 1} ${alignr -4}${top cpu 1} % 
${offset 122}$font${top name 2}${alignr}${top cpu 2} %
${offset 122}$font${top name 3}${alignr}${top cpu 3} %
${font arial black:size=11}${color orange}MEMORY ${color}${font arial black:size=10}INFORMATION${color orange} ${hr 2}$color$font
${font arial black:size=8}RAM: $font$memperc% ${alignr}$mem ${font arial black:size=8}/ $font$memmax 
${membar 4}
${font arial black:size=8}SWAP: $font$swapperc% ${alignr}$swap ${font arial black:size=8}/ $font$swapmax 
${swapbar 4}
${font arial black:size=8}TOP 5 PROCESSES:${offset 5}$font${top_mem name 1}${alignr -4}${top mem 1} % 
${offset 122}$font${top_mem name 2}${alignr}${top mem 2} %
${offset 122}$font${top_mem name 3}${alignr}${top mem 3} %
${offset 122}$font${top_mem name 4}${alignr}${top mem 4} %
${offset 122}$font${top_mem name 5}${alignr}${top mem 5} %
${font arial black:size=11}${color orange}DISK ${color}${font arial black:size=10}INFORMATION${color orange} ${hr 2}$color$font
${font arial black:size=8}VOLUME${goto 116}TYPE${goto 180}%FREE${alignr 1}SIZE$font
${font arial black:size=8}ROOT:$font${goto 120}${fs_type /}${goto 190}${fs_free_perc /}%${alignr}${fs_size /}
${fs_bar 4 /}$color
${font arial black:size=8}HOME:$font${goto 120}${fs_type /home/}${goto 190}${fs_free_perc /home/}%${alignr 1}${fs_size /home/}
${fs_bar 4 /home/}$color
${font arial black:size=8}MEDIA:$font${goto 120}${fs_type /media/disk-1}${goto 190}${fs_free_perc /media/disk-1}%${alignr 1}${fs_size /media/disk-1}
${fs_bar 4 /media/disk-1}$color
${font arial black:size=8}BACKUP:$font${goto 120}${fs_type /media/disk}${goto 190}${fs_free_perc /media/disk}%${alignr 1}${fs_size /media/disk}
${fs_bar 4 /media/disk}$color
${font arial black:size=11}${color orange}NETWORK ${color}${font arial black:size=10}INFORMATION${color orange} ${hr 2}$color$font

${font arial black:size=8}DOWN: $font$color${downspeed eth0} k/s ${alignr}${font arial black:size=8}UP: $font${upspeed eth0} k/s
${downspeedgraph eth0 25,140 FFFFFF FFFFFF} ${alignr}${upspeedgraph eth0
25,140 FFFFFF FFFFFF}$color
${font arial black:size=8}TOTAL: $font${totaldown eth0} ${alignr}${font arial black:size=8}TOTAL: $font${totalup eth0}
${color orange}${hr 2}$color
```

---

### Post by easybake on 2008-08-06
[QUOTE=timzak;5534667]I notice that when I have an app open full screen so that it covers my conky display, I see it flickering through my open app.  But when I have a windowed app that is not touching the conky display, I don't see any flicker at all.  The flicker I do see with full screen apps corresponds with the update interval of 5 seconds.  Here's my output file, can someone help me fix this?  Yes, I am using compiz.

Thanks

I would try replacing all of your own_window listings and only using these ones.
```
own_window yes
own_window_hints undecorated, sticky, below, skip_pager, skip_taskbar
own_window_transparent yes
```

It might have something to do with the fact that when you use _type override it ignores you WM. Also when you use override your _hints line is useless.

---

### Post by timzak on 2008-08-06
Thanks, but if I disable the override line, then my mouse wheel no longer switches workspaces while the mouse is over the conky display.  I need this, as I size my windows so that the only desktop space showing is the conky display.

---

