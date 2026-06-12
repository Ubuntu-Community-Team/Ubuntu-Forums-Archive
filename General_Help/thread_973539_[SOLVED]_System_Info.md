---
title: "[SOLVED] System Info?"
date: 2008-11-06
forum: General Help
---

### Post by Yezinki on 2008-11-06
Hi there,

How does one check System Info like CPU , Memory usage, drives, partitions etc. in Ubuntu 8.10?

Regards,

Yezinki.

---

### Post by ww711 on 2008-11-06
System monitor is quite comprehensive for information about your system.

Conky is good application for this too.

---

### Post by cariboo on 2008-11-06
There are several commands, for cpu info:

```
cat /proc/cpuinfo
```

for memory usage:

```
free -m
```

for drive usage info:

```
df -h
```

for partition info:

```
sudo fdisk -l
```

For complete hardware info:

```
sudo lshw
```

Jim

---

### Post by Yezinki on 2008-11-06
> **cariboo907 said:**
> There are several commands, for cpu info:

```
cat /proc/cpuinfo
```

for memory usage:

```
free -m
```

for drive usage info:

```
df -h
```

for partition info:

```
sudo fdisk -l
```

For complete hardware info:

```
sudo lshw
```

Jim


Thanks Jim for such a prompt reply which I appreciate.

Is their a desktop utility also, to monitor or check these......not just by using commands in the terminal ?

Regards,

Yezinki.

---

### Post by Sam on 2008-11-06
Install [sysinfo](apt://sysinfo) or [hardinfo](apt://hardinfo).

---

### Post by Yezinki on 2008-11-06
> **ww711 said:**
> System monitor is quite comprehensive for information about your system.

Conky is good application for this too.

What is Conky.....can I use it in Ubuntu........where do I get to install/ download it?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-06
> **Sam said:**
> Install [sysinfo](apt://sysinfo) or [hardinfo](apt://hardinfo).

Thanks where did it get installed?

Regards,

Yezinki.

---

### Post by Sam on 2008-11-06
> **Yezinki said:**
> Thanks where did it get installed?

Regards,

Yezinki.

Applications > System Tools

---

### Post by Sam on 2008-11-06
> **Yezinki said:**
> What is Conky.....can I use it in Ubuntu........where do I get to install/ download it?

Regards,

Yezinki.

Read this: [http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html)

There is a lot of documentation on the web or in these forums.

---

### Post by Yezinki on 2008-11-06
Hi there thanks every one,

I did install Conky now where is it?

Regards,

Yezinki.

---

### Post by Sam on 2008-11-06
> **Yezinki said:**
> Hi there thanks every one,

I did install Conky now where is it?

Regards,

Yezinki.

You have to put your settings in the file .conkyrc in your home directory. See the link I provided above for an example. Then start conky with the command "conky" or using the session manager (see link above).

You can run "man conky" for a list of all available settings that you can put in your ~/.conkyrc file.

---

### Post by Bucky Ball on 2008-11-06
System->Administration->System Monitor.

---

### Post by Yezinki on 2008-11-06
1.What screen resolution should I keep .....at the moment is 640x800.......with windows XP MCE installed its 1600 X 1200?

2. How do I refresh the screen?

3. Cannot find conky file in home?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-06
> **Bucky Ball said:**
> System->Administration->System Monitor.

Hi,

Whats the difference btw Ubuntu Hardy, Studio Hardy & Hardy blend 8.04?

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-06
[B]ubuntu@ubuntu-laptop:~$ sudo apt-get install conky
[sudo] password for ubuntu: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
conky is already the newest version.
The following packages were automatically installed and are no longer required:
  libsvga1 libglide2 libggi-target-x libggi2 libgii1 libgii1-target-x
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu-laptop:~$ 
[/B]

---

### Post by Yezinki on 2008-11-07
[B]ubuntu@ubuntu-laptop:~$ sudo apt-get install conky
Reading package lists... Done
Building dependency tree       
Reading state information... Done
conky is already the newest version.
The following packages were automatically installed and are no longer required:
  libsvga1 libglide2 libggi-target-x libggi2 libgii1 libgii1-target-x
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu-laptop:~$ apt -get autoremove
The program 'apt' can be found in the following packages:
 * cacao-oj6-jdk
 * openjdk-6-jdk
 * sun-java5-jdk
 * sun-java6-jdk
Try: sudo apt-get install <selected package>
bash: apt: command not found
ubuntu@ubuntu-laptop:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ubuntu@ubuntu-laptop:~$ y
[/B]

What should I do now?

Regards,

Yezinki.

---

### Post by Sam on 2008-11-07
Conky is installed on your system. To get rid of the autoremove message, run:
```
sudo apt-get autoremove
```

---

### Post by Yezinki on 2008-11-07
> **Sam said:**
> Conky is installed on your system. To get rid of the autoremove message, run:
```
sudo apt-get autoremove
```

It looks installed but wont run when I press Alt+F2??

---

### Post by Sam on 2008-11-07
> **Yezinki said:**
> It looks installed but wont run when I press Alt+F2??

Did you create the file ~/.conkyrc properly ?

You'd better run conky from a terminal, this way any error will be outputed.

---

### Post by Yezinki on 2008-11-07
> **Sam said:**
> Did you create the file ~/.conkyrc properly ?

You'd better run conky from a terminal, this way any error will be outputed.



No I did not create a file.....how do I do that?

How do I run it  from the Terminal.

Regards,

Yezinki.

---

### Post by Sam on 2008-11-07
> **Yezinki said:**
> No I did not create a file.....how do I do that?
Run from a teminal:
```
zcat /usr/share/doc/conky/examples/conky.conf.gz > ~/.conkyrc
```
This will create a .conkyrc file in your home directory from the sample in the documentation.

Then open it with a text editor:
```
gedit ~/.conkyrc
```

And customize it as you wish.


All the available parameters that you can put in ~/.conkyrc are listed are listed in the man page. Run:
```
man conky
```

[This page](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html) as other informations, too.

> **Yezinki said:**
> How do I run it  from the Terminal.
```
conky
```

---

### Post by Yezinki on 2008-11-07
> **Sam said:**
> Run from a teminal:
```
zcat /usr/share/doc/conky/examples/conky.conf.gz > ~/.conkyrc
```
This will create a .conkyrc file in your home directory from the sample in the documentation.

Then open it with a text editor:
```
gedit ~/.conkyrc
```

And customize it as you wish.


All the available parameters that you can put in ~/.conkyrc are listed are listed in the man page. Run:
```
man conky
```

[This page](http://www.ubuntugeek.com/conky-a-light-weight-system-monitor-for-ubuntu-linux-systems.html) as other informations, too.


```
conky
```


[B]ubuntu@ubuntu-laptop:~$ sudo zcat /usr/share/doc/conky/examples/conky.conf.gz > ~/.conkyrc
[sudo] password for ubuntu: 
ubuntu@ubuntu-laptop:~$ 
[/B]

Whats this??

Regards,

Yezinki.

---

### Post by Yezinki on 2008-11-07
Is this OK?

Regards!

Yezinki.

---

### Post by Sam on 2008-11-07
> **Yezinki said:**
> [B]ubuntu@ubuntu-laptop:~$ sudo zcat /usr/share/doc/conky/examples/conky.conf.gz > ~/.conkyrc
[sudo] password for ubuntu: 
ubuntu@ubuntu-laptop:~$ 
[/B]

Whats this??

Regards,

Yezinki.

```
sudo zcat /usr/share/doc/conky/examples/conky.conf.gz > ~/.conkyrc
```
means:

"As root, print the content of the gzipped (=compressed) file /usr/share/doc/conky/examples/conky.conf.gz in the file ~/.conkyrc"

---

### Post by Sam on 2008-11-07
> **Yezinki said:**
> Is this OK?

Regards!

Yezinki.

No, the file has a dot in front of the name. This makes it an hidden file. Use Ctrl-H in nautilus to show the hidden files.

But if you ran "sudo zcat /usr/share/doc/conky/examples/conky.conf.gz > ~/.conkyrc", the file .conkyrc is already there.

Use```
gedit ~/.conkyrc
``` to open it !

---

### Post by Yezinki on 2008-11-07
# Conky sample configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check [http://conky.sf.net](http://conky.sf.net) for an up-to-date-list.

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

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders yes

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
#alignment top_right
alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 12

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
override_utf8_locale no

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer none

# Shows the maximum value in scaled graphs.
show_graph_scale no

# Shows the time range covered by a graph.
show_graph_range no

# Allow each port monitor to track at most this many connections (if 0 or not set, default is 256)
#max_port_monitor_connections 256

# Maximum number of special things, e.g. fonts, offsets, aligns, etc.
#max_specials 512

# Maximum size of buffer for user text, i.e. below TEXT line.
#max_user_text 16384

# Timing interval for music player thread, e.g. mpd, audacious
#music_player_interval (update_interval is default)

# Strictness of if_up. One of: up, link or address. The later ones imply the further ones.
# Defaults to up.
#if_up_strictness address

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename - $sysname $kernel on $machine
$stippled_hr
${color lightgrey}Uptime:$color $uptime ${color lightgrey}- Load:$color $loadavg
${color lightgrey}CPU Usage:${color #cc2222} $cpu% ${cpubar}
${color red}${cpugraph 0000ff 00ff00}
${color lightgrey}RAM Usage:$color $mem/$memmax - $memperc% ${membar}
${color lightgrey}Swap Usage:$color $swap/$swapmax - $swapperc% ${swapbar}
${color lightgrey}Processes:$color $processes  ${color grey}Running:$color $running_processes
$color$stippled_hr
${color lightgrey}Networking:
 Down:${color #8844ee} ${downspeed eth0} k/s${color lightgrey} ${offset 80}Up:${color #22ccff} ${upspeed eth0} k/s
${color #0000ff}${downspeedgraph eth0 32,150 ff0000 0000ff} ${color #22ccff}${upspeedgraph eth0 32,150 0000ff ff0000}
${color lightgrey}File systems:
 / $color${fs_used /}/${fs_size /} ${fs_bar /}
${color #88aadd}MPD: ${alignc}$mpd_artist - $mpd_title
${color #88aadd}$mpd_bar
${color #88aadd}${alignc}$mpd_status
${color}Name              PID     CPU%   MEM%
${color #ddaa00} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color lightgrey} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color lightgrey} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color lightgrey} ${top name 4} ${top pid 4} ${top cpu 4} ${top mem 4}
${color}Mem usage
${color #ddaa00} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color lightgrey} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color lightgrey} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}
$stippled_hr
${color #ddaa00}Port(s)${alignr}#Connections
$color Inbound: ${tcp_portmon 1 32767 count}  Outbound: ${tcp_portmon 32768 61000 count}${alignr}ALL: ${tcp_portmon 1 65535 count}
${color #ddaa00}Inbound Connection ${alignr} Local Service/Port$color
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 lservice 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 lservice 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 lservice 2}
 ${tcp_portmon 1 32767 rhost 3} ${alignr} ${tcp_portmon 1 32767 lservice 3}
 ${tcp_portmon 1 32767 rhost 4} ${alignr} ${tcp_portmon 1 32767 lservice 4}
 ${tcp_portmon 1 32767 rhost 5} ${alignr} ${tcp_portmon 1 32767 lservice 5}
${color #ddaa00}Outbound Connection ${alignr} Remote Service/Port$color
 ${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
 ${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
 ${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
 ${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
 ${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
 ${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}

---

### Post by Yezinki on 2008-11-07
Is this correct?

Where is this file located??

---

### Post by Sam on 2008-11-07
Yes this is the conky config.


You copied this from the file ~/.conkyrc right ?

In this case, run from a teminal:
```
conky
```

---

### Post by Yezinki on 2008-11-08
[B]ubuntu@ubuntu-laptop:~$ conky
Conky: desktop window (1a000a9) is subwindow of root window (9f)
Conky: window type - normal
Conky: drawing to created window (0x3a00001)
Conky: drawing to double buffer
Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

Conky: MPD error: problems getting a response from "localhost" on port 6600 : Connection refused

[/B]


Thanks alot Sam,

Why am I getting these errors in the Terminal?

One more question how does one make a power plan like in Vista or XP hard drive, standby, hibernation etc?

Regards,

Yezinki.

---

### Post by Sam on 2008-11-08
It's because you use a sample configuration file, and it may contain some stuff that is not available on your machine. Here it's mpd (an audio server). Remove from the .conkyrc file the lines```
${color #88aadd}MPD: ${alignc}$mpd_artist - $mpd_title
${color #88aadd}$mpd_bar
${color #88aadd}${alignc}$mpd_status
```

You should try to understand what the lines means in the config file (read "man conky"). There are also a few threads in the forums with people's customized .conkyrc files.

I don't understand your last question. If it's not relative to this thread, you'd better start a new one.

---

### Post by Yezinki on 2008-11-08
Thanks Sam,

Regards,

Yezinki.

---

