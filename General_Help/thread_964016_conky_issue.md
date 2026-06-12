---
title: "conky issue"
date: 2008-10-30
forum: General Help
---

### Post by Hoobler on 2008-10-30
searched everywhere, couldnt find an answer to this

whenever i start Conky, i get this message in my terminal:

Conky: desktop window (12000be) is subwindow of root window (1a6)
Conky: window type - override
Conky: drawing to created window (4000001)
Conky: drawing to double buffer
localhost [127.0.0.1] 7634 (?) : Connection refused
Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory
localhost [127.0.0.1] 7634 (?) : Connection refused
localhost [127.0.0.1] 7634 (?) : Connection refused
localhost [127.0.0.1] 7634 (?) : Connection refused


the last message continues repeating.  so, if anyone could tell me what the problem is, that would be awesome!  :)

---

### Post by Awperator on 2008-10-30
It could help to post your entire conky file so we can figure out why conky is trying to contact localhost and failing.

---

### Post by Hoobler on 2008-10-30
sorry, here it is:

use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58



TEXT
 ${color 6694B2}${font OpenLogos:size=45} u t
${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25}  ${execi 1200 ~/scripts/pogodynka.sh}

   ${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C 
    
   ${font PizzaDude Bullets:size=16}v${font}   Up: ${upspeed eth1} Kb/s 
   ${font PizzaDude Bullets:size=16}r${font}   Down: ${downspeed eth1} Kb/s 

   ${font PizzaDude Bullets:size=16}M${font}   Upload: ${totalup eth1}
   ${font PizzaDude Bullets:size=16}S${font}   Download: ${totaldown eth1}

   ${color ffffff}${font StyleBats:size=16}A${font}  CPU0: ${cpu cpu0}% ${cpubar cpu0}
   ${font StyleBats:size=16}A${font}  CPU1: ${cpu cpu1}% ${cpubar cpu1}

   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent}% ${battery_bar}

   ${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py [email]myusername@myhost.org[/email] mypassword(censored) 3}

   ${color C2E078}${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

   ${font StyleBats:size=18}P${font}  Work:  ${uptime_short}


 ${font Radio Space:size=14}${time %A %d %Y}
      ${font Radio Space:size=55}${time %H:%M}

---

### Post by cl0ckwork on 2008-10-30
it seems to me the lines i highlighted could be the problem

```
use_xft yes
xftfont verdana:size=8
alignment top_right
xftalpha 0.8
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color BADCDD
use_spacer none
no_buffers yes
uppercase no
color1 F8DF58



TEXT
${color 6694B2}${font OpenLogos:size=45} u t
[highlight]${color BADCDD}${font weather:size=82}${execi 600 ~/scripts/conditions.sh}${color}${font}${voffset -25} ${execi 1200 ~/scripts/pogodynka.sh}[/highlight]

${font weather:size=28}x ${font}HDD ${execi 1 ~/scripts/hddmonit.sh}°C

${font PizzaDude Bullets:size=16}v${font} Up: ${upspeed eth1} Kb/s
${font PizzaDude Bullets:size=16}r${font} Down: ${downspeed eth1} Kb/s

${font PizzaDude Bullets:size=16}M${font} Upload: ${totalup eth1}
${font PizzaDude Bullets:size=16}S${font} Download: ${totaldown eth1}

${color ffffff}${font StyleBats:size=16}A${font} CPU0: ${cpu cpu0}% ${cpubar cpu0}
${font StyleBats:size=16}A${font} CPU1: ${cpu cpu1}% ${cpubar cpu1}

[highlight]${color F8DF58}${font StyleBats:size=16}8${font} Battery: ${battery_percent}% ${battery_bar}[/highlight]

[highlight]${color F8DF58}${font FreeSans:size=16}@${font}${execpi 300 python ~/scripts/gmail_parser.py myusername@myhost.org mypassword(censored) 3}[/highlight]

${color C2E078}${font PizzaDude Bullets:size=16}J${font} $mem / $memmax

${font StyleBats:size=18}P${font} Work: ${uptime_short}


${font Radio Space:size=14}${time %A %d %Y}
${font Radio Space:size=55}${time %H:%M}
```

the battery line causes--
[b]Conky: can't open /sys/class/power_supply/BAT0/uevent: No such file or directory
Conky: can't open /proc/acpi/battery/BAT0/state: No such file or directory[/b]

and the other error line--
**localhost [127.0.0.1] 7634 (?) : Connection refused**
-- is caused by either your weather or gmail section

---

### Post by josesilva on 2009-05-06
You need to run
sudo dpkg-reconfigure hddtemp
and choose to run hddtemp as a daemon (last screen). This will fix the can't connect to localhost issue.

As for the battery, you need to modify the battery line in your ~/.conkyrc file to read like this:
   ${color F8DF58}${font StyleBats:size=16}8${font}  Battery: ${battery_percent BAT1}% ${battery_bar BAT1}

Or change BAT1 to whatever your battery proc info is (ls /proc/acpi/battery/).

Hope this helps.

---

