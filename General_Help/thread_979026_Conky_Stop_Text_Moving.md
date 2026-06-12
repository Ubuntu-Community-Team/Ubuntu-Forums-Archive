---
title: "Conky Stop Text Moving"
date: 2008-11-11
forum: General Help
---

### Post by ElvetPuff on 2008-11-11
I'm trying to get conky to display information horizontally across the top of my screen, but below the top gnome panel.

My script works but when certain variable (i.e. CPU percentage) move from double figures (e.g. 76) to single figures (e.g. 7) it causes all of the text conky is displaying to move. It's ugly and distracting.

How can I stop this from happening?

```

# Horizontal Conky


#Alignment
	alignment top_middle

#Background
	background true

#Border
	border_margin 0
	border_width 0
	draw_borders false

#Buffer
	double_buffer true

#Console
	out_to_console false

#Gap
	gap_x 0
	gap_y 0

#Run Times
	total_run_times 0	

#Spacer
	use_spacer right

#Window
	own_window true
	own_window_transparent true
	own_window_type desktop
	own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

#XFT
	use_xft true
	xftfont sans:size=9

TEXT
${font sans:size=9}Kernel: $kernel $machine | Uptime: ${uptime_short} | Hostname: ${nodename} | Processes: ${processes} | CPU1: ${cpu cpu1}% | CPU2: ${cpu cpu2}% | RAM: ${memperc}% | 

```

Any other hints/suggestions would be brilliant. 

Cheers,

ElvetPuff

---

### Post by easybake on 2008-11-12
You can use goto values in your conky so the text always stays at the right place, instead of having the variables depend on the location of what is before it.

For example.

```
${goto 45}${cpu cpu1}
``` 

That will place make the cpu% variable start at 45 pixels from the edge of the screen. You can add goto values to all the variables and text to keep everything locked down.

---

