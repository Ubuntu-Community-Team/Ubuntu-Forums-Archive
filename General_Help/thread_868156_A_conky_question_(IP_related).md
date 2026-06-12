---
title: "A conky question (IP related)"
date: 2008-07-23
forum: General Help
---

### Post by wolfe on 2008-07-23
How can I make conky show my external IP address?  Is there a way to query whatismyipaddress.com?

---

### Post by easybake on 2008-07-23
> **wolfe said:**
> How can I make conky show my external IP address?  Is there a way to query whatismyipaddress.com?


Put this in your conkyrc
```
${execi 3600 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}
```

---

### Post by wolfe on 2008-07-23
thanks so much, works perfectly!

---

### Post by bluesfreak72 on 2009-02-22
I've had this working for quite some time, but it stopped working this morning.  I have this in my ~/.conkyrc file:

${execi 600 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}

It used to get my external IP, but now it's displaying

(html)(body)(h1)It Works(/h1)(/body)(/html)

(Replace parentheses with angle brackets)

This is also what I get when I view the source of the [http://whatismyip.org](http://whatismyip.org) site.  Does anybody know of another site I can query to display my external IP in conky???

Thanks in advance,
Scott

---

### Post by Ng Oon-Ee on 2009-02-23
> **bluesfreak72 said:**
> I've had this working for quite some time, but it stopped working this morning.  I have this in my ~/.conkyrc file:

${execi 600 wget -O - [http://whatismyip.org/](http://whatismyip.org/) | tail}

It used to get my external IP, but now it's displaying

(html)(body)(h1)It Works(/h1)(/body)(/html)

(Replace parentheses with angle brackets)

This is also what I get when I view the source of the [http://whatismyip.org](http://whatismyip.org) site.  Does anybody know of another site I can query to display my external IP in conky???

Thanks in advance,
Scott
I use the following:-

```
execi 3600 wget -O - http://ip.tupeux.com | tail
```

Got it from one of the .conkyrc files posted up in that humongous thread.

---

### Post by hectic1 on 2009-09-05
> **Ng Oon-Ee said:**
> I use the following:-

```
execi 3600 wget -O - http://ip.tupeux.com | tail
```

Got it from one of the .conkyrc files posted up in that humongous thread.

man thank you!! i still dunno why whatismyip dindn't show any info for me,if i'd use the link in my browser it would work but not in conky,lol
this works just fine tough! ty

---

### Post by redDEADresolve on 2009-12-21
Do these commands continually check the ip or just do it once at start up?

I don't want it checking every second.

---

### Post by 5BallJuggler on 2009-12-21
> **redDEADresolve said:**
> Do these commands continually check the ip or just do it once at start up?

I don't want it checking every second.

```
execi 3600 wget -O - http://ip.tupeux.com | tail
```

the "execi 3600" part of the command means run this every 3600 second

Phil

---

### Post by redDEADresolve on 2009-12-21
> **5BallJuggler said:**
> ```
execi 3600 wget -O - http://ip.tupeux.com | tail
```

the "execi 3600" part of the command means run this every 3600 second

Phil

I guess I should think before I type, thanks. As soon as I read that I realized how obvious it was.

If there anyway to get it to just run once?

---

### Post by 5BallJuggler on 2009-12-21
just increase the number to an overly large value....

65535 should do it.

Phil

---

### Post by StuartN on 2009-12-21
whatismyip.com will lock out automated requests that recur too frequently, so use the provided automation page [www.whatismyip.com/automation/n09230945.asp](www.whatismyip.com/automation/n09230945.asp) and wait at least 300 seconds between accesses.

The whatismyip.com home page includes this comment:
```
<!--Please set your code to scrape your IP from **_www.whatismyip.com/automation/n09230945.asp_** For more info, please see our "Recommended Automation Practices" thread in the Forum.-->
```

---

### Post by gcndavidmn on 2010-08-12
I am very new to conky so please be patient.

What should the line in .conkyrc actually look like?

I presume it's more than:
```
External IP: execi 3600 wget -O - http://ip.tupeux.com | tail
```

---

### Post by mobilediesel on 2010-08-12
> **gcndavidmn said:**
> I am very new to conky so please be patient.

What should the line in .conkyrc actually look like?

I presume it's more than:
```
External IP: execi 3600 wget -O - http://ip.tupeux.com | tail
```

You had it pretty close, try this:
```
External IP: ${execi 3600 wget -O - http://ip.tupeux.com | tail}
```
or even:
```
External IP: ${execi 3600 curl -s http://www.whatismyip.com/automation/n09230945.asp}
```

---

### Post by gcndavidmn on 2010-08-12
That didn't work, am I putting it in the correct location?

```
NETWORK ${hr 2}${if_existing /proc/net/route wlan0}
Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,70 BEBEBE BEBEBE}
Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,70 BEBEBE BEBEBE}
Upload: ${alignr}${totalup wlan0}
Download: ${alignr}${totaldown wlan0}
Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,70 wlan0}
Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,70 789E2D A7CC5C}
Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,70 789E2D A7CC5C}
Upload: ${alignr}${totalup eth0}
Download: ${alignr}${totaldown eth0}
Local Ip: ${alignr}${addr eth0}
${endif}${else}${if_existing /proc/net/route eth1}
Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,70 789E2D A7CC5C}
Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,70 789E2D A7CC5C}
Upload: ${alignr}${totalup eth1}
Download: ${alignr}${totaldown eth1}
Local IP: ${alignr}${addr eth1}
External IP: ${execi 3600 curl -s http://www.whatismyip.com/automation/n09230945.asp}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
```

---

### Post by mobilediesel on 2010-08-12
> **gcndavidmn said:**
> That didn't work, am I putting it in the correct location?

```
NETWORK ${hr 2}${if_existing /proc/net/route wlan0}
Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,70 BEBEBE BEBEBE}
Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,70 BEBEBE BEBEBE}
Upload: ${alignr}${totalup wlan0}
Download: ${alignr}${totaldown wlan0}
Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,70 wlan0}
Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,70 789E2D A7CC5C}
Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,70 789E2D A7CC5C}
Upload: ${alignr}${totalup eth0}
Download: ${alignr}${totaldown eth0}
Local Ip: ${alignr}${addr eth0}
${endif}${else}${if_existing /proc/net/route eth1}
Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,70 789E2D A7CC5C}
Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,70 789E2D A7CC5C}
Upload: ${alignr}${totalup eth1}
Download: ${alignr}${totaldown eth1}
Local IP: ${alignr}${addr eth1}
External IP: ${execi 3600 curl -s http://www.whatismyip.com/automation/n09230945.asp}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}
```

Yeah that's the right place. Maybe curl isn't installed on your system. Try the other one with wget:
```
External IP: ${execi 3600 wget -O - http://ip.tupeux.com | tail}
```

---

### Post by gcndavidmn on 2010-08-12
Hmm... curl wasn't installed.

I tried the wget version and still now joy. I also installed curl then tried the curl version, still no joy.

---

### Post by mobilediesel on 2010-08-12
> **gcndavidmn said:**
> Hmm... curl wasn't installed.

I tried the wget version and still now joy. I also installed curl then tried the curl version, still no joy.

Let's see your whole .conkyrc file, maybe there's something else missing that I can't think of yet.

---

### Post by gcndavidmn on 2010-08-12
Here it is:
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
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 150

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 0

# border width
border_width 0

# Default colors and also border colors
default_color black
#default_shade_color black
#default_outline_color grey
own_window_colour grey

# Text alignment, other possible values are commented
#alignment top_left
alignment middle_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 35

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

${alignc 10}${font Arial Black:size=12}Davidmn${font}
${alignc}Love Linux!

Kernel:  ${alignr}${kernel}
CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,70}
CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,70}
CPU3: ${cpu cpu3}% ${alignr}${cpubar cpu3 8,70}
CPU4: ${cpu cpu4}% ${alignr}${cpubar cpu4 8,70}
RAM: $memperc% ${alignr}${membar 8,70}
SWAP: $swapperc% ${alignr}${swapbar 8,70}
Uptime: ${alignr}${uptime}

${alignc 10}${font Arial Black:size=12}${time %H:%M}${font}
${alignc}${time %A %d %B %Y}

NETWORK ${hr 2}${if_existing /proc/net/route wlan0}
Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,70 BEBEBE BEBEBE}
Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,70 BEBEBE BEBEBE}
Upload: ${alignr}${totalup wlan0}
Download: ${alignr}${totaldown wlan0}
Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,70 wlan0}
Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,70 789E2D A7CC5C}
Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,70 789E2D A7CC5C}
Upload: ${alignr}${totalup eth0}
Download: ${alignr}${totaldown eth0}
Local Ip: ${alignr}${addr eth0}
${endif}${else}${if_existing /proc/net/route eth1}
Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,70 789E2D A7CC5C}
Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,70 789E2D A7CC5C}
Upload: ${alignr}${totalup eth1}
Download: ${alignr}${totaldown eth1}
Local IP: ${alignr}${addr eth1}
External IP: ${execi 3600 curl -s http://www.whatismyip.com/automation/n09230945.asp}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}

PROCESSES ${hr 2}
NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}

```

---

### Post by mobilediesel on 2010-08-12
> **gcndavidmn said:**
> Here it is:

ahhhhh almost, you have it looking for two possible network adapters. I added the code for the external IP in the first **${if_existing /proc/net/route** section, you only had it in the second section.
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
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 180 0
#maximum_width 150

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 0

# border margins
border_margin 0

# border width
border_width 0

# Default colors and also border colors
default_color black
#default_shade_color black
#default_outline_color grey
own_window_colour grey

# Text alignment, other possible values are commented
#alignment top_left
alignment middle_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 5
gap_y 35

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

${alignc 10}${font Arial Black:size=12}Davidmn${font}
${alignc}Love Linux!

Kernel:  ${alignr}${kernel}
CPU1: ${cpu cpu1}% ${alignr}${cpubar cpu1 8,70}
CPU2: ${cpu cpu2}% ${alignr}${cpubar cpu2 8,70}
CPU3: ${cpu cpu3}% ${alignr}${cpubar cpu3 8,70}
CPU4: ${cpu cpu4}% ${alignr}${cpubar cpu4 8,70}
RAM: $memperc% ${alignr}${membar 8,70}
SWAP: $swapperc% ${alignr}${swapbar 8,70}
Uptime: ${alignr}${uptime}

${alignc 10}${font Arial Black:size=12}${time %H:%M}${font}
${alignc}${time %A %d %B %Y}

NETWORK ${hr 2}${if_existing /proc/net/route wlan0}
Up: ${upspeed wlan0} kb/s ${alignr}${upspeedgraph wlan0 8,70 BEBEBE BEBEBE}
Down: ${downspeed wlan0} kb/s ${alignr}${downspeedgraph wlan0 8,70 BEBEBE BEBEBE}
Upload: ${alignr}${totalup wlan0}
Download: ${alignr}${totaldown wlan0}
Signal: ${wireless_link_qual wlan0}% ${alignr}${wireless_link_bar 8,70 wlan0}
Local Ip: ${alignr}${addr wlan0}
${else}${if_existing /proc/net/route eth0}
Up: ${upspeed eth0} kb/s ${alignr}${upspeedgraph eth0 8,70 789E2D A7CC5C}
Down: ${downspeed eth0} kb/s ${alignr}${downspeedgraph eth0 8,70 789E2D A7CC5C}
Upload: ${alignr}${totalup eth0}
Download: ${alignr}${totaldown eth0}
Local Ip: ${alignr}${addr eth0}
External IP: ${execi 3600 curl -s http://www.whatismyip.com/automation/n09230945.asp}
${endif}${else}${if_existing /proc/net/route eth1}
Up: ${upspeed eth1} kb/s ${alignr}${upspeedgraph eth1 8,70 789E2D A7CC5C}
Down: ${downspeed eth1} kb/s ${alignr}${downspeedgraph eth1 8,70 789E2D A7CC5C}
Upload: ${alignr}${totalup eth1}
Download: ${alignr}${totaldown eth1}
Local IP: ${alignr}${addr eth1}
External IP: ${execi 3600 curl -s http://www.whatismyip.com/automation/n09230945.asp}
${endif}${else}
${font PizzaDude Bullets:size=14}4${font}   Network Unavailable
${endif}

PROCESSES ${hr 2}
NAME $alignr PID    CPU
${top name 1} $alignr ${top pid 1} ${top cpu 1}
${top name 2} $alignr ${top pid 2} ${top cpu 2}
${top name 3} $alignr ${top pid 3} ${top cpu 3}
${top name 4} $alignr ${top pid 4} ${top cpu 4}
${top name 5} $alignr ${top pid 5} ${top cpu 5}
```

---

### Post by gcndavidmn on 2010-08-12
Brilliant! Thank you very much :)

---

### Post by mobilediesel on 2010-08-12
> **gcndavidmn said:**
> Brilliant! Thank you very much :)

You're welcome! I thought it had to be something simple. It was simple enough that I looked right past it a couple times before I saw it!

---

