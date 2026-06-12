---
title: "Conky: /proc/i8k doesn't exist!"
date: 2008-09-08
forum: General Help
---

### Post by schizostatic on 2008-09-08
I have been trying to get conky working for the past few hours and every 'config' I try from the forums gives me this error
> Conky: /proc/i8k doesn't exist! use insmod to make sure the kernel driver is loaded...
The config I am using is
```
font freesans:size=8
xftfont freesans:size=8
use_xft yes
#easy

xftalpha 1

update_interval 3.0

use_spacer right
#background no
own_window yes
own_window_hints undecorated, sticky, below, skip_pager, skip_taskbar
own_window_colour 0B243B
double_buffer yes
draw_shades no

minimum_size 200 5
maximum_width 200

gap_x 20
gap_y 20

color6 2e2e2e

color1 DF7401
color2 57CEF9
color3 0B3861
color4 404040
color5 1f1f1f
color6 AADA2C

draw_outline no
no_buffers yes
uppercase no


draw_borders no
draw_graph_borders no


default_shade_color black
default_color grey90
default_outline_color DarkGrey

#alignment bottom_left
alignment bottom_right
#alignment top_left
#alignment top_right


# stuff after 'TEXT' will be formatted on screen
FF8000
TEXT
${color1}${hr 5}

    ${color2}PROCESSES$alignr$processes    

    ${color2}${top name 1}$alignr${top cpu 1}    
    ${top name 2}$alignr${top cpu 2}    
    ${top name 3}$alignr${top cpu 3}    
    ${top name 4}$alignr${top cpu 4}    
    ${top name 5}$alignr${top cpu 5}    
    ${top name 6}$alignr${top cpu 6}    
    ${top name 7}$alignr${top cpu 7}    
    ${top name 8}$alignr${top cpu 8}    
    ${top name 9}$alignr${top cpu 9}    
    ${top name 10}$alignr${top cpu 10}    

${color1}${hr 5}

    ${color2}UpTime:$alignr$uptime    
    Kernel:$alignr$kernel    
    ${color black}${fs_bar 50,180 /monkey}
${voffset -71}
    ${color1}${cpugraph 25, 180}   
${voffset -21}
    ${color1}${memgraph 25, 180}    

    ${color2}FILE SYSTEMS
    ${color2}/:$alignr${fs_free /}/${fs_size /}    
    ${color black}${fs_bar 5,180 /monkey}
${voffset -24}
    ${color1}${fs_bar 5,180 /}    
    ${color2}HOME:$alignr${fs_free /home}/${fs_size /home}   
    ${color black}${fs_bar 5,180 /monkey}   
${voffset -24}
    ${color1}${fs_bar 5,180 /home}
```
From what I can tell that error refers to trying to use lm_sensors, but I am not seeing a temp check or fan speed check or anything along those lines. Heh maybe I have been just staring at the problem to long.

This is on a Lenovo laptop.

---

### Post by S.A.A on 2008-09-08
Try removing these lines:

```
${top name 5}$alignr${top cpu 5}    
    ${top name 6}$alignr${top cpu 6}    
    ${top name 7}$alignr${top cpu 7}    
    ${top name 8}$alignr${top cpu 8}    
    ${top name 9}$alignr${top cpu 9}    
    ${top name 10}$alignr${top cpu 10}
```

---

### Post by schizostatic on 2008-09-08
Cool thanks, now its time for me to learn how to actually make this thing look the way I want.

---

