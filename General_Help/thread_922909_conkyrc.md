---
title: "conkyrc"
date: 2008-09-17
forum: General Help
---

### Post by henryjm206 on 2008-09-17
I wrote a new conky for the first time and was wondering if anyone could give me a few tips.
thanks
henry

gmail is still in the works

L@@@K at screen shot

conky : 

background yes
use_xft yes
xftfont 123:size=8
xftalpha 0.1
update_interval 0.5
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 250 5
maximum_width 400
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color dark orange
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
net_avg_samples 1
override_utf8_locale no
use_spacer yes
TEXT
Henry@Ubuntu
Gobuntu 8.04
Linux kernel $kernel
--------------------------------------------------------------------
Max Memory
$memmax
Memory
${memperc}%
$membar
---------------------------------------------------------------------
CPU
Core 1
${cpu cpu0}%
${cpubar cpubar0}

Core 2
${cpu cpu1}%
${cpubar cpubar1}
--------------------------------------------------------------------
Hard Drive
Writing
$diskio
Size
$fs_size
Used
$fs_bar
---------------------------------------------------------------------
Processes
$processes
---------------------------------------------------------------------
Gmail

---

### Post by henryjm206 on 2008-09-17
just finished the gmail part of conky:)

---

### Post by easybake on 2008-09-18
> **henryjm206 said:**
> I wrote a new conky for the first time and was wondering if anyone could give me a few tips.


If I were you I would cut the width of that thing at least in half. For more ideas you could always check this [mega-conky-thread]("http://ubuntuforums.org/showthread.php?t=281865")

I use 3 different ones at once, but I like unconventional ones. Here's mine: [[IMG]http://img242.imageshack.us/img242/5985/screenshot2du7.th.png[/IMG]](http://img242.imageshack.us/img242/5985/screenshot2du7.png)

---

