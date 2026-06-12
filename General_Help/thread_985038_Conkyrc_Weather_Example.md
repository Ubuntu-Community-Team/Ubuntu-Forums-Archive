---
title: "Conkyrc Weather Example"
date: 2008-11-17
forum: General Help
---

### Post by Shwefty on 2008-11-17
Hey there, I was reading the wonderful [http://ubuntuforums.org/showthread.php?t=869328]("http://ubuntuforums.org/showthread.php?t=869328"), and it occurred to me that you really have to hunt and peck to find a working conkyrc (and they use a conky template too, if you're interested, check it out!).

So, I decided to post mine as-is.  Basically, I did almost nothing, it's the awesome [Conky-Colors]("http://www.gnome-look.org/content/show.php/CONKY-colors?content=92328") download from Gnome-look with functionality REMOVED (Network IP and email checking) but more of the weather stuff added.  Check out Gnome-look for installation instructions and the top link for weather installation instructions.  Here's the code!

```
# Use Xft?
use_xft yes
xftfont DejaVu Sans:size=8
xftalpha 0.8
text_buffer_size 2048

# Update interval in seconds
update_interval 1

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 200

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline yes

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 5

# border width
border_width 1

# Default colors and also border colors
default_color white
#default_shade_color white
#default_outline_color black
own_window_colour white

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 35
gap_y 50

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

TEXT
SYSTEM ${hr 2}
${voffset 2}${font OpenLogos:size=16}u${font}   Kernel:  ${alignr}${kernel}
${font StyleBats:size=16}A${font}   CPU0: ${cpu cpu1}% ${alignr}${cpubar 8,60 cpu1}
${font StyleBats:size=16}A${font}   CPU1: ${cpu cpu2}% ${alignr}${cpubar 8,60 cpu2}
${font StyleBats:size=16}g${font}   RAM: $memperc% ${alignr}${membar 8,60}
${font StyleBats:size=16}j${font}   SWAP: $swapperc% ${alignr}${swapbar 8,60}
${font Webdings:size=16}~${font}  Battery: ${battery_percent BAT0}% ${alignr}${battery_bar 8,60 BAT0}
${font StyleBats:size=16}q${font}   Uptime: ${alignr}${uptime}

DATE ${hr 2}
${alignc 35}${font Arial Black:size=26}${time %H:%M}${font}
${alignc}${time %A %d %Y}

HD ${hr 2}
${voffset 4}${font Pie charts for maps:size=14}7${font}   ${voffset -5}Root:
${voffset 4}${fs_used /}/${fs_size /} ${alignr}${fs_bar 8,60 /}
${font Pie charts for maps:size=14}7${font}   ${voffset -5}Home:
${voffset 4}${fs_free /home}/${fs_size /home} ${alignr}${fs_bar 8,60 /home}

NETWORK ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}Z${font}   Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,60 wlan0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth0}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth0}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth0}
${endif}${else}${if_existing /proc/net/route eth1}
${voffset -6}${font PizzaDude Bullets:size=14}O${font}   Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}U${font}   Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,60 C22F2F DA3F3F}
${voffset 4}${font PizzaDude Bullets:size=14}N${font}   Upload: ${alignr}${totalup eth1}
${voffset 4}${font PizzaDude Bullets:size=14}T${font}   Download: ${alignr}${totaldown eth1}
${voffset 4}${font PizzaDude Bullets:size=14}a${font}   Local Ip: ${alignr}${addr eth1}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
WEATHER ${hr 2}
${if_existing /proc/net/route wlan0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USTX0045 --datatype=WF --imperial}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USTX0045 --datatype=HT --imperial}${font}

${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=USTX0045 --datatype=HM --imperial}
${voffset 0}${alignr 35}${font ConkyWeather:style=Bold:size=32}${execi 600 conkyForecast --location=USTX0045 --datatype=WF --startday=1 --imperial}${font}
${voffset -28}Tomorrow: ${alignr 50}${execi 600 conkyForecast --location=USTX0045 --datatype=HT --startday=1 --imperial}/${execi 600 conkyForecast --location=USTX0045 --datatype=LT --startday=1 --imperial}
${voffset 7}${alignr 35}${font ConkyWeather:style=Bold:size=32}${execi 600 conkyForecast --location=USTX0045 --datatype=WF --startday=2 --imperial}${font}
${voffset -28}Next Day: ${alignr 50}${execi 600 conkyForecast --location=USTX0045 --datatype=HT --startday=2 --imperial}/${execi 600 conkyForecast --location=USTX0045 --datatype=LT --startday=2 --imperial}


${else}${if_existing /proc/net/route eth0}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USTX0045 --datatype=WF --imperial}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USTX0045 --datatype=HT --imperial}${font}

${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=USTX0045 --datatype=HM --imperial}
${voffset 0}${alignr 35}${font ConkyWeather:style=Bold:size=32}${execi 600 conkyForecast --location=USTX0045 --datatype=WF --startday=1 --imperial}${font}
${voffset -28}Tomorrow: ${alignr 50}${execi 600 conkyForecast --location=USTX0045 --datatype=HT --startday=1 --imperial}/${execi 600 conkyForecast --location=USTX0045 --datatype=LT --startday=1 --imperial}
${voffset 7}${alignr 35}${font ConkyWeather:style=Bold:size=32}${execi 600 conkyForecast --location=USTX0045 --datatype=WF --startday=2 --imperial}${font}
${voffset -28}Next Day: ${alignr 50}${execi 600 conkyForecast --location=USTX0045 --datatype=HT --startday=2 --imperial}/${execi 600 conkyForecast --location=USTX0045 --datatype=LT --startday=2 --imperial}

${endif}${else}${if_existing /proc/net/route eth1}
${voffset -10}${alignr 56}${font ConkyWeather:style=Bold:size=40}${execi 600 conkyForecast --location=USTX0045 --datatype=WF --imperial}${font}
${voffset -50}${font Weather:size=40}y${font}  ${voffset -38}${font Arial Black:size=26}${execi 600 conkyForecast --location=USTX0045 --datatype=HT --imperial}${font}

${voffset 0}Humidity: ${alignr}${execi 600 conkyForecast --location=USTX0045 --datatype=HM --imperial}
${voffset 0}${alignr 35}${font ConkyWeather:style=Bold:size=32}${execi 600 conkyForecast --location=USTX0045 --datatype=WF --startday=1 --imperial}${font}
${voffset -28}Tomorrow: ${alignr 50}${execi 600 conkyForecast --location=USTX0045 --datatype=HT --startday=1 --imperial}/${execi 600 conkyForecast --location=USTX0045 --datatype=LT --startday=1 --imperial}
${voffset 7}${alignr 35}${font ConkyWeather:style=Bold:size=32}${execi 600 conkyForecast --location=USTX0045 --datatype=WF --startday=2 --imperial}${font}
${voffset -28}Next Day: ${alignr 50}${execi 600 conkyForecast --location=USTX0045 --datatype=HT --startday=2 --imperial}/${execi 600 conkyForecast --location=USTX0045 --datatype=LT --startday=2 --imperial}


${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Weather Unavailable
${endif}
```

---

### Post by Shwefty on 2008-11-17
Here's a better attached picture.

---

