---
title: "Conky help for a noob"
date: 2008-10-18
forum: General Help
---

### Post by Radiotic on 2008-10-18
I'm pretty new to Ubuntu, and linux in general. So forgive me if this is a stupid question or has been covered in other posts. 

I'd like to get a conky system monitor going on my desktop, so I installed conky and ran it. It displayed in windowed mode, so I took a tutorial to get it on desktop, but something went wrong. Now when I try to run conky, I get this message: Conky: missing text block in configuration; exiting

I tried uninstalling/reinstalling but results are the same. My aim is to get something like vertigo-'s config as listed on this [thread]("http://ubuntuforums.org/showthread.php?t=281865&highlight=nvidia&page=7"), [screenshot]("http://splenetic.info/screenshots/screenshot_blue2-1.png"). I'm particularly interested in getting a temperature and fan speed monitor, but some weather would be cool too. 

Cheers.

---

### Post by rjmdomingo2003 on 2008-10-18
> **Radiotic said:**
> I'm pretty new to Ubuntu, and linux in general. So forgive me if this is a stupid question or has been covered in other posts. 

I'd like to get a conky system monitor going on my desktop, so I installed conky and ran it. It displayed in windowed mode, so I took a tutorial to get it on desktop, but something went wrong. Now when I try to run conky, I get this message: Conky: missing text block in configuration; exiting

I tried uninstalling/reinstalling but results are the same. My aim is to get something like vertigo-'s config as listed on this [thread]("http://ubuntuforums.org/showthread.php?t=281865&highlight=nvidia&page=7"), [screenshot]("http://splenetic.info/screenshots/screenshot_blue2-1.png"). I'm particularly interested in getting a temperature and fan speed monitor, but some weather would be cool too. 

Cheers.
Could you post your .conkyrc?
```
gedit ~/.conkyrc
```

---

### Post by Radiotic on 2008-10-18
It's empty.

---

### Post by rjmdomingo2003 on 2008-10-18
> **Radiotic said:**
> It's empty.
OK, do this:
```
gedit ~/.conkyrc
```

then paste this:
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

maximum_width 143 5
minimum_size 143 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 4

# border margins
border_margin 2

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

#own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 2
gap_y 20

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 0}${color white}uptime: ${color }$uptime
${offset 0}${color white}kernel: ${color }$kernel
${offset 0}${color white}battery:${color } ${battery}
${offset 0}${color white}fan: ${ibm_fan}rpm
${offset 0}${color white}temp:
${offset 0}${color white} hda: ${hddtemp /dev/hda}
${offset 0}${color white} c1: ${ibm_temps 1}C
${offset 0}${color white} c2: ${ibm_temps 2}C
${offset 0}${color white} gpu: ${ibm_temps 3}C
${offset 0}${color white} cpu: ${ibm_temps 0}C
${offset 0}${color white}cpu:${color } $cpu%
${offset 0}${cpugraph 20,130 cccccc ffffff}
${offset 0}${color white}load: ${color }$loadavg
${offset 0}${color white}processes: ${color }$processes  
${offset 0}${color white}running: ${color }$running_processes

${offset 0}${color white}top cpu time:
${offset 0}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 0}${color white} ${top name 2}${top cpu 2}
${offset 0}${color white} ${top name 3}${top cpu 3}
${offset 0}${color white} ${top name 4}${top cpu 4}

${offset 0}${color white}top mem:
${offset 0}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 0}${color white} ${top_mem name 2}${top_mem mem 2}
${offset 0}${color white} ${top_mem name 3}${top_mem mem 3}
${offset 0}${color white} ${top_mem name 4}${top_mem mem 4}

${offset 0}${color white}ram:
${color }$memperc% $mem/$memmax
${offset 0}${membar 3,100}
${offset 0}${color white}swap:
${color }$swapperc% $swap/$swapmax
${offset 0}${swapbar 3,100}
${offset 0}${color white}root:
${color }${fs_free /}/${fs_size /}
${offset 0}${fs_bar 3,100 /}
${offset 0}${color white}net:
${offset 0}${color} wlan signal: ${color }${linkstatus eth1}%
${offset 0}${color} ip: ${addr eth1}
${offset 0}${color}up: ${color }${upspeed eth1} k/s
${offset 0}${upspeedgraph eth1 20,130 000000 ffffff}
${offset 0}${color}down: ${color }${downspeed eth1}k/s${color}
${offset 0}${downspeedgraph eth1 20,130 000000 ffffff}
```

Save, then, 
```
conky &
```

Then,
```
exit
```

---

### Post by Radiotic on 2008-10-18
OK, things are happening now. I guess there's a compatibility issue. My laptop is an Asus, not IBM. 

```
is@is-laptop:~$ conky &
[1] 20699
is@is-laptop:~$ Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: unknown variable linkstatus
Conky: forked to background, pid is 20700

Conky: desktop window (1200251) is subwindow of root window (5d)
Conky: window type - override
Conky: drawing to created window (4200001)
Conky: drawing to double buffer
Conky: can't open '/proc/acpi/ibm/fan': No such file or directory
You are not using the IBM ACPI. Remove ibm* from your Conky config file.

```

---

### Post by rjmdomingo2003 on 2008-10-18
> **Radiotic said:**
> OK, things are happening now. I guess there's a compatibility issue. My laptop is an Asus, not IBM. 

```
is@is-laptop:~$ conky &
[1] 20699
is@is-laptop:~$ Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: unknown variable linkstatus
Conky: forked to background, pid is 20700

Conky: desktop window (1200251) is subwindow of root window (5d)
Conky: window type - override
Conky: drawing to created window (4200001)
Conky: drawing to double buffer
Conky: can't open '/proc/acpi/ibm/fan': No such file or directory
You are not using the IBM ACPI. Remove ibm* from your Conky config file.

```

Some of the variables aren't "compatible". Again paste this:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

maximum_width 143 5
minimum_size 143 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 4

# border margins
border_margin 2

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

#own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 2
gap_y 20

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 0}${color white}uptime: ${color }$uptime
${offset 0}${color white}kernel: ${color }$kernel
${offset 0}${color white}battery:${color } ${battery}
${offset 0}${color white} cpu: ${ibm_temps 0}C
${offset 0}${color white}cpu:${color } $cpu%
${offset 0}${cpugraph 20,130 cccccc ffffff}
${offset 0}${color white}load: ${color }$loadavg
${offset 0}${color white}processes: ${color }$processes  
${offset 0}${color white}running: ${color }$running_processes

${offset 0}${color white}top cpu time:
${offset 0}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 0}${color white} ${top name 2}${top cpu 2}
${offset 0}${color white} ${top name 3}${top cpu 3}
${offset 0}${color white} ${top name 4}${top cpu 4}

${offset 0}${color white}top mem:
${offset 0}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 0}${color white} ${top_mem name 2}${top_mem mem 2}
${offset 0}${color white} ${top_mem name 3}${top_mem mem 3}
${offset 0}${color white} ${top_mem name 4}${top_mem mem 4}

${offset 0}${color white}ram:
${color }$memperc% $mem/$memmax
${offset 0}${membar 3,100}
${offset 0}${color white}swap:
${color }$swapperc% $swap/$swapmax
${offset 0}${swapbar 3,100}
${offset 0}${color white}root:
${color }${fs_free /}/${fs_size /}
${offset 0}${fs_bar 3,100 /}
```

---

### Post by Radiotic on 2008-10-18
It still references IBM. I tried another config file from that same thread and it works. How do I turn that one off now?

```
is@is-laptop:~$ conky &
[1] 21583
is@is-laptop:~$ Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: forked to background, pid is 21584

Conky: desktop window (1200251) is subwindow of root window (5d)
Conky: window type - override
Conky: drawing to created window (4600001)
Conky: drawing to double buffer
Conky: can't open '/proc/acpi/ibm/thermal': No such file or directory
You are not using the IBM ACPI. Remove ibm* from your Conky config file.

```

---

### Post by rjmdomingo2003 on 2008-10-18
> **rjmdomingo2003 said:**
> Some of the variables aren't "compatible". Again paste this:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_hints undecorated,below,skip_taskbar
background yes

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

maximum_width 143 5
minimum_size 143 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 4

# border margins
border_margin 2

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

#own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 2
gap_y 20

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 0}${color white}uptime: ${color }$uptime
${offset 0}${color white}kernel: ${color }$kernel
${offset 0}${color white}battery:${color } ${battery}
[COLOR="Red"]${offset 0}${color white} cpu: ${ibm_temps 0}C[/COLOR]
${offset 0}${color white}cpu:${color } $cpu%
${offset 0}${cpugraph 20,130 cccccc ffffff}
${offset 0}${color white}load: ${color }$loadavg
${offset 0}${color white}processes: ${color }$processes  
${offset 0}${color white}running: ${color }$running_processes

${offset 0}${color white}top cpu time:
${offset 0}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 0}${color white} ${top name 2}${top cpu 2}
${offset 0}${color white} ${top name 3}${top cpu 3}
${offset 0}${color white} ${top name 4}${top cpu 4}

${offset 0}${color white}top mem:
${offset 0}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 0}${color white} ${top_mem name 2}${top_mem mem 2}
${offset 0}${color white} ${top_mem name 3}${top_mem mem 3}
${offset 0}${color white} ${top_mem name 4}${top_mem mem 4}

${offset 0}${color white}ram:
${color }$memperc% $mem/$memmax
${offset 0}${membar 3,100}
${offset 0}${color white}swap:
${color }$swapperc% $swap/$swapmax
${offset 0}${swapbar 3,100}
${offset 0}${color white}root:
${color }${fs_free /}/${fs_size /}
${offset 0}${fs_bar 3,100 /}
```

Remove the one in RED.

If you have one config which works, then just overwrite this one, and save. Good luck!

---

### Post by Radiotic on 2008-10-18
Great. Thanks for the help. 

I've got a nice one working and will try to customize it a bit from other people's configurations. 

It turned out to be a lot easier than I expected, encouragement for the learning still to come. Thanks again.

---

### Post by rjmdomingo2003 on 2008-10-18
> **Radiotic said:**
> Great. Thanks for the help. 

I've got a nice one working and will try to customize it a bit from other people's configurations. 

It turned out to be a lot easier than I expected, encouragement for the learning still to come. Thanks again.
Check out kaivalagi's tutes (see his sig): [http://ubuntuforums.org/showthread.php?t=869328&highlight=conky](http://ubuntuforums.org/showthread.php?t=869328&highlight=conky)

---

