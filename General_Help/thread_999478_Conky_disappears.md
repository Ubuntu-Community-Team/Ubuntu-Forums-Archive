---
title: "Conky disappears"
date: 2008-12-01
forum: General Help
---

### Post by turned2black on 2008-12-01
My new conky disappears after I open a program full screen. My old conky did not do this. I saved my old one and all the settings at the top of the file appear to be identical. Any suggestions?

Here's the file:

background yes
use_xft yes
xftfONt Utopia:size=10
xftalpha 0.8
update_interval 5
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline yes
stippled_borders no
border_margin 0
border_width 1
default_color white
default_shade_color black
alignment bottom_middle
gap_y 35
use_spacer no
no_buffers yes
uppercase no
double_buffer yes

TEXT
${color white}$hr
${alignc}${color white}$kernel ${color darkgrey}ON ${color white}$nodename ${color white}
${alignc}${color white}${cpu cpu1}%${color darkgrey} CPU1 LOAD ${color white} +  ${color white}${cpu cpu2}%${color darkgrey} CPU2 LOAD ${color white}
${alignc}${color white}$mem/$memmax ${color darkgrey}RAM ${color white} +  ${color white}$swap/$swapmax ${color darkgrey}SWAP
${alignc}${color white} $processes ${color darkgrey}PROCESSES ${color white} +  ${color darkgrey}TOP PROCESS${color white} ${top name 1}
${alignc}${color white} ${fs_used /}${color darkgrey} of ${color white}${fs_size /}${color darkgrey} HD ${color white} + ${color darkgrey} CONNECTED TO ${color white}${addr wlan0} ${color white}
$hr

---

### Post by xjcannonx on 2008-12-01
New to conky but try this:
```
background yes
use_xft yes
xftfONt Utopia:size=10
xftalpha 0.8
update_interval 5
own_window[COLOR="Red"]_type[/COLOR] yes
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline yes
stippled_borders no
border_margin 0
border_width 1
default_color white
default_shade_color black
alignment bottom_middle
gap_y 35
use_spacer no
no_buffers yes
uppercase no
double_buffer yes
```

---

### Post by easybake on 2008-12-02
Adding ```
own_window_type override
``` would work better.

---

### Post by loomsen on 2008-12-02
> **turned2black said:**
> Any suggestions?

double_buffer yes
...
no_buffers yes
double_buffer yes



:-s

I have to admit I didn't use conky for quite some time now, but couple of months ago 
```

minimum_size 1440 2
maximum_width 1440

```

this helped. So basically fixing the desired width.

Oh yes, own_window override should work as well.

---

