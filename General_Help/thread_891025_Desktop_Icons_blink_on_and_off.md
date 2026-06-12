---
title: "Desktop Icons blink on and off"
date: 2008-08-15
forum: General Help
---

### Post by celtic426 on 2008-08-15
My desktop icons disappear when I am running Conky.  But when I highlight my mouse over them they appear for a second then go away.  This is my conkyrc file:

> #avoid flicker
double_buffer yes
#own window to run simultanious 2 or more conkys
own_window no
own_window_transparent yes
own_window_type overide
own_window_hints undecorate,skip_taskbar,skip_pager
#borders
draw_borders no
#shades
draw_shades no
#position
gap_x 12
gap_y 8
alignment bottom_right
#behaviour
update_interval 2
#colour
default_color bfbfbf
#font
use_xft yes
xftfont Sans:size=10
#to prevent window from moving
use_spacer yes
TEXT
${color FFFFFF}linux: ${color 95956B}${font}${kernel}${color FFFFFF} ${color FFFFFF} up: ${color 95956B}${font}${uptime_short}${color FFFFFF} ${color FFFFFF} core: ${color 95956B}${font}${cpu cpu1}% ${color FFFFFF} mem: ${color 95956B}${font}${mem} ${color FFFFFF} 


Its a pretty simple conky config.  Does anyone have any ideas on this? Thanks.

---

### Post by celtic426 on 2008-08-15
I fixed it by going here: [http://ubuntuforums.org/archive/index.php/t-658861.html](http://ubuntuforums.org/archive/index.php/t-658861.html)

---

