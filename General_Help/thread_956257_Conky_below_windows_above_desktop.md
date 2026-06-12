---
title: "Conky below windows above desktop"
date: 2008-10-23
forum: General Help
---

### Post by tynen on 2008-10-23
Is there a way to get Conky to be on the same level as the desktop? It is below all windows that I have open but whenever I try to interact with the desktop or open a file that's on the desktop Conky is above the arrow on the desktop. Is there anyway to fix this? here is my Conky config file and a screen shot of what it does.

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
own_window_background yes


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 100 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
```

---

### Post by cammin on 2008-10-23
change
own_window_type override

to
own_window_type desktop
or
own_window_type normal

---

### Post by easybake on 2008-10-23
> **tynen said:**
> Is there a way to get Conky to be on the same level as the desktop? It is below all windows that I have open but whenever I try to interact with the desktop or open a file that's on the desktop Conky is above the arrow on the desktop. Is there anyway to fix this? here is my Conky config file and a screen shot of what it does.

If cammin's way doesn't work:

Does this only happen when you have conky start at start-up. For instance, does the problem still occur when you kill conky and launch it from terminal?

If it does, than you simply need a sleep script for conky, which you can find [Here]("http://ubuntuforums.org/showpost.php?p=5997415&postcount=2").

---

### Post by tynen on 2008-10-23
No it happens all the time. I'll try that config edit. I already have Conky sleeping but thank you :)

---

### Post by cl0ckwork on 2008-10-23
try setting the option

```
maximum_width [highlight]xxx[/highlight]
```

change [highlight]xxx[/highlight] to any desired width that it wont expand bigger than.

and just wondering why do you have everything with a 240 offset?
that could be the main cause of it being so wide

---

### Post by tynen on 2008-10-24
Honestly I don't even know what the offset does. What is a better setting for it?

---

### Post by cl0ckwork on 2008-10-24
all offset does is move the line X amount of spaces right if positive and left if negative.

there would be no harm in just taking all the offsets out, since they all are the same value

---

### Post by cl0ckwork on 2008-10-24
i worked on your script a bit, took out the offsets and set some color variables.

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
own_window_background yes


# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 100 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20

#color set
color1 slate grey
color2 lightgrey

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${color1}${time %a, } ${color }${time %e %B %G}
${color1}${time %Z,    }${color }${time %H:%M:%S}
${color1}UpTime: ${color }$uptime
${color1}Kern:${color }$kernel
${color1}CPU:${color } $cpu% ${acpitemp}C
${cpugraph 20,130 000000 ffffff}
${color1}Load: ${color }$loadavg
${color1}Processes: ${color }$processes  
${color1}Running:   ${color }$running_processes

${color1}Highest CPU:
${color #ddaa00} ${top name 1}${top_mem cpu 1}
${color2} ${top name 2}${top cpu 2}
${color2} ${top name 3}${top cpu 3}
${color2} ${top name 4}${top cpu 4}

${color1}Highest MEM:
${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${color2} ${top_mem name 2}${top_mem mem 2}
${color2} ${top_mem name 3}${top_mem mem 3}
${color2} ${top_mem name 4}${top_mem mem 4}

${color1}MEM:  ${color } $memperc% $mem/$memmax
${membar 3,100}
${color1}SWAP: ${color }$swapperc% $swap/$swapmax
${swapbar 3,100}

${color1}ROOT:    ${color }${fs_free /}/${fs_size /}
${fs_bar 3,100 /}
${color1}HOME:  ${color }${fs_free /home}/${fs_size /home}
${fs_bar 3,100 /home}
${color1}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${fs_bar 3,100 /mnt/slack}
${color1}NET: 
${color}Up: ${color }${upspeed eth0} k/s
${upspeedgraph eth0 20,130 000000 ffffff}
${color}Down: ${color }${downspeed eth0}k/s${color}
${downspeedgraph eth0 20,130 000000 ffffff}
```

just did a little house cleaning :lolflag:

---

