---
title: "Please help me make a good .conkyrc for my desktop with the Dust theme :)"
date: 2008-10-19
forum: General Help
---

### Post by wersdaluv on 2008-10-19
I want a simple .conkyrc for my dark desktop. I want it to have white fonts, be transparent, form one line under my upper panel, and be transparent. 

I want it to be a system monitor that shows me cpu activities (I have a Core 2 Duo), ram and swap usage, network activities, battery status, temperature, and disk space usage. 

Where can I start? :)

See screenshot for you to have an idea on how my desktop looks :)

---

### Post by wersdaluv on 2008-10-19
I'm done with it! :)

```
#Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.

# set to yes if you want Conky to be forked in the background
#background yes

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*


# Use Xft?
use_xft yes

# Set conky on the bottom of all other applications
#on_bottom yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
#mpd_host 
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# Use pseudo transparency with own_window?
own_window_transparent yes

# own_window_type = normal, desktop or override
own_window_type normal

# own_window_hints = undecorated,below,above,sticky,skip_taskbar,skip_pager
own_window_hints below undecorated skip_taskbar skip_pager sticky

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour black

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 500 5

# Draw shades?
draw_shades no

# Draw outlines?
#draw_outlines no

# Draw borders around text
draw_borders no

# Stippled borders?
#stippled_borders 8

# border margins
#border_margin 4

# border width
#border_width 1

# Default colors and also border colors
default_color black
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 25

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
#cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16)
#min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
#min_port_monitor_connections 256

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
override_utf8_locale yes
# stuff after 'TEXT' will be formatted on screen
xftfont Monospace:size=10

text_buffer_size 1024
TEXT
${color #ffffff}CPU1:${cpubar cpu1 8,25} | CPU2:${cpubar cpu2 8,25} | RAM:${membar 8,25} | Swap:${swapbar 8,25} | Root:${fs_bar 8,25 /} | Home:${fs_bar 8,25 /home} | Temp:${acpitemp}C | IP:${addr wlan0} | Rx:${downspeed wlan0} k/s${offset 5} | Sx:${upspeed wlan0} k/s | Uptime:${uptime}
```

---

### Post by talktorishav on 2009-10-10
Here, try this horzontal conky[ http://techspalace.blogspot.com/2009/10/beautiful-horizontal-conky.html]("http://techspalace.blogspot.com/2009/10/beautiful-horizontal-conky.html") as you said, one line, horizontal, and transparent.

---

