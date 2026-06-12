---
title: "Conky doesnt appear after 8.10 update"
date: 2008-11-09
forum: General Help
---

### Post by Venom_Man on 2008-11-09
Now that i have upgraded to ibex conky does not appear. i had it working before i updated but now it says its running but it is not appearing ontop of my desktop. does anybody know a fix. also here is my conky.rc

background no

use_xft yes

xftfont Bitstream Vera Sans Mono:size=9
xftalpha 0.8
update_interval 3.0
total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
own_window_colour hotpink
own_window_hints undecorated,below,skip_taskbar,sticky,skip_pager

double_buffer yes


minimum_size 280 5
draw_shades no
draw_outline no
draw_graph_borders yes
stippled_borders 8
border_margin 4

border_width 1
maximum_width 155
default_color black
default_shade_color black
default_outline_color black
alignment bottom_left
gap_x 15
gap_y 150
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
use_spacer no

TEXT
${color #000000${alignc}${nodename} ${uptime_short}

${color #000000CPU: ${color grey}$cpu%
${color #000000 ${cpugraph 16,140 000000 7f8ed3}
${color #000000RAM: $color$mem/$memmax
${color #000000 ${membar 6,140}
${color #000000Swap:$color$swap/$swapmax
${color #000000 ${swapbar 6,140}

${color #000000ETH0 Down: $color${downspeed eth0}${alignr} k/s 
${color #000000 ${downspeedgraph eth0 16,140 000000 7f8ed3 150}
${color #000000ETH0 Up:   $color${upspeed eth0}${alignr} k/s 
${color #000000 ${upspeedgraph eth0 16,140 000000 7f8ed3 18}

${color #000000ile systems:
${color #000000/       $color${fs_free /}
${color #000000 ${fs_bar 6,140 /}

${color #000000Processes:$color $processes | $running_processes
${color} Cpu usage    CPU
${color #ddaa00} ${top name 1}${offset -50} ${top cpu 1}
${color #000000 ${top name 2}${offset -50} ${top cpu 2}
${color #000000 ${top name 3}${offset -50} ${top cpu 3}
${color #000000 ${top name 4}${offset -50} ${top cpu 4}

${color} Mem usage    MEM
${color #ddaa00} ${top_mem name 1}${offset -50} ${top_mem mem 1}
${color #000000 ${top_mem name 2}${offset -50} ${top_mem mem 2}
${color #000000 ${top_mem name 3}${offset -50} ${top_mem mem 3}
${color #000000 ${top_mem name 4}${offset -50} ${top_mem mem 4}

---

### Post by emid on 2008-12-10
I just upgraded and am having the same issue.

---

### Post by ajcham on 2008-12-10
I'd never used conky before, but having just installed it on Intrepid as a test it is working fine.

Have you tried reinstalling it since you upgraded?

---

### Post by spiderbatdad on 2008-12-10
user_space no might be a problem. Should be something like left or right.

"Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none."

---

### Post by spiderbatdad on 2008-12-10
In fact your .conkyrc seems to have a lot of syntax errors. Try this copy of yours, slightly cleaned up.```
background yes

use_xft yes

xftfont Bitstream Vera Sans Mono:size=9
xftalpha 0.8
update_interval 3.0
total_run_times 0

own_window yes
own_window_type override
own_window_transparent yes
own_window_colour hotpink
own_window_hints undecorated,below,skip_taskbar,sticky,skip_pager

double_buffer yes


minimum_size 280 5
draw_shades no
draw_outline no
draw_graph_borders yes
stippled_borders 8
border_margin 4

border_width 1
maximum_width 155
default_color black
default_shade_color black
default_outline_color black
alignment bottom_left
gap_x 15
gap_y 150
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 2
override_utf8_locale no
#use_spacer right

TEXT
${color #000000} ${alignc}${nodename} ${uptime_short}

${color #000000} CPU: ${color grey}$cpu%
${color #000000} ${cpugraph 16,140 000000 7f8ed3}
${color #000000} RAM: $color$mem/$memmax
${color #000000} ${membar 6,140}
${color #000000} Swap:$color$swap/$swapmax
${color #000000} ${swapbar 6,140}

${color #000000} ETH0 Down: $color${downspeed eth0}${alignr} k/s
${color #000000} ${downspeedgraph eth0 16,140 000000 7f8ed3 150}
${color #000000} ETH0 Up: $color${upspeed eth0}${alignr} k/s
${color #000000} ${upspeedgraph eth0 16,140 000000 7f8ed3 18}

${color #000000}  file systems:
${color #000000} / $color${fs_free /}
${color #000000} ${fs_bar 6,140 /}

${color #000000} Processes:$color $processes | $running_processes
${color} Cpu usage CPU
${color #ddaa00} ${top name 1}${offset -50} ${top cpu 1}
${color #000000} ${top name 2}${offset -50} ${top cpu 2}
${color #000000} ${top name 3}${offset -50} ${top cpu 3}
${color #000000} ${top name 4}${offset -50} ${top cpu 4}

${color} Mem usage MEM
${color #ddaa00} ${top_mem name 1}${offset -50} ${top_mem mem 1}
${color #000000} ${top_mem name 2}${offset -50} ${top_mem mem 2}
${color #000000} ${top_mem name 3}${offset -50} ${top_mem mem 3}
${color #000000} ${top_mem name 4}${offset -50} ${top_mem mem 4}

```

---

### Post by emid on 2008-12-15
Could someone point out any errors in my .conkyrc that might be causing problems?  This setup used to work on 8.04 but doesn't anymore on a fresh 8.10 reinstall.

```
background yes

use_xft yes

xftfont sans :size=9
xftalpha 0.8
out_to_console no
update_interval 2.0
total_run_times 0

own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

double_buffer yes

#minimum_size 280 5
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
stippled_borders 0
border_margin 4

border_width 1
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

gap_x 5
gap_y 3

uppercase no
cpu_avg_samples 3
net_avg_samples 3
override_utf8_locale yes
use_spacer right
TEXT
${color #000000}${font Sans:size=10}Uptime: ${color #000000}$uptime | ${color #000000}CPU: ${color #000000}${cpu}% | ${color #000000}RAM: ${color #000000}$mem | ${color #000000}Swap: ${color #000000}$swap | ${color #000000}Home: ${color #000000}${fs_free /home} | ${color #000000}Data.Store: ${color #000000}${fs_free /media/data.store} | ${color #000000}Down: ${color #000000}${totaldown eth0} - ${color #000000}${downspeed eth0}k/s | ${color #000000}Up: ${color #000000}${totalup eth0} - ${color #000000}${upspeed eth0}k/s
```

---

### Post by emid on 2008-12-17
Removing "out_to_console no" fixed it for me.

---

