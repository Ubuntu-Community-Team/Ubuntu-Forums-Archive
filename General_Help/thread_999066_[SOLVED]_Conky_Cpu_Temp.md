---
title: "[SOLVED] Conky Cpu Temp"
date: 2008-12-01
forum: General Help
---

### Post by IceReaver75 on 2008-12-01
I can't get conky to report my cpu temp at all.  I have installed lm-sensor and when I type sensors in a terminal I get all the readings.  I have also installed GKrellM and that will read my Cpu and Video card temps.

I have tried to use where GKrellM gets the temps from in conky and still nothing.  GKrellM gets the temps from:

w83697hf-hwmon0/temp1

I have tried that whole line and conky says unknown variable when started
I have tried just hwmon0/temp1 : hwmon0 temp1 both came back with unknown variable

I have also tried hwmon temp1 and i got : can't open '/sys/class/hwmon/hwmon0/device/temp10_input': No such file or directory

I just don't know what to try now.  Any help will be appreciated.  
Thank you.

---

### Post by markp1989 on 2008-12-01
```
${execi 1 echo`acpi -t | cut -c20-22`}C
```

Try adding that to you conkyrc

---

### Post by m_duck on 2008-12-01
If running "sensors" from the terminal works, the following in your ~/.conkyrc should work:
```
${execi 1 sensors | grep "Core 0:" | cut -d+ -f2 | cut -c1-7}
```
  and for a second core
```
${execi 1 sensors | grep "Core 1:" | cut -d+ -f2 | cut -c1-7}
```This outputs only the temperature value from "sensors" along with the degrees symbol and "C".

---

### Post by IceReaver75 on 2008-12-01
Neither one worked.  I'm not receiving any error now but the temp is just blank nothing shows.  Maybe I just dont have something setup right so here is my conky file:

background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

TEXT
${color white}SYSTEM ${hr 1}${color}

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${execi 1 sensors | grep "Core 0:" | cut -d+ -f2 | cut -c1-7}

CPU: ${alignr}${freq} MHz
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg

CPU1 ${alignr}${cpu cpu1}%
${cpubar 4 cpu1}

Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color white}Filesystem ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /home}

${color white}NETWORK ${hr 1}${color}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107} ${alignr}${upspeedgraph eth0 25,107}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

I got this from deviant art so its not mine but the one I'm using right now.  Everything works but the cpu temp

---

### Post by m_duck on 2008-12-01
The conky itself seems fine (runs on my computer). Can you post the output of ```
sensors
```when run from the terminal? I assume that the lines I gave need to be modified to work in your case.

EDIT: Also, in order to get the degrees symbol to display properly, I think you need to change the line:```
override_utf8_locale no
```to```
override_utf8_locale yes
```

---

### Post by IceReaver75 on 2008-12-01
my sensors report comes back with this:

w83697hf-isa-0290
Adapter: ISA adapter
VCore:       +1.60 V  (min =  +0.00 V, max =  +0.00 V)   ALARM
+3.3V:       +3.17 V  (min =  +0.78 V, max =  +0.45 V)   ALARM
+5V:         +4.92 V  (min =  +1.13 V, max =  +5.16 V)   
+12V:       +11.07 V  (min =  +1.95 V, max =  +8.88 V)   ALARM
-12V:        +0.30 V  (min = -14.91 V, max =  -9.48 V)   ALARM
-5V:         +1.68 V  (min =  -7.71 V, max =  -5.80 V)   ALARM
V5SB:        +5.43 V  (min =  +1.88 V, max =  +0.24 V)   ALARM
VBat:        +3.46 V  (min =  +0.06 V, max =  +0.10 V)   ALARM
fan1:       1406 RPM  (min =   -1 RPM, div = 8)  ALARM
fan2:       5443 RPM  (min = 2596 RPM, div = 8)
temp1:       +32.0°C  (high = +64.0°C, hyst =  +8.0°C)  sensor = thermistor
temp2:       +46.5°C  (high = +120.0°C, hyst = +120.0°C)  sensor = thermistor
beep_enable:enabled

---

### Post by m_duck on 2008-12-01
OK, I'm assuming it's a dual core cpu you have got so you can have both temperatures displayed. The lines you need in your ~/.conkyrc are (I think):
```
${execi 1 sensors | grep "temp1:" | cut -d+ -f2 | cut -c1-7}
${execi 1 sensors | grep "temp2:" | cut -d+ -f2 | cut -c1-7}
```

---

### Post by IceReaver75 on 2008-12-01
${execi 1 sensors | grep "temp1:" | cut -d+ -f2 | cut -c1-7}
 that worked it now shows the temp in my conky

the other temp i'm not sure what that is cause i have a single core amd sempron processor.......i'm thinking maybe the other temp might be my gpu temp from my nvidia card

cause my bios is saying my cpu temp is around 32c and the nvidia setting is reporting my gpu temp at around 46c so that's about my best guess of what that other temp is

thank you so much for your help.

---

### Post by m_duck on 2008-12-01
No problem. Another alternative could be your motherboard temperature, but I don't know for sure.

---

### Post by loomsen on 2008-12-02
> 
docter[~] nvidia-settings -q GPUCoreTemp

  Attribute 'GPUCoreTemp' (dhcppc0:0.0): 63.
    'GPUCoreTemp' is an integer attribute.
    'GPUCoreTemp' is a read-only attribute.
    'GPUCoreTemp' can use the following target types: X Screen, GPU.

docter[~] 


This will show.

Or, a little bit easier to handle maybe, using nvclock:

> 
docter[~] nvclock -T
          nVidia Geforce 8600M GT
          => GPU temperature: 63C
docter[~] 

So, cutting it:
> 
docter[~] nvclock -T | awk '/temperature/ {print $4}'
          63C
docter[~] 


That's the part in my conky:
```
${execi 30 nvclock -T | awk '/temperature/ {print $4}'}

```

*edit*
To cut the C add **| cut -d "C" -f1**

nvclock -T | awk '/temperature/ {print $4}'| cut -d "C" -f1

Then you can use ° and conky will look a little nicer imho :)

---

