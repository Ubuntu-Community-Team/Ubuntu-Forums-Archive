---
title: "[SOLVED] &amp;quot;Permission Denied&amp;quot; for startup script"
date: 2008-11-29
forum: General Help
---

### Post by greyfox1 on 2008-11-29
Hello,

I decided to try out conky today by following [this tutorial]("http://ubuntuforums.org/showthread.php?t=867076").  Everything seems OK except that I can't get the startup script I created to run-- it's an entry in my Sessions settings but it doesn't start when I log in.  I tried to execute the script from Terminal and I get simply: "bash: /home/rick/.conky/startconky.sh: Permission denied".  Just to test I tried to run the script as root but I get the same results.  Here are the specifics:

My conkymain file is in ~/.conky as is my startup script (startconky)

Contents of startconky are: ```
sleep 20 &&
conky -c ~/.conky/conkymain &
#sleep 0 &&
#conky -c ~/Conky/conkyforecast &
```


I made sure to execute ```
chmod a+x ~/.conky/startconky
```

My conkymain file, which I grabbed from [this thread]("http://ubuntuforums.org/showthread.php?t=281865"): ```
# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}
```




What am I doing wrong here?  Advice would be appreciated.

---

### Post by x1a4 on 2008-11-29
Hi,
Change ownership of startconky.sh to *user:group*
Where *user:group* is your user name (I'm assuming 'rick') and the default group for that user.  Most likely that's either 'rick' or 'users'
```
chown rick:rick /home/rick/.conky/startconky.sh
```

---

### Post by greyfox1 on 2008-11-30
Ok I tried your suggestion (you are correct about my user name) but I still get the same error.  I checked the file properties using Nautilus and confirmed that I am the owner of the startconky file, have read-write access, and that "Allow executing file as a program" is checked.

One thing: the file is named startconky (no file extension), not startconky.sh as you mentioned in your post.  Should that make any difference?

---

### Post by greyfox1 on 2008-12-02
bump

---

### Post by bodhi.zazen on 2008-12-02
Do you have a separate home partition ? If so is it mounted noexec ?

---

### Post by greyfox1 on 2008-12-02
Aha, maybe we're onto something.  I do have a second hard disk mounted at /home/rick.  Here's the entry from fstab:

/dev/sdb1                                  /home/rick     ext3         owner,errors=remount-ro,users,user  0  0 

Should the mount options be changed?

---

### Post by bodhi.zazen on 2008-12-03
what is the output of :

```
mount | grep sdb1
```

---

### Post by greyfox1 on 2008-12-03
Bingo.

```
/dev/sdb1 on /home/rick type ext3 (rw,noexec,nosuid,nodev,errors=remount-ro)
```

How do I change that?

---

### Post by bodhi.zazen on 2008-12-03
Edit /etc/fstab and add the exec option :

```
/dev/sdb1 /home/rick ext3 owner,errors=remount-ro,users,exec 0 0
```

---

### Post by greyfox1 on 2008-12-10
Thanks bodhi, that did the trick!

---

