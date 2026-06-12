---
title: "Custom made Conky for me???"
date: 2008-10-31
forum: General Help
---

### Post by w1av on 2008-10-31
Hello,

I have managed to install and run Conky on my desktop with a conky.conf file I copied to /etc/conky.....works GREAT but I cannot seem to figure out, after looking and reading, how to customize it as far as showing all my partitions!!! It does show the root Ubuntu partition though but I want to have the other partitions on there as well. Could someone help me with this???? There may be just a few other things I would like to see appear also. Such as IP address and weather. But I will settle for the  partitions for now.
Thanks....bob:)

---

### Post by king.pest on 2008-10-31
hey, 

the first thing you should do is to read conky manual page (man conky), where all the config options are described, along with some examples. then you could take a look at [this]("http://ubuntuforums.org/showthread.php?t=281865") thread, where people post their .conkyrc files, copy them to your computer, adopt, adapt and improve:)
if you want conky to show you free space on other partitions than root, you can just add:
```
Home: ${fs_free /home}
```
to your .conkyrc for example.
good luck with customizing!

---

### Post by w1av on 2008-10-31
OK but I still don't understand the code. For example, here is a list of the HDD partitions I want to display:

hda1 WinXP
hda2 ubuntu (I think this one is already on there)
hda3 swap
hda4 fat32

hdb1 storage (music files)
hdb2 storage (completed music)
hdb3 storage (misc)

So for each one I would enter on a line for my WinXP partition for example:  WinXP ${fs_free /hda1} Is that right?

For my hda4:  Fat32 ${fs_free /hda4}  Is this right???

The entrie all go on separate lines....Then I would have to configure COLOR......



Home: ${fs_free /home}

---

### Post by king.pest on 2008-10-31
conky understands mount points, not devices. for example, for your hda4, you should rather do something like:```
${fs_free /mount_point_of_your_hda4}
```to see where your devices are mounted, just type mount with a grep. here's how it looks on my computer (i got scsi disks, so they're sda's)```

kp ~  $  mount|grep sda
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
/dev/sda3 on /home type ext3 (rw,relatime)
```

---

### Post by w1av on 2008-10-31
OK I think I get it...

Wouldnt the mount point of, say for example my FAT32 partition be /dev/hda4? Thats how I have always mounted my partitions in the past even with different distros of linux.

FAT32:  ${fs_free /dev/hda4}  That is the mount point according to my computer. I looked at the man page but it doesnt give more concrete detailed samles for most of the options and variables....it explains all the options and what they are/do but no clear examples!!!! I have looked at a bunch of other conky.conf files on here posted by other users but can't find any info on displaying more partition info. Sorry to be a pest!!!! Bob:confused:

---

### Post by m_duck on 2008-10-31
The "/dev/hda4" type thing is a link to the device, but in order to be used, the device must be mounted. For example, my windows drive is "/dev/sda1" but it is mounted in "/media/Windows". It is your equivalent of /media/Windows that conky needs to see. 

If you run ```
df -a
```in a terminal, it will show you disks and mount point, (or run the mount command with grep as said above). Then once you find your mount points put it into conky like king.pest mentions.

In terms of color, you need to use the $color tag:
```
${color red} - for red
${color black} - for black
${color 000000} - also black
${color} - reset to default colour
```

EDIT: Also, take a look at [this](http://conky.sourceforge.net/variables.html). It lists a all of the variables in conky that are built in. If you look at the thread mentioned above as well, it helps to be able to see how to use each variable.

---

### Post by king.pest on 2008-10-31
hmm... i'm not quite sure if it's possible to mount /dev/hda4 at /dev/hda4, which is actually a special file for the device. would you mind posting the output of ```
mount|grep hda
``` from your computer?
and as for showing multiple partitions free space, here's an example found somewhere on the web (it's not mine):```

    ${font} Cpu: ${color E7E7E7}${font} ${cpubar 4,50}  ${color} Mem: ${color E7E7E7}${font}    ${membar 4,50}${color}  | Net: ${color E7E7E7}${font}   ${downspeed eth0} Kb/s ${color} ${totaldown eth0} down${color}  | ${color E7E7E7}       ${upspeed eth0} Kb/s ${color}   ${totalup eth0} up${color}      |  Root: ${color E7E7E7}${font} ${fs_free /} ${color}   Home: ${color E7E7E7}${font}    ${fs_free /home} ${color}       | Email: ${color E7E7E7}        ${execi 60 perl ~/Skrypty/gmail.pl n} new messages ${color}     | Weather:  ${color E7E7E7}${font}      ${execi 1800 $HOME/Skrypty/pogodynka.sh}${color}        | Top:  ${color E7E7E7}${font}  ${top name 1}${top name 2}
${voffset -11}${alignr 10}${color E7E7E7}${time %e} ${color}${time %B}
```note that there are two partitions being monitored, the root (/) and the home (/home).

---

### Post by w1av on 2008-10-31
But I still don't know what a real entry looks like! For example, what does the entry look like on your conky.conf for displaying more partitions? I guess what I am asking is what does a mount point entry look like? I will do those commands when I get home later and see what the actual mount points are. But I still don't know the EXACT thing to type in when I see what the mount points are. So there is, in Ubuntu (8.04) a folder called "media" and inside that folder are your mount points? Very similar to Kanotix, a distribution I used for a few years. There was also a media folder with all the hdd's listed....

---

### Post by king.pest on 2008-10-31
take a look at a config I showed in the previous post, it says exactly what to put in a config file in order to have free space checked on multiple disk partitions. once you check what are your mount points, just change the apropriate parts of this config file and you're done. 
most devices in Ubuntu are mounted in /media, that's correct. if you didn't make any custom changes to your /etc/fstab file (and I assume you didn't), then that's where your disks are probably mounted.

---

### Post by w1av on 2008-10-31
I will post those things you guys mentioned above, later today and then continue to work on it...thanks for help and I will post back tonight...bob:)

---

### Post by m_duck on 2008-10-31
First of all, I would make a conky config file in your home folder. In terminal type:```
sudo touch .conkyrc
```This will make a hidden file called .conkyrc in /home/<your_user_name>/.conkyrc.

My "mount | grep sd" gives:
```
/dev/sdb2 on [COLOR=Red]/[/COLOR] type ext3 (rw,relatime,errors=remount-ro)
/dev/sdb3 on [COLOR=Red]/home[/COLOR] type ext3 (rw,relatime)
/dev/sdc1 on [COLOR=Red]/media/Media[/COLOR] type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on [COLOR=Red]/media/Windows[/COLOR] type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```bearing in mind I'm using sata disks, you may need to use "mount | grep hd".

I have highlighted my mount points in red. These are what conky needs from the output of the command when run on your computer.

As an example, a coloured config line, showing some info for the /home partition could be:
```
${color red}Home Partition: ${fs_free /home}${alignr}(${fs_free_perc /home}%)
${color green}${fs_bar}

```Which would give a display as shown in the first attachment.

One of my conky configs looks like the second pic in the attachments and the code is as follows: ```
use_xft yes
xftfont Monospace:size=8
# DeJaVu Sans Mono:size=9
alignment top_middle
xftalpha 0.8
update_interval 1.0
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
draw_shades no
draw_outline no
draw_borders no
stippled_borders 10
border_margin 4
border_width 1
default_shade_color grey
default_outline_color black
default_color 000000 #was 333333
use_spacer none
uppercase no
gap_x 5
gap_y 5
minimum_size 800 5
maximum_width 800
override_utf8_locale yes

TEXT
${alignc}/ ${fs_bar 5,50 /} | /home ${fs_bar 5,50 /home} | /media ${fs_bar 5,50 /media/Media} | /windows ${fs_bar 5,50 /media/Windows}
```

If you copy from "use_xft yes" to "TEXT" into your .conkyrc file, then you can add your configuration options underneath. You may need to change a few bits round though, for example, if you are running a top panel, you will need a larger number after "gap_y" to account for this.

---

### Post by w1av on 2008-10-31
Here is my df -a:
[COLOR="DarkGreen"][COLOR="DarkGreen"][COLOR="DarkGreen"]
bob@bob-desktop:~$ df -a
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2             29296252   3637440  25658812  13% /
proc                         0         0         0   -  /proc
/sys                         0         0         0   -  /sys
varrun                  517684        92    517592   1% /var/run
varlock                 517684         0    517684   0% /var/lock
udev                    517684        72    517612   1% /dev
devshm                  517684       120    517564   1% /dev/shm
devpts                       0         0         0   -  /dev/pts
lrm                     517684     39780    477904   8% /lib/modules/2.6.24-21-generic/volatile
securityfs                   0         0         0   -  /sys/kernel/security
gvfs-fuse-daemon      29296252   3637440  25658812  13% /home/bob/.gvfs
/dev/sdc                990200       344    989856   1% /media/BOBPOD
/dev/sda1             39988304  18667112  21321192  47% /media/disk
/dev/sda4              6896716       280   6896436   1% /media/disk-1
/dev/sdb1             38675008   3829536  34845472  10% /media/MUSICBACKUP
/dev/sdb2             39261280   1639040  37622240   5% /media/MAINMXFILES
/dev/sdb3             39253248   3367488  35885760   9% /media/STORAGE[/COLOR][/COLOR][/COLOR]

Apparently it calls the hard drives "sda and sdb" instead of "hda and hdb" so I guess my mount points would be /dev/sda1 and so on.....

Here's what happens when I run conky from terminal as regular user:

[COLOR="DarkGreen"]bob@bob-desktop:~$ conky
Conky: /home/bob/.conkyrc: 9: config file error
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: can't open '/sys/class/hwmon/hwmon0/device/temp1_input': No such file or directory
please check your device or remove this var from Conky[/COLOR]


If I run as root it works fine! Does anyone know why I have to be root to run it???? 

Thanks...Bob

---

### Post by king.pest on 2008-11-02
do you mean that when you run it as a regular user, you're getting this error message but conky starts, and while you run it as root, you don't get any error message or what? the error says that you're checking a temperature of a nonexistent device, perhaps just remove this check from your config file?

---

### Post by m_l17 on 2008-11-03
Take a look at these:

[http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/#comment-1286]("http://linuxowns.wordpress.com/2008/04/04/create-a-custum-conky-setup/#comment-1286")

[http://ubuntuforums.org/showthread.php?t=205865&highlight=conky]("http://ubuntuforums.org/showthread.php?t=205865&highlight=conky")

---

### Post by m_duck on 2008-11-07
[COLOR=DarkGreen][COLOR=Black]```
Conky: can't open '/sys/class/hwmon/hwmon0/device/temp1_input': No such file or directory
```Does the temperature referred to by this line in the error message display in the conky? If not I would delete the line containing "/sys/class/hwmon/....." from your .conkyrc.

The notification about "use_spacer" can be ignored. Alternatively to get rid of it, you could add the line
```
use_spacer right
```in your .conkyrc somewhere above "TEXT". Once this is done, I would have thought conky would run as a regular user. I think it is probably that temperature line that is requiring the root privileges.

From your "df -a" the mount points you need are:
```
/ /media/BOBPOD /media/disk /media/disk-1 /media/MUSICBACKUP /media/MAINMXFILES /media/STORAGE
```You could display as many / few of these as you like. The disk space variables available are:
```
fs_bar fs_free fs_free_perc fs_size fs_type fs_used
```and they are used like:
```
${fs_free_perc <mountpoint>}
```so
```
${fs_free_perc /media/disk-1}
```would display the percentage of free space on you disk-1 partition / disk.
[/COLOR] [/COLOR]

---

