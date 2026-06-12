---
title: "Help: Xcompmgr won't play nice with Conky?"
date: 2008-10-15
forum: General Help
---

### Post by Alucard-sama on 2008-10-15
I'm trying to get xcompmgr working in fluxbox and everything was going shweet until I tried to run it and all my windows disappeared (including the taskbar). After a little troubleshooting I found the culprit; Conky.
My guess is Conky is having it's window drawn on top of the rest of the windows and this is what's causing them to seemingly "disappear".
Tried setting "own_window" in .conkyrc to "no" but that didn't help at all.
Anybody know how to stop this?

P.S: .conkyrc looks like this -
> # UBUNTU-CONKY
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
# own_window yes
# own_window_type override
# own_window_transparent yes
# own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

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

# own_window no
own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color orange}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color orange}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
Music:  ${fs_free_perc /home/alucard-sama/Music}%   ${fs_bar 6 /home/alucard-sama/Music}$color
Home:  ${fs_free_perc /home}%   ${fs_bar 6 /home}

${color orange}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color orange}FORTUNE ${hr 2}$color
${execi 120 fortune -s | fold -w50}

---

### Post by loomsen on 2008-10-15
Well, posting your conky could be sth to consider if you have problems with it, don't you think?

However, there are some more options for own_window in conky.

[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

Since one of the recent updates conky however works for me without own_window... Running intrepid here.

Else you could try and specify a window when launchig conky, telling it which window to draw to.

You might want to install xwininfo with the common command to get simple yet very useful infos about all of your windows.

---

### Post by Alucard-sama on 2008-10-16
> Well, posting you're conky could be sth to consider if you have problems with it, don't you think?

Good point.

---

### Post by loomsen on 2008-10-16
You still gotta specify your own_window style.

Just try different options, like:

```
own_window no
```

```

own_window yes
## if own window true, specify a background
background color
own_window_type normal  ## other values you could give a shot: desktop, root, normal, override
own_window_transparent yes  ## if own window true, this will enable FAKE-ARGB!
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

```

I, i.e., had this in my conky options before own_window no worked:
```

own_window	yes
own_window_transparent	yes
own_window_type		normal
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager
background white

```


*edit*
A hint which you might find useful... While configuring conky leave a terminal open with two tabs, and take this cmd:
```

killall conky && sleep 2 && conky &

```

To quickly have your conky restarted.

---

### Post by richardq on 2008-10-27
I've been trying off and on to get Conky to play nicely with xcompmgr (more specifically, so that Conky won't be drawn with a drop shadow). Up till now I haven't had much success. But using the settings in this post ([http://crunchbang.org/archives/2008/03/02/openbox-xcompmgr-transset-and-conky/](http://crunchbang.org/archives/2008/03/02/openbox-xcompmgr-transset-and-conky/)) It actually seems to work!!!

So I've got Openbox running xcompmgr with just drop shadows and conky running without a drop shadow around the conky window. I still don't get the correct drop shadows around my gnome-terminal window (xterm looks fine though).

Hope that helps.

RQ

---

