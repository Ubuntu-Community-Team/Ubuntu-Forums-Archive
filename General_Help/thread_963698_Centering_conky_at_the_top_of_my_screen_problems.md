---
title: "Centering conky at the top of my screen: problems"
date: 2008-10-30
forum: General Help
---

### Post by SomeGuyDude on 2008-10-30
Hey folks. I'm not asking for anything complex, I'm just trying to center align my conky at the top of my screen.  The file in question:

```
alignment top_left
border_margin 5
border_width 1
default_color 000000
double_buffer yes
draw_borders no
draw_outline no
draw_shades no
gap_x 0
gap_y 0
minimum_size 1280 5
no_buffers yes
override_utf8_locale yes
own_window_colour black
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_transparent yes
own_window_type override
own_window yes
stippled_borders 0
update_interval 5
uppercase no
use_spacer yes
use_xft yes
xftfont Nu:size=9


TEXT
${alignc}${color 666666}${time %I:%M %p}$color ${time %A, %b %d %Y} ${color} | Kernel: ${color 666666}${kernel}  ${color}| UpTime:${color 666666} $uptime_short  ${color}| Cpu: ${color 666666}${cpu}% ${color} | ${color 666666}${voffset 1}${membar 6,100}${offset -100}${voffset -1}${color white}Mem${color 666666}${offset 80}${color}  | ${voffset 1}${color 666666}${fs_bar 6,100 /home}${offset -100}${color white}${voffset -1}Home${color 666666}${offset 80}${color} | ${voffset 1}${color 666666}${fs_bar 6,100 /}${offset -100}${voffset -1}${color white}Root${color 666666}${offset 80} ${color}| Email: ${color 666666}${execi 300 python ~/scripts/gmail.py}  ${color}| Weather: ${color 666666}${execi 3600 python ~/scripts/conkyForecast.py --location=USPA1290 --datatype=HT -i} ${color}| ${color}Battery: ${color 666666}${battery BAT0}  ${color}| ${color}Temp: ${color 666666}${acpitemp}C
```

Shouldn't the "minimum_size 1280 5" set that up? What ends up happening is throwign $alignc in there shoots the thing way to the right so the temperature bit is "off screen". I tried to add "maximum_width 1280" but that anchored it to the left side for some reason. Any ideas?

---

### Post by easybake on 2008-10-30
Instead of using $alignc at the beginning you could use ${goto #}. You would replace the # with a pixel value. If you wanted your time variable to start 20 pixels from the side you would just use ${goto 20}${time %I:%M %p}.

You can use $goto throughout your conky file if you have set places you want the variables to stay.

---

### Post by SomeGuyDude on 2008-10-30
> **easybake said:**
> Instead of using $alignc at the beginning you could use ${goto #}. You would replace the # with a pixel value. If you wanted your time variable to start 20 pixels from the side you would just use ${goto 20}${time %I:%M %p}.

You can use $goto throughout your conky file if you have set places you want the variables to stay.

Hmmmm. I found another solution, but I like this one a LOT more. Thanks! :guitar:

EDIT: My "solution" was basically to change "minimum_size 1280" to "maximum_width 1330" and for some reason it worked.

---

