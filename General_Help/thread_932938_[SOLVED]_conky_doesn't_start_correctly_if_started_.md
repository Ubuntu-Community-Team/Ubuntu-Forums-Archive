---
title: "[SOLVED] conky doesn't start correctly if started in sessions"
date: 2008-09-28
forum: General Help
---

### Post by NovaAesa on 2008-09-28
Hi, I have my conky set up file going okay now, so I decided to put conky into the sessions startup so that it would start every time I turn my computer on. It's doesn't seem to be working that well though. It appears above everything else, like the bar at the top. Here are some screenshots:

Here's what it looks like when it starts up from sessions when my computer starts:
[img]http://i277.photobucket.com/albums/kk50/novaaesa/Screenshot-4.png[/img]

Here's what it looks like when it starts up form using the command line:
[img]http://i277.photobucket.com/albums/kk50/novaaesa/Screenshot-1-1.png[/img]

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
update_interval 0.5

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


${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}    ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}    ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}    ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}    ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
```

Anyone know how to fix this?

---

### Post by easybake on 2008-09-29
> **NovaAesa said:**
> Hi, I have my conky set up file going okay now, so I decided to put conky into the sessions startup so that it would start every time I turn my computer on. It's doesn't seem to be working that well though. It appears above everything else, like the bar at the top. Here are some screenshots


Anyone know how to fix this?

You just need a sleep script because it is drawing the conky window out of order. 
```

#!/bin/bash

sleep 20 &&
conky
```

Remember to make it executable and to also use this to replace your original sessions entry.

---

### Post by NovaAesa on 2008-10-02
Thank you easybake, worked a charm =]

---

