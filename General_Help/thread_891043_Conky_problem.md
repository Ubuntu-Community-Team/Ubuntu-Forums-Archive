---
title: "Conky problem"
date: 2008-08-15
forum: General Help
---

### Post by kurry on 2008-08-15
I'm _just_ starting out with ubuntu, i've had it about three days in a dual-boot. So far it's been great, but after i installed conky and tried to run it it'll give me and error saying
> Conky: can't open '/sys/class/hwmon/hwmon0/device/temp2_input': No such file or directory

I eventually found the file in sys/bus/i2c/devices/0-002e. How could i fix this so it works ?

---

### Post by kurry on 2008-08-15
bump ...

---

### Post by kurry on 2008-08-16
X2 bump :(

---

### Post by y-lee on 2008-08-16
> **kurry said:**
> I'm _just_ starting out with ubuntu, i've had it about three days in a dual-boot. So far it's been great, but after i installed conky and tried to run it it'll give me and error saying

```
Conky: can't open '/sys/class/hwmon/hwmon0/device/temp2_input': No such file or directory
```

I eventually found the file in sys/bus/i2c/devices/0-002e. How could i fix this so it works ?

Strange error, I can't find much info on it. But first of all how do you know that the file in sys/bus/i2c/devices/0-002e is the same file conky is looking for in /sys/class/hwmon/hwmon0/device/?

Second of all if it is the same file you could put a link in /sys/class/hwmon/hwmon0/device/ linking to it. creating the necessary directories if need be. That way conky would be able to find it.

---

### Post by dje on 2008-08-16
please post the output of:
```
cat $HOME/.conkyrc
```

dje

---

### Post by kurry on 2008-08-16
> background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$sysname $kernel on $machine

Uptime $alignr $uptime
Load $alignr $loadavg

Hostname $alignr $nodename
eth0 $alignr ${addr eth0}
Mobo CPU Temp $alignr ${hwmon temp 1}C ${hwmon temp 2}C
HDDlinux $alignr /dev/hdb ${execi 300 nc localhost 7634 | cut -c53-54 ;}C
HDDwindows $alignr /dev/hda ${execi 300 nc localhost 7634 | cut -c27-28 ;}C

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/root $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}

$processes processes ($running_processes running)

${color white}Highest CPU:
${color de0b0b}${top name 1}${top_mem cpu 1}
${color white}${top name 2}${top cpu 2}
${top name 3}${top cpu 3}
${top name 4}${top cpu 4}
${top name 5}${top cpu 5}

${color white}Highest MEM:
${color de0b0b}${top_mem name 1}${top_mem mem 1}
${color white}${top_mem name 2}${top_mem mem 2}
${top_mem name 3}${top_mem mem 3}
${top_mem name 4}${top_mem mem 4}
${top_mem name 5}${top_mem mem 5}

${color}Networking:
Down:${color} $alignr ${downspeed eth0} k/s${color} ${offset 80}
$alignc ${downspeedgraph eth0 32,150 de0b0b de0b0b}
Up:${color} $alignr ${upspeed eth0} k/s ${offset 80}
$alignc ${upspeedgraph eth0 32,150 de0b0b de0b0b}


There

---

### Post by kurry on 2008-08-16
> **y-lee said:**
> Strange error, I can't find much info on it. But first of all how do you know that the file in sys/bus/i2c/devices/0-002e is the same file conky is looking for in /sys/class/hwmon/hwmon0/device/?

Second of all if it is the same file you could put a link in /sys/class/hwmon/hwmon0/device/ linking to it. creating the necessary directories if need be. That way conky would be able to find it.

I supposed that since it had the same name it would be what it was looking for, there were alot of other files there to do with temps, fans, etc.
How would I do a system link ?

---

### Post by dje on 2008-08-16
ok do the following in a terminal:
```
sudo gedit $HOME/.conkyrc
```
and change it so the red line below is the same as the one in that file (ie. put a hash in front of that line)
> background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 200
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 12
gap_y 48
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no

TEXT
$sysname $kernel on $machine

Uptime $alignr $uptime
Load $alignr $loadavg

Hostname $alignr $nodename
eth0 $alignr ${addr eth0}
[COLOR="Red"]#Mobo CPU Temp $alignr ${hwmon temp 1}C ${hwmon temp 2}C[/COLOR]
HDDlinux $alignr /dev/hdb ${execi 300 nc localhost 7634 | cut -c53-54 ;}C
HDDwindows $alignr /dev/hda ${execi 300 nc localhost 7634 | cut -c27-28 ;}C

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

/root $alignc ${fs_used /} / ${fs_size /} $alignr ${fs_free_perc /}%
${fs_bar /}

/home $alignc ${fs_used /home} / ${fs_size /home} $alignr ${fs_free_perc /home}%
${fs_bar /home}

swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}

$processes processes ($running_processes running)

${color white}Highest CPU:
${color de0b0b}${top name 1}${top_mem cpu 1}
${color white}${top name 2}${top cpu 2}
${top name 3}${top cpu 3}
${top name 4}${top cpu 4}
${top name 5}${top cpu 5}

${color white}Highest MEM:
${color de0b0b}${top_mem name 1}${top_mem mem 1}
${color white}${top_mem name 2}${top_mem mem 2}
${top_mem name 3}${top_mem mem 3}
${top_mem name 4}${top_mem mem 4}
${top_mem name 5}${top_mem mem 5}

${color}Networking:
Down:${color} $alignr ${downspeed eth0} k/s${color} ${offset 80}
$alignc ${downspeedgraph eth0 32,150 de0b0b de0b0b}
Up:${color} $alignr ${upspeed eth0} k/s ${offset 80}
$alignc ${upspeedgraph eth0 32,150 de0b0b de0b0b} 
save and close the file then run:
```
conky &
```

dje

---

### Post by dexter on 2008-08-16
What happens when you remove this line?
```

Mobo CPU Temp $alignr ${hwmon temp 1}C ${hwmon temp 2}C

```

It should work but it will no longer display you temperature.

---

### Post by kurry on 2008-08-16
> **dje said:**
> ok do the following in a terminal:
```
sudo gedit $HOME/.conkyrc
```
and change it so the red line below is the same as the one in that file (ie. put a hash in front of that line)

save and close the file then run:
```
conky &
```

dje
I did that and ran conky & and got this;
> [1] 14605
kurt@kurt-desktop-buntu:~$ Conky: can't open '/sys/class/hwmon/hwmon0/device/temp2_input': No such file or directory
please check your device or remove this var from Conky


---

### Post by kurry on 2008-08-16
Right, I removed the line as dexter said and it runs fine now, just without the temp. I don't really need it anyway. Thanks for the help everyone though :D

---

