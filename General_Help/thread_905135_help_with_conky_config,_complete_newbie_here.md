---
title: "help with conky config, complete newbie here"
date: 2008-08-30
forum: General Help
---

### Post by negativezero-0 on 2008-08-30
Can someone help me take something from one conky config I found and add it to the one I'm currently using? Like I said, I'm a complete newbie at all this and have pretty much no idea how to customize this all on my own! :P

Also, considering the former statement, I don't know how much work it is to do what I'm asking, so if it'll take more than 5 minutes just try to explain how to change it to me, so I can just do it myself.

Here's the config I'm currently using:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 1.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase yes # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, green90 == #e5e5e5
default_color green
default_shade_color black
default_outline_color green

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

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color green}${time %a, } ${color }${time %e %B %G}
${offset 240}${color green}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color green}UpTime: ${color }$uptime
${offset 240}${color green}Kern:${color }$kernel
${offset 240}${color green}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color green}Load: ${color }$loadavg
${offset 240}${color green}Processes: ${color }$processes  
${offset 240}${color green}Running:   ${color }$running_processes


${offset 240}${color green}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color green}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color green}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color  green}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}

${offset 240}${color green}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

```

And here's the thing I want to add to it (I'd like to keep all the color and text settings from my current config):

```
${color #FFFFFF}$hr

 ${color #FFFFFF}Connections in:${color #FFFFFF} ${tcp_portmon 1 32767 count}${color #FFFFFF} Connections    out:${color #FFFFFF} ${tcp_portmon 32768 61000 count}${color #FFFFFF} Total:${color #FFFFFF}    ${tcp_portmon 1 65535 count}

${color #FFFFFF} Inbound Connection ${alignr} Local Service/Port
${color {color #FFFFFF}} ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767    lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
${color #FFFFFF} Outbound Connection ${alignr} Remote Service/Port$color
${color #00FF09} ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon    32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice    1}
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice    2}
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice    3}
 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice    4}
 ${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice    5}
 ${tcp_portmon 32768 61000 rhost 6} ${alignr} ${tcp_portmon 32768 61000 rservice    6}
 ${tcp_portmon 32768 61000 rhost 7} ${alignr} ${tcp_portmon 32768 61000 rservice    7}
 ${tcp_portmon 32768 61000 rhost 8} ${alignr} ${tcp_portmon 32768 61000 rservice    8}
 ${tcp_portmon 32768 61000 rhost 9} ${alignr} ${tcp_portmon 32768 61000 rservice    9}
 ${tcp_portmon 32768 61000 rhost 10} ${alignr} ${tcp_portmon 32768 61000 rservice   10}
$color$hr
```

Thanks to anyone who helps at all :) and if I'm asking too much just tell me and ignore my post :P

---

### Post by loomsen on 2008-08-30
Alright, so... Add it :)

But, what I dont understand, y do u start every line with $offset 240?

Makes no sense at all... Try to understand the arguments.

First, the stuff where u can comment out using #
This is the options part, where you tell conky what he is and what he shall look like. 
```

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

gap_x 10
gap_y 10
```

tells your conky where to be. So, as you decided to align top_right 
gap_x will make conky your conky leave a gap of 10 pixels towards the right edge of your screen, so actually moves it to the left.
Gap_y moves it down.

If you had chosen bottom_right for example gap_y would have moved it up 10 pixels.

So, 1st, by specifying gaps you always move towards the middle of your screen, depending where u chosen to align it at. Got that?

So, offseting every line is like 2>/dev/null.
Discardable.

So first I'd say delete this files, simplay add what u wanna add to ur conky to the bottom of it. 
Then you gotta just toy around wie spaces, offsets and gotos until your conky is formatted that way you want it to be

You might want to make softlinks instead of always editing your ~/.conkyrc...

For example, I created a directory in my home dir called configs, where I got everything configurable stored. this way you may name your conkys however you want to, making it easier to handle different configurations.
I have a couple of different configs, one small topbar, named conky-1-bar, one conky drawing 2 lines on top op my screen, named conky-2-bar, one bigger sidebarconky, named conky_sidebar and so on. 

Then, by running
```

ln -s ~/configs/conky/conky_sidebar ~/.conkyrc 
```

You will create a softlink. Its way easier to edit the files this way, toggle through your conkys, keeping your homedirectory clean, and so on.

Then, after you added what u want to add, startup a terminal, and start your conky, just by typing conky if you linked it like the box says before.conky will start up, you should have your conky-file open in gedit for example. 

Then you just gotta see whats good, and what you'd like to change. Change the file, save it leaving it open (this will not break your link)

and type
```
 killall conky && sleep 1 && conky

``` 
into a terminal. This will allow you to edit your conky almost instantly.

Have fun :)


*edit*
What you might want to know too, there is also a ${voffset n} command, where n is the number of pixel you want an argument to be moved on screen. 

What you r doing is to tell conky it has 400 Pixel space, adding your gap_x 10, it will start at 410 Pixel from the right side of your screen. But then you push him back again, so u might just specify a smaller width, and delete the offset arguments out of every file.


```

# Minimum size of text area
minimum_size 400 5

``` 

change this line to:
```

# Minimum size of text area
minimum_size 160 5
maximum_width 160

```
which is basically what you want :) 

And so on, you gotta learn it by doing, no other way, unless you r able to make up pictures out of lines and lines of code.

---

### Post by negativezero-0 on 2008-08-30
Well you have to understand that I didn't write any of this, it's just tweaked by me :) I got it off of several different configs I liked. So some of the stuff you said was a little confusing but I think I can figure it out, thanks :)

---

