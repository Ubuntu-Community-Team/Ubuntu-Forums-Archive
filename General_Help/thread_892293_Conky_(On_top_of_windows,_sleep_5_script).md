---
title: "Conky (On top of windows, sleep 5 script)"
date: 2008-08-17
forum: General Help
---

### Post by faction918 on 2008-08-17
In reference to: [http://ubuntuforums.org/showthread.php?t=388560]("http://ubuntuforums.org/showthread.php?t=388560")...

When I start conky in a session it will appear on top of all windows (as specified to the archived post). If I kill the conky process and restart it, conky displays fine.

If I try to launch conky via a sleep method, the conky window never appears, however, I can still start the process manually.

My two sleep methods were putting the following code into a file and running the script with the bash command: 

```

#!/bin/sh
sleep 5
conky &

```

And the other method was putting the following directly into the sessions list:

 ```
sleep 5; conky
``` 

If I try both methods after Ubuntu is started, conky also launches fine. It is only when the scripts are run at startup that conky never displays.

Any other suggestions how to get conky to not be on top of all windows and still launch with the session?

Thanks!

---

### Post by ahmedh on 2008-08-17
I have the exact same problem, conky is on top of all other windows at startup. Killing and restarting conky works fine after that.

Help would be greatly appreciated!

---

### Post by ahmedh on 2008-08-17
Also it should be noted that there is nothing about this problem in the conky documentation.

---

### Post by easybake on 2008-08-17
> **ahmedh said:**
> Also it should be noted that there is nothing about this problem in the conky documentation.

It's not a problem with Conky it has to Compiz.

In the first script you might have skipped the step to make it executable or don't have the time set high enough.

In Terminal ```
sudo chmod a+x PATH-TO-SLEEP-SCRIPT
```

You should be able to test out the script in terminal by typing```
./PATH-TO-SLEEP-SCRIPT
```

change the sleep to 15 or 20 if it still doesn't work.


NOTE: Only put the Bash Sleep Script into your sessions menu and remove any other conky listing.

---

### Post by ahmedh on 2008-08-17
Even after doing the steps you suggested the problem remained. Can you confirm that I did it correctly?

1. Paste the following in gedit and save (my saved file was /home/name/conkyscript)

```
#!/bin/sh
sleep 5
conky &
```

2. Run:
```
sudo chmod a+x PATH-TO-SLEEP-SCRIPT
./PATH-TO-SLEEP-SCRIPT
```

The output of the second terminal command was "no such file or directory."

I tried changing "sleep" to 15 and 20 as well but that didn't work either.

---

### Post by easybake on 2008-08-17
> **ahmedh said:**
> Even after doing the steps you suggested the problem remained. Can you confirm that I did it correctly?

1. Paste the following in gedit and save (my saved file was /home/name/conkyscript)

```
#!/bin/sh
sleep 5
conky &
```

2. Run:
```
sudo chmod a+x PATH-TO-SLEEP-SCRIPT
./PATH-TO-SLEEP-SCRIPT
```

The output of the second terminal command was "no such file or directory."

I tried changing "sleep" to 15 and 20 as well but that didn't work either.

I didn't notice but that original script could be bad. Do those same steps but use this instead.```
#!/bin/bash

sleep 20 &&
conky 
```

---

### Post by ahmedh on 2008-08-17
Thanks for the reply, but even with the new script, neither sleep 5, 15, nor 20 worked. It still appears on top of other windows.

---

### Post by easybake on 2008-08-17
> **ahmedh said:**
> Thanks for the reply, but even with the new script, neither sleep 5, 15, nor 20 worked. It still appears on top of other windows.

It's got to be in your conkyrc then. 

Above TEXT add the line ```
own_window_type override
```

---

### Post by ahmedh on 2008-08-18
:-/ Still no progress

---

### Post by easybake on 2008-08-18
> **ahmedh said:**
> :-/ Still no progress

Post your conkyrc on here. 

Also double check to make sure you are only using the script I gave you. Make sure no other scripts to start conky are listed in your sessions menu.

You can double check this on after start up by going into your System Monitor and seeing if there are more than one Conky listed in the processes.

---

### Post by ahmedh on 2008-08-19
Double checked and everything...All seems fine.

Here is my .conkyrc:

```
# set to yes if you want Conky to be forked in the background
background no

cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 260

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 40
alignment top_right
#alignment bottom_left
#alignment bottom_right
# Gap between borders of screen and text
# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer no
# Subtract file system buffers from used memory?
no_buffers yes
# set to yes if you want all text to be in uppercase
uppercase no
# none, xmms, bmp, audacious, infopipe (default is none)
xmms_player bmp
# boinc (seti) dir
# seti_dir /opt/seti
# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit
# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=12}${time %a  %b  %d}${alignr -25}${time %k:%M}
own_window_type override
TEXT
${color #FFFFFF}$sysname $kernel $machine - $nodename 

${color #FFFFFF}Uptime:${color white} $uptime ${alignr}${color #FFFFFF}Temperature: ${color white}${acpitemp}C

${color #FFFFFF}RAM:${color white} $mem/$memmax - $memperc% ${color #FFFFFF}${membar 5,85}
${color #FFFFFF}Usage:${color #FFFFFF} ${color white}${cpu}% ${color #FFFFFF}${cpubar}
${color #FFFFFF}${cpugraph 000000 FFFFFF}

${color #FFFFFF}Hard Disks:
${color #FFFFFF} Root ${color white}${fs_used /}/${fs_size /}${alignr}${color #FFFFFF}${fs_bar 5,99 /}

${color #FFFFFF}CPU Usage         PID     CPU%   MEM%
${color white} ${top name 1} ${top pid 1} ${top cpu 1} ${top mem 1}
${color #FFFFFF} ${top name 2} ${top pid 2} ${top cpu 2} ${top mem 2}
${color #FFFFFF} ${top name 3} ${top pid 3} ${top cpu 3} ${top mem 3}
${color #FFFFFF}Mem Usage
${color white} ${top_mem name 1} ${top_mem pid 1} ${top_mem cpu 1} ${top_mem mem 1}
${color #FFFFFF} ${top_mem name 2} ${top_mem pid 2} ${top_mem cpu 2} ${top_mem mem 2}
${color #FFFFFF} ${top_mem name 3} ${top_mem pid 3} ${top_mem cpu 3} ${top_mem mem 3}

${color #FFFFFF}Network: ${color white}${addr wlan0}
${color #FFFFFF}Down:${color white} ${downspeed wlan0} k/s $alignr${color #FFFFFF} Up:${color white} ${upspeed wlan0} k/s
${color #FFFFFF}${downspeedgraph wlan0 27,120 000000 FFFFFF 180} $alignr${color #FFFFFF}${upspeedgraph wlan0 27,120 000000 FFFFFF 25}
${color white}${totaldown wlan0}           $alignr${color white}${totalup wlan0}
```

---

### Post by easybake on 2008-08-19
> **ahmedh said:**
> Double checked and everything...All seems fine.

Here is my .conkyrc:

I checked out your set up and using your code in my .conkyrc file, my sleep script and it worked out.

If you have a slow booting system you might want to change that sleep value to something even higher. I would suggest changing it to something like 60. That way Conky will noticeably start awhile after you boot your system.

If that doesn't work you could try just starting over. Delete all of the other conky start scripts and do the following. 

In terminal type```
gedit .startconky0
```
Paste this```
#!/bin/bash

sleep 35 &&
conky
```
Save and close.

In terminal type```
sudo chmod a+x .startconky0
```

In SYSTEM>PREFERENCES>SESSIONS 
Click +Add
Name= Starting Conky
Command=./.startconky0

Reboot. It should work. If it still stays above windows I don't really know...

---

### Post by ahmedh on 2008-08-19
Fantastic! That worked like a charm. Thank you so much for your work on this issue.

Over time I will try to decrease the sleep amount until I reach the lowest possible. 

Thanks so much again, everything is working like it should.

---

### Post by faction918 on 2008-08-21
I just realized people actually responded to this :)!... Let me read through all this.

---

### Post by faction918 on 2008-08-21
> **easybake said:**
> I checked out your set up and using your code in my .conkyrc file, my sleep script and it worked out.

If you have a slow booting system you might want to change that sleep value to something even higher. I would suggest changing it to something like 60. That way Conky will noticeably start awhile after you boot your system.

If that doesn't work you could try just starting over. Delete all of the other conky start scripts and do the following. 

In terminal type```
gedit .startconky0
```
Paste this```
#!/bin/bash

sleep 35 &&
conky
```
Save and close.

In terminal type```
sudo chmod a+x .startconky0
```

In SYSTEM>PREFERENCES>SESSIONS 
Click +Add
Name= Starting Conky
Command=./.startconky0

Reboot. It should work. If it still stays above windows I don't really know...

This worked (at 35 seconds). I don't know why the original code did not work; anyways, thanks all!

---

### Post by lithium2007 on 2008-11-11
easybake, 
Thank you very much. It was f--- "A".

---

### Post by mastatux on 2009-08-10
I don't know if anybody looks at this anymore.

The reason conky loads on top of windows is because of the Compiz settings applied to it. 
[B]
1. Go to the "Window Rules" section of the compiz config setting manager. 
2. Add "class=Conky" (no quotes) to the "below" and "sticky" sections.[/B]

"Conky" is the default class assigned to the conky window. If the steps above don't work check your ~/.conkyrc file and look for the line "own_window_class". If you don't need to assign a class for anything else (you probably don't) just erase the line.

Exit the manager and log-out.

This is better for me than a start-up script because I'm impatient. I also game. So swapping out metacity and compiz a lot makes the star-up script seem less useful.


It should now be fixed.

Cheers

---

