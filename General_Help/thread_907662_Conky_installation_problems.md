---
title: "Conky installation problems"
date: 2008-09-01
forum: General Help
---

### Post by Bart_D on 2008-09-01
In installed conky from Synaptic(Xubuntu Hardy) and got this error message when I ran it in the terminal:

```

Conky: missing text block in configuration; exiting
```

When I ran it through ALT+F2, I got nothing.

I have CompizFusion installed and running well, as far as I can tell.  It is set to automatically startup.  I am not running AWN or Emerald or Beryl.


What am I doing wrong?:confused::confused::confused:

---

### Post by frklin on 2008-09-01
Configuration file you've created?
```
~/.conkyrc
```

---

### Post by Bart_D on 2008-09-01
Unless it was done as part of the installation, I have not created any configuration files.

---

### Post by frklin on 2008-09-03
Create a file ~ /.conkyrc and paste the sample configuration, search for conky at [http://gnome-look.org](http://gnome-look.org)
My .conkyrc:
```
# conky configuration

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
#draw_graph_borders no

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans:size=7
#xftfont Terminus:size=7
# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 2,0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
#own_window_type desktop
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 200 5

# Draw shades?
draw_shades yes

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color black
default_shade_color black
default_outline_color black

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 12
gap_y 30

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
use_spacer yes
#Note: doesn't work in conky 1.2 =(

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none


# Possible variables to be used:
#
#      Variable         Arguments                  Description                

# 	addr              (interface)   IP address for an interface
# 	acpiacadapter                   ACPI ac adapter state.                   
# 	acpifan                         ACPI fan state                           
# 	acpitemp                        ACPI temperature.                        
# 	adt746xcpu                      CPU temperature from therm_adt746x       
# 	adt746xfan                      Fan speed from therm_adt746x             
# 	alignr            (num)         Right-justify text, with space of N
# 	alignc                          Align text to centre
# 	battery           (num)         Remaining capasity in ACPI or APM        
# 					battery. ACPI battery number can be      
# 					given as argument (default is BAT0).     
# 	buffers                         Amount of memory buffered                
# 	cached                          Amount of memory cached                  
# 	color             (color)       Change drawing color to color            
# 	cpu                             CPU usage in percents                    
# 	cpubar            (height)      Bar that shows CPU usage, height is      
# 					bar's height in pixels                 
# 	cpugraph          (height),(width) (gradient colour 1) (gradient colour 2)
# 					CPU usage graph, with optional colours in hex,
# 					minus the #.
# 	downspeed         net           Download speed in kilobytes              
# 	downspeedf        net           Download speed in kilobytes with one     
# 					decimal                                  
# 	downspeedgraph    net (height),(width) (gradient colour 1) (gradient colour 2)
# 					Download speed graph, colours defined in
# 					hex, minus the #.
# 	exec              shell command Executes a shell command and displays    
# 					the output in conky. warning: this      
# 					takes a lot more resources than other    
# 					variables. I'd recommend coding wanted   
# 					behaviour in C and posting a patch :-).  
# 	execbar           shell command Same as exec, except if the first value
# 					return is a value between 0-100, it
# 					will use that number for a bar.
# 					The size for the bar is currently fixed,
# 					but that may change in the future.
# 	execgraph         shell command Same as execbar, but graphs values
# 	execi             interval, shell command
#  					Same as exec but with specific interval. 
# 					Interval can't be less than              
# 					update_interval in configuration.        
#	font		  font		Specify a different font.  Only applies
#					to one line.
# 	fs_bar            (height), (fs)Bar that shows how much space is used on 
# 					a file system. height is the height in   
# 					pixels. fs is any file on that file      
# 					system.                                  
# 	fs_free           (fs)          Free space on a file system available    
# 					for users.                               
# 	fs_free_perc      (fs)          Free percentage of space on a file       
# 					system available for users.              
# 	fs_size           (fs)          File system size                         
# 	fs_used           (fs)          File system used space                   
# 	hr                (height)      Horizontal line, height is the height in 
# 					pixels                                   
# 	i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
# 					may be omitted if you have only one I2C  
# 					device. type is either in (or vol)       
# 					meaning voltage, fan meaning fan or
# 					temp/tempf (first in C, second in F)
# 					meaning temperature. n is number of the  
# 					sensor. See /sys/bus/i2c/devices/ on     
# 					your local computer.                     
# 	if_running        (process)     if PROCESS is running, display
# 					everything if_running and the matching $endif
# 	if_existing       (file)        if FILE exists, display everything between
# 					if_existing and the matching $endif
# 	if_mounted        (mountpoint)  if MOUNTPOINT is mounted, display everything between
# 					if_mounted and the matching $endif
# 	else                            Text to show if any of the above are not true
# 	kernel                          Kernel version                          
# 	linkstatus        (interface)   Get the link status for wireless connections
# 	loadavg           (1), (2), (3) System load average, 1 is for past 1     
# 					minute, 2 for past 5 minutes and 3 for   
# 					past 15 minutes.                         
# 	machine                         Machine, i686 for example                
# 	mails                           Mail count in mail spool. You can use    
# 					program like fetchmail to get mails from 
# 					some server using your favourite         
# 					protocol. See also new_mails.            
# 	mem                             Amount of memory in use                  
# 	membar            (height)      Bar that shows amount of memory in use   
# 	memmax                          Total amount of memory                   
# 	memperc                         Percentage of memory in use
# 	
# 	metar_ob_time
# 	metar_temp
# 	metar_tempf                     Temp in F
# 	metar_windchill
# 	metar_dew_point                 There are a bunch of these
# 	metar_rh                        and they are self-explanatory
# 	metar_windspeed
# 	metar_winddir
# 	metar_swinddir
# 	metar_cloud
# 	metar_u2d_time
# 	
# 	ml_upload_counter               total session upload in mb
# 	ml_download_counter             total session download in mb
# 	ml_nshared_files                number of shared files
# 	ml_shared_counter               total session shared in mb, buggy
# 					in some mldonkey versions
# 	ml_tcp_upload_rate              tcp upload rate in kb/s
# 	ml_tcp_download_rate            tcp download rate in kb/s
# 	ml_udp_upload_rate              udp upload rate in kb/s
# 	ml_udp_download_rate            udp download rate in kb/s
# 	ml_ndownloaded_files            number of completed files
# 	ml_ndownloading_files           number of downloading files
# 	
# 	mpd_artist			Artist in current MPD song
# 					(must be enabled at compile)
# 	mpd_album			Album in current MPD song
# 	mpd_bar           (height)      Bar of mpd's progress
# 	mpd_bitrate                     Bitrate of current song
# 	mpd_status                      Playing, stopped, et cetera.
# 	mpd_title			Title of current MPD song
# 	mpd_vol				MPD's volume
# 	mpd_elapsed                     Song's elapsed time
# 	mpd_length                      Song's length
# 	mpd_percent                     Percent of song's progress
# 	new_mails                       Unread mail count in mail spool.         
# 	nodename                        Hostname                                 
# 	outlinecolor      (color)       Change outline color                     
# 	pre_exec          shell command Executes a shell command one time before 
# 					conky displays anything and puts output 
# 					as text.                                 
# 	processes                       Total processes (sleeping and running)   
# 	running_processes               Running processes (not sleeping),        
# 					requires Linux 2.6                       
# 	shadecolor        (color)       Change shading color                     
# 	stippled_hr       (space),      Stippled (dashed) horizontal line        
# 			(height)        
# 	swapbar           (height)      Bar that shows amount of swap in use     
# 	swap                            Amount of swap in use                    
# 	swapmax                         Total amount of swap                     
# 	swapperc                        Percentage of swap in use                
# 	sysname                         System name, Linux for example           
# 	offset            pixels        Move text over by N pixels
# 	tail              logfile, lines (interval)
# 					Displays last N lines of supplied text
# 					text file.  If interval is not supplied,
# 					Conky assumes 2x Conky's interval.
# 					Max of 30 lines.
# 					Max of 30 lines can be displayed.
# 	time              (format)      Local time, see man strftime to get more 
# 					information about format                 
# 	totaldown         net           Total download, overflows at 4 GB on     
# 					Linux with 32-bit arch and there doesn't 
# 					seem to be a way to know how many times  
# 					it has already done that before conky   
# 					has started.                            
# 	top               type, num     This takes arguments in the form:
# 					top <name> <number>
# 					Basically, processes are ranked from 
# 					highest to lowest in terms of cpu
# 					usage, which is what <num> represents.
# 					The types are: "name", "pid", "cpu", and
# 					"mem".
# 					There can be a max of 10 processes listed.
# 	top_mem           type, num     Same as top, except sorted by mem usage
# 					instead of cpu
# 	totalup           net           Total upload, this one too, may overflow 
# 	updates                         Number of updates (for debugging)        
# 	upspeed           net           Upload speed in kilobytes                
# 	upspeedf          net           Upload speed in kilobytes with one       
# 					decimal                                  
# 	upspeedgraph      net (height),(width)  (gradient colour 1) (gradient colour 2)
# 					Upload speed graph, colours defined in
# 					hex, minus the #.
# 	uptime                          Uptime                                   
# 	uptime_short                    Uptime in a shorter format               
# 	
# 	seti_prog                       Seti@home current progress
# 	seti_progbar      (height)      Seti@home current progress bar
# 	seti_credit                     Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#
#
#	alignc	alignr 	wysrodkuj-rownaj do prawej
#	hr				linia
#	stippled_hr		przerywana linia
#
# stuff after 'TEXT' will be formatted on screen

TEXT
${color #ddaa00}Procesor $hr
${color white}Temperatuta: ${color red}CPU: $alignc${color red}$acpitemp C, GPU: ${color red}${texeci 5 ~/skrypty/nvidia}  C
${color white}CPU 0:${alignr}:CPU 1
${color red}${cpu cpu1}%  ${freq_g cpu1}GHz$alignr${color red}${cpu cpu2}%  ${freq_g cpu2}GHz
${color white}${cpugraph cpu1 30,90 dc143c dc143c}$alignr${color white}${cpugraph cpu2 30,90 dc143c dc143c}
${color #DEDEDE}LoadAvg: ${color white}$loadavg ${color #DEDEDE}Pr: ${color white}$processes ${color #DEDEDE}Ur: ${color white}$running_processes
${color #ddaa00}Pamiec $hr
${color #DEDEDE}RAM: ${alignr}all ${color white}$memmax ${color #DEDEDE}buffers ${color white}$buffers
${color #DEDEDE}used ${color white}$memperc% $mem ${membar}
${color #DEDEDE}SWAP: ${alignr}all ${color white}$swapmax ${color #DEDEDE}cached ${color white}$cached
${color #DEDEDE}used ${color white}$swapperc% $swap ${swapbar}
${color #ddaa00}Top $hr
${color #DEDEDE}Highest CPU: ${alignr}Highest MEM:
${font Bitstream Vera Sans:size=6}${color white}${top name 1}${top_mem cpu 1} ${alignr}${top_mem name 1}${top_mem mem 1}
${color white}${top name 2}${top cpu 2} ${alignr}${color white}${top_mem name 2}${top_mem mem 2}
${top name 3}${top cpu 3} ${alignr}${top_mem name 3}${top_mem mem 3}
${top name 4}${top cpu 4} ${alignr}${top_mem name 4}${top_mem mem 4}
${font Bitstream Vera Sans:size=7}${color #ddaa00}Siec $hr
${color #DEDEDE}Down: ${color white}${downspeedf ath0}KB/s ${alignr}${color #DEDEDE}Up: ${color white}${upspeedf ath0}KB/s
${color white}${downspeedgraph ath0 20,99 00ff00 00ff00} ${alignr}${upspeedgraph ath0 20,99 dc143c dc143c}
${color white}Pobrano: ${totaldown ath0}  || Wyslano: ${totalup ath0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
${color #DEDEDE}IP: ${color white}${addr ath0} ${alignr}${color #DEDEDE}
${wireless_essid ath0}$color2 - MAC : $color4${wireless_ap ath0}
Wifi Level : $color4${wireless_link_qual ath0}$color2 /$color4 ${wireless_link_qual_max ath0}$color2 - Quality: $color4 ${wireless_link_qual_perc ath0}
${color #DEDEDE}Ping Google$alignr ${execi 10 ping -n -c 1 66.249.93.104 | grep '64 bytes from ' | sed -e 's/.*time=//; s/ ms.*//' 2>/dev/null} ms
${color #DEDEDE}Ping Router$alignr ${execi 10 ping -n -c 1 192.168.1.1 | grep '64 bytes from ' | sed -e 's/.*time=//; s/ ms.*//' 2>/dev/null} ms
${color #ddaa00}Dyski $hr
${color #DEDEDE}System sda1 ${color red}${hddtemp /dev/sda} ${alignr}${color #DEDEDE}all ${color white}${fs_size /}
${color #DEDEDE}used ${color white}${fs_used_perc /}% ${fs_used /} ${alignr}${color #DEDEDE}free ${color white}${fs_free_perc /}% ${fs_free /}
${color white}${fs_bar 3,200 /}
${color #DEDEDE}Home sda3 ${color red}${hddtemp /dev/sda} ${alignr}${color #DEDEDE}all ${color white}${fs_size /home}
${color #DEDEDE}used ${color white}${fs_used_perc /home}% ${fs_used /home}${alignr}${color #DEDEDE}free ${color white}${fs_free_perc /home}% ${fs_free /home}
${color white}${fs_bar 3,200 /home}
${color #DEDEDE}SD Card sdb1 ${alignr}${color #DEDEDE}all ${color white}${fs_size /media/disk}
${color DEDEDE}used ${color white}${fs_used_perc /media/disk}% ${fs_used /media/disk}${alignr}${color #DEDEDE}free ${color white}${fs_free_perc /media/disk}% ${fs_free /media/disk}
${color white}${fs_bar 3,200 /media/disk}
${color white}Odczyt / zapis dysku: $diskio
${color white}${diskiograph 15,220 f9f604 f9f604}
${color #ddaa00}Bateria $hr
${color white}$acpiacadapter$color4  $battery
Pozostaly czas :$color4  $battery_time
${battery_bar 6,160}
${color #ddaa00}System $hr
${alignc}${color white}$sysname $kernel ${color #DEDEDE}on ${color white}$machine
${alignc}${color white}${exec whoami}@$nodename ${color #DEDEDE}Czas pracy: ${color white}$uptime
${color #ddaa00}Poczta $hr
${color white}${texeci 600 ~/skrypty/gmail}
${color #ddaa00}$hr
```

---

### Post by noremac on 2008-09-03
Yeah, you will need a config file for the program to look at and see. Do something like 

```
gedit /home/username/.conkyrc
```

Then paste in what was already posted, something your make, or try mine. 

```
background yes
font Zekton:size=7
xftfont Zekton:size=7
use_xft yes
xftalpha 0.1
update_interval 1.0
total_run_times 0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 220 5
maximum_width 220
default_color white
default_shade_color black
default_outline_color black
alignment top_right
gap_x 2
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale no
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Zekton:style=Bold:pixelsize=42}${alignc}${time %H:%M:%S}${font Zekton:size=7}
SYSTEM ${hr 1 }

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Processes: ${alignr}$processes ($running_processes running)
Load: ${alignr}$loadavg
CPU       ${alignc} ${freq}MHz / ${acpitemp}C ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

FILESYSTEM ${hr 1}${color}

Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}
Storage: ${alignr}${fs_free /media/Media} / ${fs_size /media/Media}
${fs_bar 4 /media/Media}

NETWORK ${hr 1}${color}

Down ${downspeed eth1} k/s ${alignr}Up ${upspeed eth1} k/s
${downspeedgraph eth1 25,107} ${alignr}${upspeedgraph eth1 25,107}
Total ${totaldown eth1} ${alignr}Total ${totalup eth1}

```

Pending how your system is set up, you may have to change all the "eth1" codes to eth0 in order to show your network usage. Same goes for hard drive space. Have to customize it to your system. Once you get it where you like it, its such a useful program.

-Cameron

---

