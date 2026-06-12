---
title: "Conky disappears with startup?"
date: 2008-07-13
forum: General Help
---

### Post by grenadier32 on 2008-07-13
So I have a weird problem with conky. I have it in my sessions set to run at startup, and when my desktop starts up, I see it appearing for a short time and then vanishing (presumably hidden under nautilus or something). Is there something I can do to fix it? I can fix it manually by running:```
pkill conky; conky &
``` But this is kind of annoying. Is there any way to fix that?

Here's my .conkyrc:

```
# set to yes if you want Conky to be forked in the background
background no

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

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Not sure what this does, but it's cool
use_xft yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 37

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
use_spacer right

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
${color orange}SYSTEM ${hr 2}$color
$nodename - $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #cc2222} $cpu% ${cpubar}
${color lightgrey}Temperature:${color} ${acpitemp}degrees
${color red}${cpugraph 0000ff 00ff00}

${color orange}MEMORY ${hr 2}$color
${color}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color}Processes:$color $processes  ${color}Running:$color $running_processes

${color orange}FILE SYSTEMS ${hr 2}$color
Root: $color${fs_used /}/${fs_size /} ${fs_bar /}
Storage: $color${fs_used /media/Storage/}/${fs_size /media/Storage/} ${fs_bar /media/Storage/}

${color orange}NETWORK (${addr ra0}) ${hr 2}$color
 Down:${color #8844ee} ${downspeed ra0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed ra0} k/s
${color #0000ff}${downspeedgraph ra0 32,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph ra0 32,150 0000ff ff0000}
${color}Total Down: ${totaldown ra0} ${alignr}Total Up: ${totalup ra0}

${color orange}PROCESSES ${hr 2}$color
${color light blue}NAME$color            ${color light blue}PID$color       ${color light blue}CPU%$color      ${color light blue}MEM%$color
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MUSIC ${hr 2}$color
${execi 60 dcop amarok player artist} - ${execi 60 dcop amarok player title}
```

---

### Post by tech0007 on 2008-07-13
Make sure you typed

conky &

in the command box in Sessions.  Not just 'conky'

---

### Post by grenadier32 on 2008-07-15
> **tech0007 said:**
> Make sure you typed

conky &

in the command box in Sessions.  Not just 'conky'

That doesn't do it, unfortunately. The problem isn't that the program is shutting down, it's that something else is covering it up that starts up after it does.

Any other suggestions? Settings I should change in .conkyrc?

---

### Post by Diptansu on 2008-07-15
I am having the same problem... 

It not only appears for a few seconds at the start up ... It also shows for a few second at the shut down...

But it was not happening at the beginning . It started after i changed my first 'conky' file and copy-paste another one ...

 Help me plzz ...

---

### Post by pelle.k on 2008-07-15
```
# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type override

```
This is correct.
The problem here is that conky launches before nautilus draws the desktop background. _Some people would say you should create a script_ to delay the launch of conky.
**sudo nano /local/usr/bin/conky-delayed.sh**
```
#! /bin/sh
sleep 10
conky
```
**sudo chmod +x /local/usr/bin/conky-delayed.sh**
Then add that script to sessions (e.g. "/local/usr/bin/conky-delayed.sh").

[COLOR="Red"]**However,**[/COLOR]
I think it's easier to just add this to sessions (no need to create a script and whatnot)
```
sh -c "sleep 10; conky"
```
since it does the above in only one step! :)

---

### Post by Diptansu on 2008-07-17
Thanx pelle.k, 

But as a newbie in linux unfortunately i didnt quite understand what u said ... :p

Wd u plzz explain these things in a bit lucid way ... 

Thanking again in anticipation ...:)

---

### Post by pelle.k on 2008-07-18
fair enough :)

put
```
sh -c "sleep 10; conky"
```
in the "command" box, when adding a new item in System > preferences > sessions. 10 is the number of seconds. you can set that to 15 or more if 10 isn't enough.

---

