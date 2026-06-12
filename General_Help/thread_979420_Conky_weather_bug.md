---
title: "Conky weather bug"
date: 2008-11-11
forum: General Help
---

### Post by Bofur on 2008-11-11
I'm using the guide from [http://ubuntuforums.org/showthread.php?p=4130735#post4130735](http://ubuntuforums.org/showthread.php?p=4130735#post4130735)

I got it to work, everything shows up just fine, however, next to current conditions it says 
"Feels like 46Å"

Heres my conkyrc:
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
default_color black
default_shade_color white
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
${color black}SYSTEM ${hr 1}${color}

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

${color black}Filesystem ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}


${color black}NETWORK ${hr 1}${color}

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,107} ${alignr}${upspeedgraph wlan0 25,107}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}

${color black}WEATHER ${hr 1}${color}

${voffset -3}$alignc CURRENT CONDITIONS 
${voffset -7}$hr $color
${execi 3600 perl ~/scripts/weather.pl USWY0102 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl USWY0102 f t}
${voffset -15}$alignr${offset -60}${font weather:size=45}${execi 3600 perl ~/scripts/weather.pl USWY0102 f cp}$font
```Any help would be appreciated, Thanks!

---

