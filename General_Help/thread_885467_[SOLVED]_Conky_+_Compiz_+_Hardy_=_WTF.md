---
title: "[SOLVED] Conky + Compiz + Hardy = WTF"
date: 2008-08-10
forum: General Help
---

### Post by r4k11n on 2008-08-10
Here's the deal.

I had conky listed in my startup programs, but everytime startup is done, conky stays on top, above all windows. Quitting it and starting it again using the terminal fixes it. What am I to do?

[LIST]
[*]I have tried the .sh file with that sleep function, but it didn't work.
[*]When I type only "conky" in the command portion of the startup dialog box, my monitor belches out weird colors [as if my monitor's broken] first before getting to the "proper" screen.
[*]I disabled double-buffering [something like that] in the xorg file, because i get no problems with the flicker.
[/LIST]

```
background yes
font Snap.se:size=7
xftfont Snap.se:size=7
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
on_bottom yes
double_buffer yes
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 206 5
maximum_width 206
default_color ffffff
default_shade_color 000000
default_outline_color 000000
alignment top_right
gap_x 6
gap_y 22
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font LCD:style=Bold:pixelsize=40}${alignc}${time %H:%M:%S}${font Snap.se:size=7}

${font Aerial:style=Bold:pixelsize=11}SYSTEM${font Snap.se:size=7} ${hr 1 }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

Battery    ${battery_time BAT0} ${alignr}(${battery BAT0})
${battery_bar 4 BAT0}

CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph cccccc ffffff}

RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}

SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${hr 1}
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${hr 1}
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}



${font Aerial:style=Bold:pixelsize=11}FILESYSTEM ${font Snap.se:size=7}${hr 1}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}

Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}

Storage: ${alignr}${fs_free /media/hdc4} / ${fs_size /media/hdc4}
${fs_bar 4 /media/hdc4}



${font Aerial:style=Bold:pixelsize=11}NETWORK ${font Snap.se:size=7}${hr 1}

Down ${downspeed ath0} k/s ${alignr}Up ${upspeed ath0} k/s
${downspeedgraph ath0 25,107 cccccc ffffff} ${alignr}${upspeedgraph ath0 25,107 cccccc ffffff}
Total ${totaldown ath0} ${alignr}Total ${totalup ath0}
```

---

### Post by Niedra on 2008-08-10
I had about the same problem, on startup, after loading conky my screen would go black with some weird colors at the top, like it's broken. I made a script for conky to load up, making it to load slower. Worked for me.
```

#! /bin/bash
sleep 10
conky -c /path/to/script/.conkyrc0
sleep 3
conky -c /path/to/script/.conkyrc1

```
I can't really explain why does this work, and those sleep values are just random.

---

### Post by r4k11n on 2008-08-10
What's with the multiple conkyrc values?

EDIT: It still doesn't work. :(

---

### Post by Niedra on 2008-08-10
I've got 2 separate conky boxes running on my desktop. Maybe try playing with 'own_window_type override' - [Try desktop or normal]("http://conky.sourceforge.net/config_settings.html")

---

### Post by r4k11n on 2008-08-10
Poof. How stupid of me. I changed it to normal and everything worked great. Thanks. :D:D

---

### Post by ArtF10 on 2008-08-11
> **Niedra said:**
> ...Maybe try playing with 'own_window_type override' - [Try desktop or normal]("http://conky.sourceforge.net/config_settings.html")

Sorry, I'm not quite following that.  I'm quite unfamiliar with conky.  

**Questions:**
1.  What has to be changed to normal and from where?

2.  With what command do I open conkyrc and where conkyrc is located?

---

### Post by Niedra on 2008-08-12
.conkyrc is a hidden file by default located in your home/user/ to edit it, just open it with any text editor. You should check [This out]("http://conky.sourceforge.net/documentation.html").

---

