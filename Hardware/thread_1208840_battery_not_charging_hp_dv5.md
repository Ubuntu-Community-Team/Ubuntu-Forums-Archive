---
title: "battery not charging hp dv5"
date: 2009-07-09
forum: Hardware
---

### Post by sdlynx on 2009-07-09
Hi.

My battery will charge when my laptop is off or on Windows, but it seems to stop charging after a random point while running Ubuntu.  The battery stopped charging at 18% this time, and last boot it stopped at 31%.  The only new package I installed was lirc (an IR thing). Suggestions?

sdlynx

---

### Post by sdlynx on 2009-07-09
ok I figured out the culprit. For some reason, when conky is running, my battery won't charge... wtf? Here's .conkyrc:

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
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no #Transparent background.

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval .5

# Minimum size of text area
minimum_size 260 5

# Draw shades?
draw_shades no

# Draw borders around graphs
draw_graph_borders no

# Text stuff
draw_outline yes
draw_borders no
override_utf8_locale no
xftfont HandelGotDLig:size=9
xftalpha 0.8
#font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color EEEEEE
color1 74afed
default_outline_color black

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 30
gap_y 40

#add for logging:
#${font HandelGotDLig:size=14}${color1}LOGGING${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
#${execi 30 tail -n3 /var/log/messages | awk '{print " ",$5,$6,$7,$8,$9,$10}' | fold -w50}

# stuff after 'TEXT' will be formatted on screen



TEXT
${font HandelGotDLig:size=14}${color1}SYSTEM${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color${font HandelGotDLig:size=10}
$nodename
$sysname  $kernel on $machine
${font HandelGotDLig:size=10} ${time %I:%M:%S %p} $alignr ${font HandelGotDLig:size=10}UPTIME: $font$uptime${font HandelGotDLig:size=10}
${time %A, }${time %B}${time %e} ${time %G}
${font HandelGotDLig:size=10}BATTERY: $font$battery_percent%
${battery_bar 4}

${font HandelGotDLig:size=14}${color1}CPU${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
${font HandelGotDLig:size=10}CORE 1: $font${cpu cpu1}% $alignr @ ${freq 1} MHz
${cpubar cpu1 4 303030 C0C0C0}
${font HandelGotDLig:size=10}CORE 2: $font${cpu cpu2}% $alignr @ ${freq 2} MHz
${cpubar cpu2 4 303030 C0C0C0}

${font HandelGotDLig:size=14}${color1}MEMORY${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
${font HandelGotDLig:size=10}RAM: $font$memperc% ${alignr}$mem ${font HandelGotDLig:size=10}/ $font$memmax 
${membar 4}
${font HandelGotDLig:size=10}SWAP: $font$swapperc% ${alignr}$swap ${font HandelGotDLig:size=10}/ $font$swapmax 
${swapbar 4}

${font HandelGotDLig:size=14}${color1}DISK${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
${font HandelGotDLig:size=10}VOLUME${alignr}SIZE$font
${font HandelGotDLig:size=10}ROOT:$font${alignr}${fs_size /}
${fs_bar 4 /}$color
${if_mounted /windows}${font HandelGotDLig:size=10}WINDOWS:$font$alignr${fs_size /windows}
${fs_bar 4 /windows}$color $endif

${font HandelGotDLig:size=14}${color1}ETHERNET${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
${font HandelGotDLig:size=10}LOCAL: $font${addr eth0} $alignr ${color} ${font HandelGotDLig:size=10}EXTERNAL: $font${execi 140 wget -O - http://whatismyip.org/ | tail}${color}
${font HandelGotDLig:size=10}DOWN: $font$color${downspeed eth0} k/s $alignr ${font HandelGotDLig:size=10}TOTAL: $font${totaldown eth0} 
${font HandelGotDLig:size=10}UP: $font${upspeed eth0} k/s $alignr ${font HandelGotDLig:size=10}TOTAL: $font${totalup eth0}

${font HandelGotDLig:size=14}${color1}WIRELESS${color}${font HandelGotDLig:size=11}INFORMATION${color1} ${hr 2}$color$font
${font HandelGotDLig:size=10}ESSID: $font${wireless_essid wlan0}$alignr  $color ${font HandelGotDLig:size=10}MODE: $font${wireless_mode wlan0}
${font HandelGotDLig:size=10}LOCAL: $font${addr wlan0} ${color}		${font HandelGotDLig:size=10}QUALITY: $font${wireless_link_bar wlan0}
${font HandelGotDLig:size=10}DOWN: $font$color${downspeed wlan0} k/s $alignr ${font HandelGotDLig:size=10}TOTAL: $font${totaldown wlan0} 
${font HandelGotDLig:size=10}UP: $font${upspeed wlan0} k/s $alignr ${font HandelGotDLig:size=10}TOTAL: $font${totalup wlan0}

```

---

### Post by Dawei87 on 2009-07-27
just wanted to say im having the same issue in jaunty 32-bit on an hp-dv5. so far it wont charge at all while booted but at the same time, im not running conky at all and still have the issue.

---

### Post by jackhulu on 2009-12-14
My battery always not enough

I am going to buy the 12 cell for my HP DV5

[http://www.laptopbatterybuy.com/12-cell-hp-dv5-series-laptop-battery](http://www.laptopbatterybuy.com/12-cell-hp-dv5-series-laptop-battery)

Hope give more time.

---

### Post by mikenz on 2010-03-02
hello,

I recently upgrade from 9.04 - 9.10 to my hp dv5 laptop and now my battery will not charge any ideas of updates that could help me with this problem?

---

### Post by djaquay on 2010-06-10
I've got a new DV6 that I put 10.4 on fresh, and discovered today that my charge wouldn't go above 21%.  Found this thread, suspected a software issue, and rebooted; my charge jumped to 100%.

I've been suspending it a lot (since I discovered to my joy that suspending actually works!), and I wonder if that has something to do with the battery status losing its clue.  I intend to keep an eye on the status better, and work off of battery more than usual to see what happens.  FWIW, my usual work pattern is to only take it off A/C while suspended, to move to another outlet to work; I rarely use the battery.

Dave

---

