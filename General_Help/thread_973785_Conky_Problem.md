---
title: "Conky Problem"
date: 2008-11-07
forum: General Help
---

### Post by Tabenx on 2008-11-07
My problem is that the CPU usage bars stay the same even if one is at 30% and the other is at 0%. My conkyrc is below and so is a picture describing the problem. Thanks!
[[IMG]http://img519.imageshack.us/img519/1778/hhhcu2.th.jpg[/IMG]](http://img519.imageshack.us/my.php?image=hhhcu2.jpg) 
Conkyrc:
```
background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

TEXT
${color blue}SYSTEM ${hr 1}${color}
Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${acpitemp}C

CPU: ${alignr}${freq} MHz
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}
CPU2 ${alignr}${cpu cpu2}%
${cpubar 4 cpu2}

Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color red}Filesystem ${hr 1}${color}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}

${color green}NETWORK ${hr 1}${color}
Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${color yellow}${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}${color}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

${color orange}WEATHER ${hr 1}${color}
${execi 1800 /home/tabenx/.weather.sh 08816}
```

---

### Post by easybake on 2008-11-07
You have the variables for both bars mixed up. Change
from 
${cpubar 4 cpu1}
to
${cpubar cpu1 4}

---

### Post by Tabenx on 2008-11-07
You fantastic amazing wonderful person! I've had this problem for like 6 months or so. Thank you so much!

---

