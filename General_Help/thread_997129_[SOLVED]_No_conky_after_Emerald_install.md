---
title: "[SOLVED] No conky after Emerald install?"
date: 2008-11-29
forum: General Help
---

### Post by OldDirtyTurtle on 2008-11-29
I installed Emerald Theme Manager this morning.  Since then, Conky won't run at startup.  I can run it from the terminal, but it won't come automatically.  The box is checked in the sessions menu. I don't get it.  If it helps, below is my .conkyrc code.

```
# Conky script (.conkyrc)
# Written by XXXXX - Ver. 2008.11.24
# Written for System76 Serval Professional (serp5)
# Ubuntu 8.10 Intrepid on x86_64 architecture
#
# UBUNTU-CONKY
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

#	*** RHYTHMBOX FORMAT SETTINGS ***

#	${rhythmbox-client --print-playing}
#              Print the title and artist of the playing song

#	${rhythmbox-client --print-playing-format}
#              Print formatted details of the song

#	*** PARAMETERS ***

#       %at    Album title
#       %aT    Album title in lowercase
#       %aa    Album artist
#       %aA    Album artist in lowercase
#       %ay    Release year of album
#       %an    Album disc number
#       %aN    Album disc number with leading zero
#       %ag    Album genre
#       %aG    Album genre in lowercase
#       %tt    Track title
#       %tT    Track title in lowercase
#       %ta    Track artist
#       %tA    Track artist in lowercase
#       %tn    Track number
#       %tN    Track number with leading zero
#       %td    Track duration
#       %te    Elapsed time of track

#       Variables can be combined using quotes. For example "%tn %aa %tt", will
#       print the track number followed by the artist  and  the  title  of  the
#       track.

# Create own window instead of using desktop (requi#543C38 in nautilus)
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
use_xft yes
xftfont Trebuchet MS:size=08
xftalpha 0.6
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 20

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color #543C38}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color #543C38}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
${cpugraph 000000 29B8F1}
CPU1 Usage: ${cpu cpu1}% ${cpubar cpu1}
CPU2 Usage: ${cpu cpu2}% ${cpubar cpu2}

NAME        		PID		CPU%		MEM%
${top name 1}	${top pid 1}	${top cpu 1}	${top mem 1}
${top name 2}	${top pid 2}	${top cpu 2}	${top mem 2}
${top name 3}	${top pid 3}	${top cpu 3}	${top mem 3}
${top name 4}	${top pid 4}	${top cpu 4}	${top mem 4}

${color #543C38}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
sda1:  ${fs_free_perc /dev/sda1}%   ${fs_bar 6 /dev/sda1}$color
sda3:  ${fs_free_perc /dev/sda3}%   ${fs_bar 6 /dev/sda3}

${color #543C38}NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0 
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color #543C38}BATTERY ${hr 2}$color
$battery

${color #543C38}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${if_running rhythmbox}${color #543C38}MUSIC ${hr 2}$color
  Artist  ${execi 1 rhythmbox-client --print-playing-format "%aA"}
  Title   ${execi 1 rhythmbox-client --print-playing-format "%tT"}
  Album   ${execi 1 rhythmbox-client --print-playing-format "%aT (%ay)"} $alignr track ${exec rhythmbox-client --print-playing-format "%tn"}
  Time     ${exec rhythmbox-client --print-playing-format "%te / %td"}
${else}  ${endif}

```

EDIT - solved - Dunno how, but solved...

---

