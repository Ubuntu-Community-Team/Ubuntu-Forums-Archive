---
title: "conky issues with $if_mounted"
date: 2008-08-24
forum: General Help
---

### Post by DSL5 on 2008-08-24
I am dual booting XP with Hardy and I have conky running on my desktop.

Here's the issue. I want conky to display information about my Windows hard drive (Local Disk) only when the disk is mounted.

I tried wrapping it in a ${if_mounted /media/Local Disk} ${endif} statement, but that causes the information to never show up, even if it is mounted!

Does anybody know how to get this to work?

here's my .conkyrc:

```

background yes
no_buffers no
out_to_console no
top_cpu_separate no
max_port_monitor_connections 256
cpu_avg_samples 2
net_avg_samples 1
total_run_times 0
update_interval 0
music_player_interval 3
uppercase no
override_utf8_locale yes
short_units no
pad_percents 0
text_buffer_size 256
max_user_text 16384
font Bitstream Charter:style=Regular
use_xft yes
xftalpha 0.1
xftfont 123:size=8
own_window yes
own_window_colour ffffff
own_window_transparent yes
own_window_hints undecorated, sticky, below, skip_pager, skip_taskbar
own_window_type override
double_buffer yes
draw_borders no
draw_graph_borders no
draw_shades yes
draw_outline no
stippled_borders 4
max_specials 512
alignment top_right
gap_x 10
gap_y 10
maximum_width 400
minimum_size 250 5
use_spacer none
border_margin 4
border_width 1
default_color 808080
default_outline_color 000000
default_shade_color 000000
color0 ff0000
color1 0000ff
color2 ffff00
color3 00ff00
color4 ffafaf
color5 ffc800
color6 ff00ff
color7 00ffff
color8 808080
color9 404040

TEXT

${font openlogos:size=20}U${font Arial:size=20}${color Tan1}GNU${color Ivory}LINUX${font openlogos:size=20}t
${voffset -90}
${color DimGray}
${font}
${font Arial:bold:size=10}${color Tan1}SYSTEM ${color DarkSlateGray} ${hr 2}
$font${color DimGray}$sysname $kernel $alignr $machine
Computer ID$alignr$nodename
Intel Pentium D $alignr${freq_g cpu0}Ghz
Uptime $alignr${uptime}
File System $alignr${fs_type}
${font Arial:bold:size=10}${color Tan1}PROCESSORS ${color DarkSlateGray}${hr 2}
$font${color DimGray}CPU  ${cpu cpu1}% ${cpubar cpu1}
${font Arial:bold:size=10}${color Tan1}MEMORY ${color DarkSlateGray}${hr 2}
$font${color DimGray}MEM $alignc $mem / $memmax $alignr $memperc%
$membar
SWAP $alignc $swap / $swapmax $alignr $swapperc%
$swapbar
${font Arial:bold:size=10}${color Tan1}BATTERY ${color DarkSlateGray}${hr 2}
$font${color DimGray}BAT$alignr${battery BAT1}
${battery_bar BAT1}
${font Arial:bold:size=10}${color Tan1}HDD ${color DarkSlateGray}${hr 2}
$font${color DimGray}Linux $alignc ${fs_used /} / ${fs_size /}
${fs_bar /}
${fs_used_perc /}%$alignr${fs_free_perc /}% ${if_mounted /media/Local Disk}
Windows $alignc ${fs_used /media/Local Disk} / ${fs_size /media/Local Disk}
${fs_bar /media/Local Disk}
${fs_used_perc /media/Local Disk}%$alignr${fs_free_perc /media/Local Disk}%
${endif}
${font Arial:bold:size=10}${color Tan1}TOP PROCESSES ${color DarkSlateGray}${hr 2}
${color DimGray}$font${top_mem name 2}${alignr}${top mem 2} %
$font${top_mem name 3}${alignr}${top mem 3} %
$font${top_mem name 4}${alignr}${top mem 4} %
$font${top_mem name 5}${alignr}${top mem 5} %
${font Arial:bold:size=10}${color Tan2}NETWORK ${color DarkSlateGray}${hr 2}
$font${color DimGray}External IP$alignr${execi 3600 wget -O - http://whatismyip.org/ | tail}
$alignc Wireless
$stippled_hr 2
IP$alignr ${addr eth0}

Down: ${downspeed eth0} kb/s $alignr Downloaded: ${totaldown eth0}
Up: ${upspeed eth0} kb/s $alignr Uploaded: ${totalup eth0}
$alignc Wired
$stippled_hr 2
IP$alignr ${addr eth1}

Down: ${downspeed eth1} kb/s $alignr Downloaded: ${totaldown eth1}
Up: ${upspeed eth1} kb/s $alignr Uploaded: ${totalup eth1}

${font Arial:bold:size=10}${color Tan2}MAIL ${color DarkSlateGray}${hr 2}
${color DimGray}${font}GMail: You have ${texeci 60 perl ~/.scripts/gmail.pl n} ${color}
${execi 60 perl ~/.scripts/gmail.pl s}
${if_running rhythmbox}${font Arial:bold:size=10}${color Tan2}MUSIC ${color DarkSlateGray}${hr 2}
${color DimGray}${font}Now Playing: ${exec rhythmbox-client --print-playing --no-start}
$endif
```

---

### Post by DSL5 on 2008-08-27
*bump*

---

### Post by detroit/zero on 2008-08-30
I'm not sure what the difference is after looking at your .conkyrc, but here's the relevant section from mine that I have doing exactly what you describe (screenshots attached):
```
${color2}/home:$color ${fs_used /home/zero}/${fs_size /home/zero} - ${alignr}${fs_free_perc /home/zero}% Free
${fs_bar 3,160 /home/zero}${alignr}${color2}R${color}${diskiograph_read /dev/sda7 9,30 0000dd d5d5d5} ${color2}W${color}${diskiograph_write /dev/sda7 9,30 0000dd d5d5d5}${if_mounted /media/SQ004286V02}
${color2}Vista: $color${fs_used /media/SQ004286V02}/${fs_size /media/SQ004286V02} -${alignr}${fs_free_perc /media/SQ004286V02}% Free
${fs_bar 3,160 /media/SQ004286V02}${alignr}${color2}R${color}${diskiograph_read /dev/sda3 9,30 0000dd d5d5d5} ${color2}W${color}${diskiograph_write /dev/sda3 9,30 0000dd d5d5d5}${endif}${if_mounted /media/disk}
```I notice your calling your Windows drive name "Local Disk". That space in there could be the source of a problem. Any time you work with spaces in filenames inside a terminal, you have to proceed the space with a backslash [COLOR=Red]\[/COLOR]; for example - /home/username/My[COLOR=Red]\[/COLOR] File.txt or /home/username/Videos/My[COLOR=Red]\[/COLOR] Video.avi

I don't know if that will work inside conky, though. If you can, I'd suggest renaming it to something without a space in the name to avoid the hassle altogether. If renaming isn't an option, I would then suggest using the drive label from /dev - /dev/sda4 or /dev/hdb or whatever it may be. If you don't know what it is, look for it inside GParted (or partition-management tool of your choice).

You seem to have it right, too, that the $if_mounted statement goes at the end of the previous line of text to be displayed, otherwise conky ends up displaying a blank line in its place.

Get back to me if none of that works and we'll see what we can come up with.

I'll attach my entire .conkyrc for you, in case you want to pour through it.

---

### Post by DSL5 on 2008-09-01
I'm afraid to change Local Disk to something else in case that somehow messes up Windows.

I tried doing ${if_mounted /media/Local\ Disk}, but it still didn't work.

I looked in GParted, and my Windows partition is /dev/sda1, so I tried ${if_mounted /dev/sda1}, and it still doesn't work.

Ugh! why doesn't it like me?!?!?!?

---

### Post by detroit/zero on 2008-09-01
> **DSL5 said:**
> I'm afraid to change Local Disk to something else in case that somehow messes up Windows.

I tried doing ${if_mounted /media/Local\ Disk}, but it still didn't work.

I looked in GParted, and my Windows partition is /dev/sda1, so I tried ${if_mounted /dev/sda1}, and it still doesn't work.

Ugh! why doesn't it like me?!?!?!?
Hmm.. yeah, that's a good question.

Once the drive is mounted, you can right click>properties on the desktop icon (if you have it set to appear on the desktop, if not, open nautilus and go to /media) and under the volume and drive tabs there are options to set a mount point that you can name  yourself. I'm not entirely clear on how that works, though, so you'll have to read up on it before you give it a try.

You should try to post over in the big ["post your .conkyrc" thread]("http://ubuntuforums.org/showthread.php?t=281865&page=344"). There are people there who know a lot more than I do about conky. I'm sure one of them can figure it out.

---

### Post by aidenscool09 on 2010-07-18
I know this may be a little late. But i this is to help anyone else having the same problem. What you do is, for the "$if_mounted" command where you have 
```
"${if_mounted /media/Local Disk}
```

you would need to change it to 
```
${if_mounted /media/Local Disk/}
```
for it to work properly. I had the same problem. I spent several hours googling etc. And i found out that it needed the "/" at the end of the File System location.
If that doesn't work, try 
```
${if_mounted /dev/sda1/}
```
with the "/" on the end also.

---

### Post by niceshorts on 2013-03-21
Me too like DSL5 have the same problem with disk name with space problem.

here is little script.

```

${color 33001A}${font StyleBats:size=35}G${font} Lacie${color FFFFFF}
${if_mounted /media/nili/Lacie Disk}
${color 1C1C1C}Size: ${alignr}${fs_size /media/nili/Lacie Disk}
${color 33001A}${fs_bar 3,83 /media/nili/Lacie Disk}${color}
${color 1C1C1C}Free: ${alignc}${fs_free /media/nili/Lacie Disk} ${alignr}${color 33001A}(${fs_free_perc /media/nili/Lacie Disk}%)${color}
${color 1C1C1C}Used: ${alignc}${fs_used /media/nili/Lacie Disk} ${alignr}${color 33001A}(${fs_used_perc /media/nili/Lacie Disk}%)${color}
${else}${color 1C1C1C}Disk: Not mounted${color}
${endif}

```

The problem as is described above is the same for me, my external disk Lacie Disk has this space between lacie and disk which creates problem to display info when the disk is mounted. "To remember, the disk Lacie is mounted but show not mounted because of the Space on the disk name".

[IMG]http://img845.imageshack.us/img845/3973/screenshotarea201303201.png[/IMG]

while on Disk Toshiba plus Seagate with the same code work OK, because Toshiba and Seagate doesn't have space. 
So how to fix the problem of space on the code above?

P.S. i not want to change now the disk name, i'm too late and have the programs that work with Lacie Disk. Tried aidenscool09 suggestion but none of them worked for me.
sorry to bump this old thread, but really this problem need a solution if there are any.


so,

Any other suggestion please?
Thank you very much!

---

### Post by oldos2er on 2013-03-21
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

