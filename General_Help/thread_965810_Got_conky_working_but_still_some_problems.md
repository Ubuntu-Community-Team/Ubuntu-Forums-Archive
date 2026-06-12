---
title: "Got conky working but still some problems"
date: 2008-10-31
forum: General Help
---

### Post by w1av on 2008-10-31
Hello, 
I managed to get conky working as far as displaying the data I wanted to display, ie. partitions. But there are a couple other issues. The "bar" that shows disk space is a little too long compared to the others that were already on there. And I still have to be ROOT to launch conky from terminal. Plus the partitions are not mounted and do not show the actual usage unless I manually mount them all first before starting conky.

Attached is a screenshot that show the unusually long (wide) bars for the partitions...still unsure even after browsing thru man pages.....cryptic info????? Any suggestions?

---

### Post by easybake on 2008-10-31
> **w1av said:**
> Hello, 
I managed to get conky working as far as displaying the data I wanted to display, ie. partitions. But there are a couple other issues. The "bar" that shows disk space is a little too long compared to the others that were already on there. And I still have to be ROOT to launch conky from terminal. Plus the partitions are not mounted and do not show the actual usage unless I manually mount them all first before starting conky.

Attached is a screenshot that show the unusually long (wide) bars for the partitions...still unsure even after browsing thru man pages.....cryptic info????? Any suggestions?

To change the bars all you have to do is change the numbers in the bar variable. They go as follows. ${(type)bar #(height) #(length)} 

For example. ${membar 5, 135}
means Memory usage bar 5 pixels in height 135 pixels in length.

I'm not sure enough to provide solutions for the other 2 issues. BruceM will know.

BRUUUUUUUCE!!!!

---

### Post by m_l17 on 2008-11-01
Please post your .conkyrc, inorder to get help.

Here is mine for comparison:

```
### my conky setup for Dell Insipron 531 ###

# XUBUNTU - CONKY- AMD64x2 - VERSION
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
#minimum_size 250 5

# Maximum Width
maximum_width 295

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font Terminus -1
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
#stippled_borders 3

# border margins
border_margin 9

# border width
border_width 5

# Default colors and also border colors, grey90 == #e5e5e5
default_color white

own_window_colour black
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 5
gap_y 15

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color ffffff}Xubuntu ${hr 2}$color
${uptime} | $nodename $sysname $kernel on $machine

${color ffffff}Amd64 X2 4000+ ${hr 2}$color
${freq}MHz $alignr ${cpu cpu0}%  Load ${loadavg}   Temp ${acpitemp}
${cpubar cpu0}
${freq}MHz $alignr ${cpu cpu1}%  Load ${loadavg}   Temp ${acpitemp}
${cpubar cpu1}
${cpugraph 000000 ffffff}
Processes $processes
Running $running_processes

NAME             PID      CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color ffffff}Memory ${hr 2}$color
Mem $alignc $memperc%    $mem / $memmax
${membar 6}$color
Swap $alignc   $swapperc%    $swap / $swapmax  
${swapbar 6}$color

${color ffffff}Hdd ${hr 2}$color
/ $alignc ${fs_free_perc /}%    ${fs_used /}/ ${fs_size /}
${fs_bar 6 /}$color
/home $alignc ${fs_free_perc /home}%    ${fs_used /home}/ ${fs_size /home}
${fs_bar 6 /home}$color
/data $alignc ${fs_free_perc /data}%    ${fs_used /data}/ ${fs_size /data}
${fs_bar 6 /data}$color

${color ffffff}Network ${hr 2}$color
eth0's IP  ${addr eth0}$color

Public IP  ${execi 3600 wget -O - http://whatismyip.org/ | tail}$color

Down $color${downspeed eth0}k/s            Up ${upspeed eth0}k/s
${downspeedgraph eth0 25,140 000000 ffffff}$color ${alignr}${upspeedgraph eth0 
25,140 000000 ffffff}$color
Total ${totaldown eth0}          Total ${totalup eth0}
${color ffffff}${hr 2}$color
```

These links where helpful for me:

[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/#comment-1286]("http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/#comment-1286")

[http://ubuntuforums.org/showthread.php?t=205865&highlight=conky]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky")

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky]("http://ubuntuforums.org/showthread.php?t=281865&highlight=conky")

---

### Post by w1av on 2008-11-03
OK I got the bar length issue resolved easily, but still having trouble with having to be ROOT in order to launch conky. I will post my conky.conf (.conkyrc?) today when I get home.....thanks

---

