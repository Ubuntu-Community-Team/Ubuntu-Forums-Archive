---
title: "Conky refusues to start."
date: 2008-09-03
forum: General Help
---

### Post by detroit/zero on 2008-09-03
I've been having some crazy problems lately with USB transfer speeds and login loops. Those problems and my genius solution [are outlined here]("http://ubuntuforums.org/subscription.php?do=viewsubscription").

Basically, I was dissatisfied with gnome, installed KDE, remembered how I can't stand KDE, then re-installed gnome.

My trusty .conkyrc file went with me through that mess. Now that I'm happily settled into my new install, I can't get conky to start. It appears briefly, but as soon as it begins to render, it winks out of existence.

If I rename my .conkyrc file to something else, and just run conky from a cl, it appears in some sort of default configuration. I can't find any other .conkyrc file anywhere in my drive, so where is it getting it's config?

Did I miss something over the last couple days, and now .conkyrc files don't go in your home dir but somewhere else?

Anybody have an idea?

I attached .conkyrc if looking through it will help, and just for giggles I included my startconky and a script for getting an external IP that I lifted from someone else.

---

### Post by easybake on 2008-09-03
> **detroit/zero said:**
> My trusty .conkyrc file went with me through that mess. Now that I'm happily settled into my new install, I can't get conky to start. It appears briefly, but as soon as it begins to render, it winks out of existence.

If I rename my .conkyrc file to something else, and just run conky from a cl, it appears in some sort of default configuration. I can't find any other .conkyrc file anywhere in my drive, so where is it getting it's config?

Did I miss something over the last couple days, and now .conkyrc files don't go in your home dir but somewhere else?

Anybody have an idea?

I tried out your conkyrc after deleting entries for cpu2, sda, and temps (because they didn't apply to my system) it worked.

Do you get any errors when you start conky from the terminal?

During your adding and removing it is possible that you removed something like "sensors". So you may have to reinstall it.

If you change the name of your conkyrc you have to use this to launch it instead ```
conky -c ~/Path/To/Wherever/Your/Conkyrc/is
```

---

### Post by detroit/zero on 2008-09-03
> **easybake said:**
> I tried out your conkyrc after deleting entries for cpu2, sda, and temps (because they didn't apply to my system) it worked.

Do you get any errors when you start conky from the terminal?

During your adding and removing it is possible that you removed something like "sensors". So you may have to reinstall it.

If you change the name of your conkyrc you have to use this to launch it instead ```
conky -c ~/Path/To/Wherever/Your/Conkyrc/is
```
I do get error messages when I start conky, but they're concerning /dev/sdb, c, and d not being mounted - they're just usb drives and I have $if_mounted statements there so the lines auto-appear/disappear as drives are mounted and unmounted.

I did re-install lm-sensors and hddtemp. The first time I tried to run conky, I got an error about permissions for hddtemp, but that's since been remedied.

Here's a screenshot of when I run conky with .conkyrc sitting soundly in my home dir.

When conky flashes and then winks out of existence, and I do a killall conky, terminal says "no process killed". 

I then renamed conkyrc to ".conkyrc-main" and didn't change anything else.  When I run conky the second time, it appears as it does in the screenshot in the lower left corner. Like I said before, I can't find a second conkyrc file anywhere in my drive.

The only thing absent from the screenshot is the code the terminal spits out as I kill that little orphan conky window:
```
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 9761 requests (9759 known processed) with 0 events remaining
```
Which, to me, seems consistent with closing the conky window.

I've tried renaming .conkyrc, I've tried moving it to its own folder and running conky with the -c switch as you suggest, but to no avail. I've even tried purging and re-installing conky both from terminal and from synaptic.

I'm at a loss.

---

### Post by JECHO on 2008-09-03
> **detroit/zero said:**
> I've been having some crazy problems lately with USB transfer speeds and login loops. Those problems and my genius solution [are outlined here]("http://ubuntuforums.org/subscription.php?do=viewsubscription").

Basically, I was dissatisfied with gnome, installed KDE, remembered how I can't stand KDE, then re-installed gnome.

My trusty .conkyrc file went with me through that mess. Now that I'm happily settled into my new install, I can't get conky to start. It appears briefly, but as soon as it begins to render, it winks out of existence.

If I rename my .conkyrc file to something else, and just run conky from a cl, it appears in some sort of default configuration. I can't find any other .conkyrc file anywhere in my drive, so where is it getting it's config?

Did I miss something over the last couple days, and now .conkyrc files don't go in your home dir but somewhere else?

Anybody have an idea?

I attached .conkyrc if looking through it will help, and just for giggles I included my startconky and a script for getting an external IP that I lifted from someone else.



Hey uninstall conky and then reinstall it. (save your conkyrc though)


after you re-install it change **own_window_type below** to **own_window_type normal**

save it and put it in your home directory. (name it .conkyrc)


then press alt+f2 and type conky. should work fine.




note: if you want it to start at login then add it to your startup programs list.

---

### Post by detroit/zero on 2008-09-03
> **JECHO said:**
> Hey uninstall conky and then reinstall it. (save your conkyrc though)


after you re-install it change **own_window_type below** to **own_window_type normal**

save it and put it in your home directory. (name it .conkyrc)


then press alt+f2 and type conky. should work fine.

Not a bad idea, but no dice. The only difference is that it comes up with standard window decorations before it shuts back down.

---

### Post by JECHO on 2008-09-03
> **detroit/zero said:**
> Not a bad idea, but no dice. The only difference is that it comes up with standard window decorations before it shuts back down.

have you added conky to the startup porgrams? (under system > preferences > sessions)


also, after you add it to the startup programs (if it still isnt working) try using the conkyrc code below to see if its just your config file.

the below conkyrc is mine and works well on my machine...

```
background yes
font Snap.se:size=8
xftfont Snap.se:size=8
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
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
gap_y 25
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font LCD:style=Bold:pixelsize=35}${alignc}${time %H:%M:%S}${font Snap.se:size=8}

${font Aerial:style=Bold:pixelsize=12}SYSTEM${font Snap.se:size=8} ${hr 1 }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

Battery    ${battery_time BAT0} ${alignr}(${battery BAT0})
${battery_bar 4 BAT0}

CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph 333333 ffffff}

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



${font Aerial:style=Bold:pixelsize=12}FILESYSTEM ${font Snap.se:size=8}${hr 1}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}

Windows: ${alignr}${fs_free /media/Vista} / ${fs_size /media/Vista}
${fs_bar 4 /media/Vista}

External: ${alignr}${fs_free /media/External} / ${fs_size /media/External}
${fs_bar 4 /media/External}



${font Aerial:style=Bold:pixelsize=12}NETWORK ${font Snap.se:size=8}${hr 1}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 333333 ffffff} ${alignr}${upspeedgraph eth0 25,107 333333 ffffff}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}
```

---

### Post by detroit/zero on 2008-09-03
> **JECHO said:**
> have you added conky to the startup porgrams? (under system > preferences > sessions)


also, after you add it to the startup programs (if it still isnt working) try using the conkyrc code below to see if its just your config file.

the below conkyrc is mine and works well on my machine...

Well, heck, I guess it's my config file. I'll have to go through it line by line and see what happened to it. Yours works like a charm.

Thanks for the insight. I'll make a post to wrap it up when I figure out what went wrong...

---

### Post by JECHO on 2008-09-03
> **detroit/zero said:**
> Well, heck, I guess it's my config file. I'll have to go through it line by line and see what happened to it. Yours works like a charm.

Thanks for the insight. I'll make a post to wrap it up when I figure out what went wrong...


:popcorn:

---

### Post by detroit/zero on 2008-09-04
Well, I'm not sure what the problem was.

I went through my .conkyrc file line-by-line. I had the original open in one gedit tab, and a test file open in a second. I copied and pasted lines from one file to the other and restarted conky each time I copied a line.

Strangest part is: Now it works.

Go figure.

---

### Post by Kiirsten on 2009-01-12
I'm trying to install Conky but i have some problems.
When i type "conky" in the console a window popsup, and when i close the window, instead of pasting it on the desktop i have this error:

```
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1280 requests (1276 known processed) with 0 events remaining.
```

Anybody can help?

---

