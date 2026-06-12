---
title: "Conky Help"
date: 2008-08-04
forum: General Help
---

### Post by eximius1 on 2008-08-04
Sorry for reposting this here but I thought it more appropriate than the post your conky thread.

[[IMG]http://img227.imageshack.us/img227/1730/conkysetupyq1.th.png[/IMG]](http://img227.imageshack.us/my.php?image=conkysetupyq1.png)

My conkyrc file:

```
#	.conkyrc configuration
#	basics by Tristam Green, 11-21-2007
# 	edited by fusion.fake

# maintain spacing between certain elements
use_spacer yes

# set to yes if you want tormo to be forked in the background
#background yes

use_xft yes

# Xft font when Xft is enabled
xftfont Vera-8
#xftfont Andale Mono-9
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
#xftfont squaredance10:pixelsize=14
#xftfont swf!t_v02:pixelsize=10

# Text alpha when using Xft
xftalpha 1
mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_hints below

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 5
maximum_width 250

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 3

# border margins
border_margin 5

# border widt5
border_width 6

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey90
default_shade_color black
default_outline_color DarkGrey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 24
gap_y 24

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

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


# stuff after 'TEXT' will be formatted on screen

TEXT

${color white}${font OpenLogos:size=14}Dewi ${font}${font Vera:size=8}$alignr ${time %a } ${time %e %B %G} | ${time %I:%M %P}${font}
${color #5da5d3}User ${hr 1}
  ${color #e5e5e5}${execi 30 whoami} @ $nodename $alignr $sysname $machine $kernel
  ${color #e5e5e5}Intel Core 2 Duo T8100, 3GB, 8600GT
  ${color #e5e5e5}uptime $alignr $uptime_short

${color #5da5d3}System ${hr 1} 
  ${color #e5e5e5}cpu usage $color $alignr $cpu%
  ${color #e5e5e5}load $alignr $loadavg
  
${color #5da5d3}Processes ${hr 1}
  ${color #e5e5e5}total $alignr $processes
  ${color #e5e5e5}running $alignr $running_processes

${color #5da5d3}Memory ${hr 1}
  ${color #e5e5e5}total $alignr ${memmax}
  ${color #e5e5e5}used $alignr $memperc%  $mem

${color #5da5d3}Wired (${color #ff9900}${addr eth0}${color #5da5d3}) ${hr 1}
  ${color e5e5e5}down ${color #ff9900}${downspeedf eth0} ${color e5e5e5}k/s ${alignr}${color e5e5e5}up ${color #0000ff}${upspeedf eth0} ${color e5e5e5}k/s
  ${color e5e5e5}total down: ${totaldown eth0} $alignr total up: ${totalup eth0}

${color #5da5d3}File Systems ${hr 1}
  ${color #e5e5e5}Home ${color white}${fs_free /} (${fs_free_perc /}%) ${color #e5e5e5}free of ${fs_size /}
       ${fs_bar /}

${if_running rhythmbox}  ${color #e5e5e5}status $alignr active
  ${color #e5e5e5}title      ${execi 1 rhythmbox-client --print-playing-format "%aA -  %tT"}
  ${color #e5e5e5}album   ${execi 1 rhythmbox-client --print-playing-format "%aT (%ay)"} $alignr track ${exec rhythmbox-client --print-playing-format "%tn"}
  ${color #e5e5e5}time     ${exec rhythmbox-client --print-playing-format "%te / %td"}${else}  ${color #e5e5e5}status $alignr inactive
  ${color #e5e5e5}title      Not playing
  ${color #e5e5e5}album   Not playing $alignr track Not playing
  ${color #e5e5e5}time     Not playing${endif}

${execi 30 wmctrl -a conky}
```

I was wondering could anyone help me get wireless speed displaying, home directory (I've misnamed the one showing allready as home when it should be root) and getting rid of track in the rhythmbox section. Thanks.

---

### Post by easybake on 2008-08-04
> **eximius1 said:**
> 

I was wondering could anyone help me get wireless speed displaying, home directory (I've misnamed the one showing allready as home when it should be root) and getting rid of track in the rhythmbox section. Thanks.

for Home directory use  ```
${fs_free /home}
``` or ```
${fs_size /home}
```

For wireless, run in terminal ```
iwconfig
``` also check ```
ifconfig
```. Change your 'eth0' to something like 'wlan0' or 'wlan1' whatever you find when you run the configs. 

If you dont want track info displayed simply remove the ```
$alignr track ${exec rhythmbox-client --print-playing-format "%tn"}

```

---

### Post by eximius1 on 2008-08-05
Thanks everything is running nicely now.

---

### Post by Kain000 on 2008-08-06
Hey guys I used your .conkyrc file and changed a few things such as batt and the names like wireless, my name, system and whatnot.   Question tho, when I start conky via the terminal it works just fine, however when I select it as a start on boot app it puts itself , still working fine, on top of everything.  It still shares the background immage as if it were to the back but any windows are put under it and I cannot change that.  Just wondered if you knew a quick fix becore i start changing things in the .conkyrc file.
thanks
-sean

---

### Post by easybake on 2008-08-06
> **Kain000 said:**
> Hey guys I used your .conkyrc file and changed a few things such as batt and the names like wireless, my name, system and whatnot.   Question tho, when I start conky via the terminal it works just fine, however when I select it as a start on boot app it puts itself , still working fine, on top of everything.  It still shares the background immage as if it were to the back but any windows are put under it and I cannot change that.  Just wondered if you knew a quick fix becore i start changing things in the .conkyrc file.
thanks
-sean

You probably need a sleep script. Save this as blahblah in home directory. 
code]#!/bin/bash

sleep 30 &&
conky[/code]
then run this in terminal```
sudo chmod a+x blahblah
```
add blahblah to your sessions.

---

### Post by Kain000 on 2008-08-06
> **easybake said:**
> You probably need a sleep script. Save this as blahblah in home directory. 
code]#!/bin/bash

sleep 30 &&
conky[/code]
then run this in terminal```
sudo chmod a+x blahblah
```
add blahblah to your sessions.

alright it didnt work but i think I've done it wrong.   so first I ran a sudo gedit command.

next I inputed 
]#!/bin/bash

sleep 30 &&
conky

and saved as blahblah in my home folder.
then the sudo chmod command
and finally I pointed the startup app searching for .exe files to blahblah in my home folder.    

upon reboot no changes but when I went to close conky via the system monitor, there were two instances active.

---

### Post by easybake on 2008-08-06
> **Kain000 said:**
> alright it didnt work but i think I've done it wrong.   so first I ran a sudo gedit command.

next I inputed 
]#!/bin/bash

sleep 30 &&
conky

and saved as blahblah in my home folder.
then the sudo chmod command
and finally I pointed the startup app searching for .exe files to blahblah in my home folder.    

upon reboot no changes but when I went to close conky via the system monitor, there were two instances active.

Remove your original conky listing from your sessions menu and only use Blahblah

---

### Post by Kain000 on 2008-08-06
> **easybake said:**
> Remove your original conky listing from your sessions menu and only use Blahblah

My friend, 

YOU RULE!!!  thanks alot
   so this is called a sleep script?  so i gather from #!/bin/bash

sleep 30 &&
conky

it tells bash to wait 30 secs before running the conky command?   what does the #!/bin/bash mean   (i know that bash is borne again shell) but thats about it.

---

### Post by easybake on 2008-08-06
> **Kain000 said:**
> My friend, 

YOU RULE!!!  thanks alot
   so this is called a sleep script?  so i gather from #!/bin/bash

sleep 30 &&
conky

it tells bash to wait 30 secs before running the conky command?   what does the #!/bin/bash mean   (i know that bash is borne again shell) but thats about it.
No problem. Sleep script is just a nickname for it because it contains a sleep command. 30 does mean seconds, you can change it to whatever you want. /bin/bash just tells the system to use Bash to run it. You can use scripts for a lot different things, changing your wallpaper depending on what time it is, launching multiple conkys, or have conky check the weather or your emails for you.

---

