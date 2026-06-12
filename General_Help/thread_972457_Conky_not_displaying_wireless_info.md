---
title: "Conky not displaying wireless info"
date: 2008-11-05
forum: General Help
---

### Post by swoody on 2008-11-05
I'm trying to get Conky to display the wireless network name, signal strength, and the signal bar, but it's not working. I uninstalled Conky, and then reinstalled it with this guide: [http://ubuntuforums.org/showthread.php?t=563401](http://ubuntuforums.org/showthread.php?t=563401) I also checked ifconfig, and it shows my device as eth2. Is there any way to change it back to wlan0? 

Also, does anyone know if you can display the Distro and version you're running, like it shows in the System Monitor? Thanks in advance to everybody! I've attached a screenshot, and here's my .conkyrc file:


```
background no
use_xft yes
xftfont Terminus:size=9
xftalpha 0.8
update_interval 1
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 230
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color F8F8FF
default_shade_color black
default_outline_color 483D8B
alignment top_right
gap_x 10
gap_y 60
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no


TEXT
$alignc Ubuntu 9.04 Jaunty
$alignc ${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'}
$alignc $mem / $memmax RAM
$alignc CPU: ${acpitemp}C | ${freq_dyn}Mhz
$alignc Platform: $machine

Hostname $alignr $nodename

Uptime $alignr $uptime


Wireless Network $alignr ${wireless_essid eth2}
Wireless IP $alignr ${addr eth2}
Wireless In $alignr ${downspeed eth2} kb/s
Wireless Out $alignr ${upspeed eth2} kb/s
Wireless Signal $alignr ${wireless_link_qual_perc eth2}%
${wireless_link_bar eth2}

CPU ${cpu cpu0}% ${cpubar cpu0} 

RAM $memperc% $membar

Swap $swapperc% ${swapbar}

Highest CPU:
   ${top name 1} ${top cpu 1}
   ${top name 2} ${top cpu 2}
   ${top name 3} ${top cpu 3}

Highest MEM:
   ${top_mem name 1} ${top_mem mem 1}
   ${top_mem name 2} ${top_mem mem 2}
   ${top_mem name 3} ${top_mem mem 3}



   Local Time $alignr ${time %H:%M}$font        

   UTC $alignr ${utime %H:%M}$font        


```

---

### Post by easybake on 2008-11-07
Have you tried running 
```
ifconfig
```
in terminal to make sure you are supposed to use eth2 and not wlan0.

You can use the ```
$kernel
``` in your config to display your Kernel but not distro.

---

### Post by swoody on 2008-11-07
> **woody86 said:**
> I also checked ifconfig, and it shows my device as eth2.

Yes, I did make sure it was eth2, and as it shows in my .conkyrc file I have eth2 for my IP, kb in, and kb out displays, and those all work fine.

---

### Post by swoody on 2008-11-17
Nobody has any other ideas?

---

