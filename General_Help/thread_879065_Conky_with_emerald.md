---
title: "Conky with emerald"
date: 2008-08-03
forum: General Help
---

### Post by Sub101 on 2008-08-03
Hi, i have conky working as i want it but would like it to use my emerald border on the left hand side. I can achieve this using ```
own_window_type normal
```
however then when i press the Desktop button Conky is removed from view as well.
So what im after is a way to use my theme with Conky or just a solid left hand border on Conky but still using either Desktop or Override.

My conky file is 
```
 Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type desktop
on_window_transparent
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

maximum_width 143 5
minimum_size 143 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 4

# border margins
border_margin 2

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

#own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 2
	gap_y 20

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 0}${color white}Uptime: ${color }$uptime
${offset 0}${color white}kernel: ${color }$kernel
${offset 0}${color white}battery:${color } ${battery}
${offset 0}${color white}Temp: ${acpitemp} C
${offset 0}${color white}Hard Drive Temp: ${hddtemp /dev/sda}
${offset 0}${color white}CPU:${color } $cpu%
${offset 0}${cpugraph 20,130 cccccc ffffff}
${offset 0}${color white}load: ${color }$loadavg
${offset 0}${color white}processes: ${color }$processes  
${offset 0}${color white}running: ${color }$running_processes

${offset 0}${color white}top cpu time:
${offset 0}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 0}${color white} ${top name 2}${top cpu 2}
${offset 0}${color white} ${top name 3}${top cpu 3}
${offset 0}${color white} ${top name 4}${top cpu 4}

${offset 0}${color white}top mem:
${offset 0}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 0}${color white} ${top_mem name 2}${top_mem mem 2}
${offset 0}${color white} ${top_mem name 3}${top_mem mem 3}
${offset 0}${color white} ${top_mem name 4}${top_mem mem 4}

${offset 0}${color white}ram:
${color }$memperc% $mem/$memmax
${offset 0}${membar 3,100}
${offset 0}${color white}swap:
${color }$swapperc% $swap/$swapmax
${offset 0}${swapbar 3,100}
${offset 0}${color white}root:
${color }${fs_free /}/${fs_size /}
${offset 0}${fs_bar 3,100 /}
${offset 0}${color white}net:
${offset 0}${color} wlan signal: ${color }${wireless_link_qual_perc wlan0}%
${offset 0}${color} ip: ${addr wlan0}
${offset 0}${color}up: ${color }${upspeed wlan0} k/s
${offset 0}${upspeedgraph wlan0 20,130 000000 ffffff}
${offset 0}${color}down: ${color }${downspeed wlan0}k/s${color}
${offset 0}${downspeedgraph wlan0 20,130 000000 ffffff}
${color white}Connections ${alignr} ${color white}
${tcp_portmon 32768 61000 rhost 0 | cut -c 10-} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${color maroon}SYSTEM LOGS ${hr 2}$color
${color maroon}Messages:$color
${execi 10 /usr/bin/tail -n 4 /var/log/messages | cut -c 10-}
$
${color maroon}Security:$color
${execi 10 /usr/bin/tail -n 4 /var/log/auth.log | cut -c 10-}
```

Any help would be greatly appreciated. Thanks for your time.

---

### Post by kaivalagi on 2008-08-03
No idea, but if you have a hard job figuring it out, try the IRC channel #conky on irc.freenode.net. I am sure someone there will be able to give you a straight answer.

If you do find an answer please post it here :) It would be interesting to know whether it is at all possible...it puts another slant on conky customisation!

---

### Post by easybake on 2008-08-03
> **Sub101 said:**
> Hi, i have conky working as i want it but would like it to use my emerald border on the left hand side. I can achieve this using 
however then when i press the Desktop button Conky is removed from view as well.
So what im after is a way to use my theme with Conky or just a solid left hand border on Conky but still using either Desktop or Override.
Any help would be greatly appreciated. Thanks for your time.

Go into CCSM. Under General Options>General Tab  uncheck the 'hide skip taskbar windows'. Your conky will stay on your desktop as long as you have ```
own_window_hints skip_taskbar
```

---

