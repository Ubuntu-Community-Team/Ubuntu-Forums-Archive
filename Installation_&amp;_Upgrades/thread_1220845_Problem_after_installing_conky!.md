---
title: "Problem after installing conky!"
date: 2009-07-23
forum: Installation &amp; Upgrades
---

### Post by vickoxy on 2009-07-23
Hi,
i installed conky, and remove it, but after installation i keep having this output  in terminal:
[I]@Mini9:~$ gedit
/home/sd/.themes/T-ish-Brushed-bright/gtk-2.0/gtkrc:59: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/sd/.themes/T-ish-Brushed-bright/gtk-2.0/gtkrc:60: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/sd/.themes/T-ish-Brushed-bright/gtk-2.0/gtkrc:61: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/sd/.themes/T-ish-Brushed-bright/gtk-2.0/gtkrc:62: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.[/I]

Does anyone knows what went wrong?

Followed instructions here:
[http://www.junauza.com/2009/06/conky-installset-up-and-auto-start-fix.html](http://www.junauza.com/2009/06/conky-installset-up-and-auto-start-fix.html)

---

### Post by vickoxy on 2009-07-23
Ok, if i select standard human theme i get no such message-maybe is only issue with my combination of showtima, t-ish-brushed and elementary theme....?

---

### Post by Partyboi2 on 2009-07-23
Hi, it looks like it probably is.

---

### Post by vickoxy on 2009-07-23
Ok, i thought i should do new installation...:D

Thanks

---

### Post by 47db82 on 2010-03-13
I'm having trouble with conky myself as well. I should say I'm an extreme n00b, I have Ubuntu 9.10. I installed X11-dev then installed conky thru the terminal, followed instructions from a separate ubuntu forum post, and when i went to run conky from the terminal, I got this:

Conky: border_margin is deprecated, please use window.border_inner_margin instead
Conky: statfs '/home/tmo': No such file or directory
Conky: desktop window (22000cf) is subwindow of root window (ff)
Conky: window type - override
Conky: drawing to created window (0x3e00001)
Conky: drawing to double buffer
Conky: statfs '/home/tmo': No such file or directory
Conky: obj->data.cpu_index 2 info.cpu_count 1
Conky: attempting to use more CPUs than you have!
Segmentation fault
dbook82@dbook82-laptop:~$ # UBUNTU-CONKY
dbook82@dbook82-laptop:~$ #
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # Create own window instead of using desktop (required in nautilus)
dbook82@dbook82-laptop:~$ own_window yes
own_window: command not found
dbook82@dbook82-laptop:~$ own_window_type override
own_window_type: command not found
dbook82@dbook82-laptop:~$ own_window_transparent yes
own_window_transparent: command not found
dbook82@dbook82-laptop:~$ own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_hints: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # Use double buffering (reduces flicker, may not work for everyone)
dbook82@dbook82-laptop:~$ double_buffer yes
double_buffer: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # fiddle with window
dbook82@dbook82-laptop:~$ use_spacer right
use_spacer: command not found
dbook82@dbook82-laptop:~$ use_xft yes
use_xft: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # Update interval in seconds
dbook82@dbook82-laptop:~$ update_interval 3.0
update_interval: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # Minimum size of text area
dbook82@dbook82-laptop:~$ minimum_size 200 800
minimum_size: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # Draw shades?
dbook82@dbook82-laptop:~$ draw_shades no
draw_shades: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # Text stuff
dbook82@dbook82-laptop:~$ draw_outline no # amplifies text if yes
draw_outline: command not found
dbook82@dbook82-laptop:~$ draw_borders no
draw_borders: command not found
dbook82@dbook82-laptop:~$ font arial
font: command not found
dbook82@dbook82-laptop:~$ uppercase no # set to yes if you want all text to be in uppercase
uppercase: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # Stippled borders?
dbook82@dbook82-laptop:~$ stippled_borders 3
stippled_borders: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # border margins
dbook82@dbook82-laptop:~$ border_margin 9
border_margin: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # border width
dbook82@dbook82-laptop:~$ border_width 10
border_width: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # Default colors and also border colors, grey90 == #e5e5e5
dbook82@dbook82-laptop:~$ default_color grey
default_color: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ own_window_colour brown
own_window_colour: command not found
dbook82@dbook82-laptop:~$ own_window_transparent yes
own_window_transparent: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # Text alignment, other possible values are commented
dbook82@dbook82-laptop:~$ #alignment top_left
dbook82@dbook82-laptop:~$ alignment top_right
alignment: command not found
dbook82@dbook82-laptop:~$ #alignment bottom_left
dbook82@dbook82-laptop:~$ #alignment bottom_right
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # Gap between borders of screen and text
dbook82@dbook82-laptop:~$ gap_x 10
gap_x: command not found
dbook82@dbook82-laptop:~$ gap_y 10
gap_y: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # number of cpu samples to average
dbook82@dbook82-laptop:~$ # set to 1 to disable averaging
dbook82@dbook82-laptop:~$ cpu_avg_samples 2
cpu_avg_samples: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ text_buffer_size 1024
text_buffer_size: command not found
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ # stuff after &#8216;TEXT&#8217; will be formatted on screen
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ TEXT
TEXT: command not found
dbook82@dbook82-laptop:~$ $color${font arial:size=9}
bash: $color${font arial:size=9}: bad substitution
dbook82@dbook82-laptop:~$ $nodename@$sysname $kernel on $machine${font arial:size=8}
bash: $machine${font arial:size=8}: bad substitution
dbook82@dbook82-laptop:~$ Battery ${battery_bar 6 BAT0}
bash: ${battery_bar 6 BAT0}: bad substitution
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ ${color orange}CPU $color
bash: ${color orange}CPU: bad substitution
dbook82@dbook82-laptop:~$ ${freq}MHz${alignr}Load: ${loadavg}
MHzLoad:: command not found
dbook82@dbook82-laptop:~$ ${alignr}${loadgraph 20,250 e5e5e5 F1AA0E}
bash: ${alignr}${loadgraph 20,250 e5e5e5 F1AA0E}: bad substitution
dbook82@dbook82-laptop:~$ CPU Total:${color} ${cpu cpu0}% ${color}${alignr}Temp:${color} ${acpitemp}
bash: ${cpu cpu0}%: bad substitution
dbook82@dbook82-laptop:~$ ${alignr}${cpugraph 0 20,250 e5e5e5 F1AA0E}
bash: ${alignr}${cpugraph 0 20,250 e5e5e5 F1AA0E}: bad substitution
dbook82@dbook82-laptop:~$ Core one: ${color}${cpu cpu1}% ${alignr} Core two: ${color}${cpu cpu2}%
bash: ${color}${cpu cpu1}%: bad substitution
dbook82@dbook82-laptop:~$ ${cpugraph 1 20,120 e5e5e5 F1AA0E}${alignr}${cpugraph 2 20,120 e5e5e5 F1AA0E}
bash: ${cpugraph 1 20,120 e5e5e5 F1AA0E}${alignr}${cpugraph 2 20,120 e5e5e5 F1AA0E}: bad substitution
dbook82@dbook82-laptop:~$ NAME${alignr}PID         CPU%        MEM%
NAMEPID: command not found
dbook82@dbook82-laptop:~$ ${top name 1}${alignr}${top pid 1}       ${top cpu 1}          ${top mem 1}   
bash: ${top name 1}${alignr}${top pid 1}: bad substitution
dbook82@dbook82-laptop:~$ ${top name 2}${alignr}${top pid 2}       ${top cpu 2}          ${top mem 2}   
bash: ${top name 2}${alignr}${top pid 2}: bad substitution
dbook82@dbook82-laptop:~$ ${top name 3}${alignr}${top pid 3}       ${top cpu 3}          ${top mem 3}   
bash: ${top name 3}${alignr}${top pid 3}: bad substitution
dbook82@dbook82-laptop:~$ ${top name 4}${alignr}${top pid 4}       ${top cpu 4}          ${top mem 4}   
bash: ${top name 4}${alignr}${top pid 4}: bad substitution
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ ${color orange}MEMORY / DISK $color
bash: ${color orange}MEMORY: bad substitution
dbook82@dbook82-laptop:~$ Total: ${color}${memmax} ${alignr} Free: ${color}${memfree}
Total:: command not found
dbook82@dbook82-laptop:~$ RAM: $memperc% ${alignr}Swap: $swapperc% 
RAM:: command not found
dbook82@dbook82-laptop:~$ ${memgraph 20,120 e5e5e5 F1AA0E} ${alignr} ${swapbar 20,120 }
bash: ${memgraph 20,120 e5e5e5 F1AA0E}: bad substitution
dbook82@dbook82-laptop:~$ root: ${fs_used_perc /}% ${fs_bar 6 /}$color
bash: ${fs_used_perc /}%: bad substitution
dbook82@dbook82-laptop:~$ home: ${fs_used_perc /home/tmo}% ${fs_bar 6 /home/tmo}$color
bash: ${fs_used_perc /home/tmo}%: bad substitution
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ ${color orange}WIFI (${addr wlan0}) $color
bash: syntax error near unexpected token `${addr wlan0}'
dbook82@dbook82-laptop:~$ ${wireless_essid wlan0} ${wireless_link_bar 6 wlan0}
bash: ${wireless_essid wlan0}: bad substitution
dbook82@dbook82-laptop:~$ Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
bash: $color${downspeed wlan0}: bad substitution
dbook82@dbook82-laptop:~$ ${downspeedgraph wlan0 20,120 e5e5e5 F1AA0E} ${alignr}${upspeedgraph wlan0
> 20,120 e5e5e5 F1AA0E}$color
bash: ${downspeedgraph wlan0 20,120 e5e5e5 F1AA0E}: bad substitution
dbook82@dbook82-laptop:~$ Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
bash: ${totaldown wlan0}: bad substitution
dbook82@dbook82-laptop:~$ Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
> 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
bash: ${tcp_portmon 1 32767 count}: bad substitution
dbook82@dbook82-laptop:~$ 
dbook82@dbook82-laptop:~$ ${color orange}LOGGING $color
bash: ${color orange}LOGGING: bad substitution
dbook82@dbook82-laptop:~$ ${font arial:size=7}${execi 30 tail -n 10 /var/log/messages | fold -w45}

Some help please?
Or how can I delete it to reinstall fresh?

---

