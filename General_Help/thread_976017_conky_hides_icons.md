---
title: "conky hides icons"
date: 2008-11-08
forum: General Help
---

### Post by uber_nerd11 on 2008-11-08
When using conky on the left side of my screen, it will cover any icons that are residing there even though it does not sit on top of any windows that are opened (fixed that issue using a delay script).  Is there a way to make conky sit even further back into the desktop kind of between the folder icons and the desktop background so that the folders will display on top of it?  I am using compiz fusion as well if it makes any difference.

Here is my conkyrc for reference:

```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages
# - netstat connections to your computer
#
# — Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
alignment middle_left

# Gap between borders of screen and text
gap_x 10
gap_y 10



# stuff after ‘TEXT’ will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${cpu cpu1} ${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
${cpu cpu2} ${freq}MHz Load: ${loadavg} Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME PID CPU% MEM%
${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM: $memperc% ${membar 6}$color
Swap: $swapperc% ${swapbar 6}$color

Root: ${fs_free_perc /}% ${fs_bar 6 /}$color

${color orange}ETHERNET (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}WIRELESS (${addr wlan0}) ${hr 2}$color
AP: ${wireless_essid wlan0} ${alignc}Bitrate: ${wireless_bitrate wlan0}
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}


```

Any suggestions would be appreciated. Thanks!

---

### Post by uber_nerd11 on 2008-11-15
Any ideas?

Thanks

---

### Post by cl0ckwork on 2008-11-16
no solution so far.
conky is technically just another program with a window like terminal or firefox, but it has had the window borders removed and background blended into the wallpaper.
the only real solution is to move conky to the right side of the screen, or shorten your setup so the top left corner is still visible

---

### Post by cammin on 2008-11-16
# Gap between borders of screen and text
gap_x 10
gap_y 10


x is left and right
y is up and down

---

### Post by binbash on 2008-11-16
you can do it with compiz window rules plugin.

---

### Post by Altay_H on 2009-05-08
Sorry to bring back an old thread, but I'm having the same problem and can't figure out how to set Compiz to force conky to sit below the desktop icons. Under Window Rules in CompizConfig Settings Manager I see a list of options, none of which seem to be what I'm looking for. Do I need to add conky to the "below" list? It already sits below other windows, just not below the desktop icons.

---

### Post by ovidiub on 2010-01-21
use these settings:

own_window yes
own_window_transparent yes
own_window_type override


Cheers!

---

### Post by Altay_H on 2010-01-30
> **ovidiub said:**
> use these settings:

own_window yes
own_window_transparent yes
own_window_type override

Those settings didn't work for me unless I set double_buffer to yes. However, when double_buffer is yes, all of my desktop icons vanish every time conky refreshes until I hover over them.

I also tried:
```
own window no
own_window_type override
double_buffer no
```

That actually works perfectly, except that conky flickers every time it refreshes. I was happy with these settings for about a day before it drove me crazy. It's tolerable if my background is solid black, but it's still a bit irritating. Also, occasionally conky will refresh incorrectly and just disappear for 2 seconds. It's far from ideal, but it's the best I've been able to come up with.

I'm guessing these problems are caused by nautilus' inability to play well with conky. Does anyone know of a desktop environment that does play nicely with conky?

---

### Post by john84 on 2010-02-03
> **Altay_H said:**
> [...] except that conky flickers every time it refreshes. I was happy with these settings for about a day before it drove me crazy. It's tolerable if my background is solid black, but it's still a bit irritating. Also, occasionally conky will refresh incorrectly and just disappear for 2 seconds. It's far from ideal, but it's the best I've been able to come up with.

I'm guessing these problems are caused by nautilus' inability to play well with conky. Does anyone know of a desktop environment that does play nicely with conky?
First of all: I'm relatively new to linux, I just started using arch linux.
I had the same problem a few minutes ago, conky was flickering.
I made one line longer than the rest of the lines (if you don't want to add text you can add blank spaces)
My conky space became a bit bigger than before and now I don't have any flickering anymore.
My best guess is that this happend because some lines became 'bigger' or 'smaller' dynamically when it was refreshing, resulting in a flicker. Now one line is permanently the longest, so the width doesn't change anymore.
Maybe this info can help you.
I'm using OpenBox

---

### Post by Altay_H on 2010-02-03
I might give openbox a try. Which settings did you use for conky to get it to allow icons to be placed over it and not flicker?

---

### Post by john84 on 2010-02-04
> **Altay_H said:**
> I might give openbox a try. Which settings did you use for conky to get it to allow icons to be placed over it and not flicker?
I use conky in combination with iDesk.
I start them both automatically from the .xinitrc file (with a short sleep, so they actually start after my openbox).
At the moment I've got only one icon, but I can place it on top of conky without it starting to flicker.
This is my .conkyrc (without the comments from the heading).
I experimented a bit with conky so you'll probably find some lines that can be deleted.
```
alignment top_left
background no
border_width 1
cpu_avg_samples 2
default_color white
default_outline_color white
default_shade_color white
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades no
use_xft yes
xftfont DejaVu Sans Mono:size=8
gap_x 5
gap_y 60
minimum_size 5 5
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window no
own_window_class Conky
own_window_type override
#own_window_type desktop
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 0.90
uppercase no
use_spacer none
show_graph_scale yes
show_graph_range no
double_buffer yes

TEXT
#${scroll 16 $nodename - $sysname $kernel on $machine | }
 
$hr
|--------------- ${nodename} ---------------|
$hr
${color grey}Uptime:$color $uptime
${color grey}Frequency (in MHz):$color $freq
${color grey}Frequency (in GHz):$color $freq_g
${color grey}RAM Usage:$color $mem/$memmax - $memperc% ${membar 4}
${color grey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar 4}
${color grey}CPU Usage:$color $cpu% ${cpubar 4}
${color grey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$hr
${color grey}File systems:
 /     $color${fs_used /}/${fs_size /} ${fs_bar 6 /}
 /home $color${fs_used /home}/${fs_size /home} ${fs_bar 6 /home}
${color grey}Networking:
Up:$color ${upspeed eth0} ${color grey} - Down:$color ${downspeed eth0}
$hr
#${color grey}Name              PID   CPU%   MEM%
#${color lightgrey} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
#${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
#${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
#${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
#${cpugraph}

```

---

