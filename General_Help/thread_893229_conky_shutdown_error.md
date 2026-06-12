---
title: "conky shutdown error"
date: 2008-08-18
forum: General Help
---

### Post by pBeseda on 2008-08-18
Conky looks great, works great, love it. When I shutdown the computer, the first thing I see is an error pop-up telling me:

these windows do not support "save current setup" and will have to be restarted manually next time you log in


It lists conky, gives me the option to close the program and proceeds to shutdown. :confused: I searched the forums and couldn't find anyone with a similar error so I thought I'd ask. Anyone seen this happen before or know how I might fix it? Thanks

---

### Post by pBeseda on 2008-08-18
bump?

---

### Post by ronjouch on 2008-11-28
Hello,

I have this too. :confused:
Googling  [conky "save current setup"]("http://www.google.com/search?q=conky+%22save+current+setup%22") doesn't help a lot...

Ubuntu 8.04.1 up to date.
And here is my .conkyrc:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

on_bottom yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right

# use a modern fonts system
use_xft yes

# Update interval in seconds
update_interval 2.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font DejaVu Sans Mono
xftfont Monospace:size=8
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 5

# border width
border_width 5

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

# Text alignment, other possible values are commented
alignment top_right

# Gap between borders of screen and text
gap_x 5
gap_y 5

# stuff after ‘TEXT’ will be formatted on screen
# ${cpugraph cpu1 25,100 78af78 a3a3a3}${alignr}${cpugraph cpu2 25,100 78af78 a3a3a3}
TEXT
$color
${color orange}sys ${hr 2}$color
$nodename on $sysname $kernel

${color orange}cpu ${hr 2}$color
${cpu cpu1}%, ${freq_g 1}, ${hwmon temp 1}C ${alignr}${cpu cpu2}%, ${freq_g 2}, ${hwmon temp 3}C
${color black}${cpugraph cpu1 25,100 000000 ffa500}${alignr}${cpugraph cpu2 25,100 000000 ffa500}$color
${color #e5e5e5}${top name 1}${alignr}${top pid 1}  ${top cpu 1}  ${top mem 1}
${color #c4c4c4}${top name 2}${alignr}${top pid 2}  ${top cpu 2}  ${top mem 2}
${color #a3a3a3}${top name 3}${alignr}${top pid 3}  ${top cpu 3}  ${top mem 3}
${color #999999}${top name 4}${alignr}${top pid 4}  ${top cpu 4}  ${top mem 4}

${color orange}ram/disk ${hr 2}$color
ram : $memperc% ${membar 6}$color
swap: $swapperc% ${swapbar 6}$color
root: ${fs_free_perc /}% ${fs_bar 6 /}$color
home: ${fs_free_perc /home}% ${fs_bar 6 /home}

${color orange}nw ${hr 2}$color
eth0 (${addr eth0}, ${execi 14400 wget -O - http://whatismyip.org/ | tail})${alignr}
${color black}${downspeedgraph eth0 25,140 000000 ffa500} ${alignr}${upspeedgraph eth0 25,140 000000 ffa500}$color
dwn: ${downspeed eth0}kBps, ${totaldown eth0}  ${alignr}up: ${upspeed eth0}kBps, ${totalup eth0}

${color orange}log ${hr 2}$color
${execi 30 tail -n5 /var/log/messages | fold -w50}
```

---

