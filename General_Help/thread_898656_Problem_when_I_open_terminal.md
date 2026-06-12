---
title: "Problem when I open terminal"
date: 2008-08-23
forum: General Help
---

### Post by r2d2klapa on 2008-08-23
Hey

I have a problem when i open the terminal... the system turns really slow it's only when i open it i don't know why it happens 
i have intel core 2 duo 1.8 and 3gb ram 

I've tried openning a lot of windows and everything works fine except when i open the terminal ...

plz help

---

### Post by Nepherte on 2008-08-23
You could use the command top to figure out what is eating up resources:
```
top
```

---

### Post by r2d2klapa on 2008-08-23
```
Tasks: 127 total,   3 running, 124 sleeping,   0 stopped,   0 zombie
Cpu(s): 37.9%us,  0.3%sy,  0.0%ni, 61.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3106796k total,  1396060k used,  1710736k free,   357256k buffers
Swap:   976552k total,        0k used,   976552k free,   619180k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5692 root      20   0  432m  72m 8480 R   75  2.4   0:32.26 Xorg               
 6334 oscar     20   0 78456  20m  11m R    1  0.7   0:00.32 gnome-terminal     
 6187 oscar     20   0 26720  19m 6988 S    1  0.7   0:03.80 compiz.real        
 6092 oscar     20   0 40388  10m 8284 S    0  0.3   0:00.41 gnome-settings-    
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.28 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   46 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   47 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1   
```

there it is ..any help?

---

### Post by LateNiteTV on 2008-08-23
xorg is raping your system.

---

### Post by r2d2klapa on 2008-08-23
and what can i do to solve this ... i'm new with ubuntu plz help

---

### Post by LateNiteTV on 2008-08-23
are you using a custom gnome theme or something?

---

### Post by jerome1232 on 2008-08-23
The only thing I can think of is if I have compiz set to ridiculous settings xorg starts eating 40-50% cpu idling, but it is universal not just when I open gnome-terminal.

---

### Post by mb_webguy on 2008-08-23
Just out of curiousity, do that again, and then type ">" to sort by memory usage.

I don't know why the Xorg process is using that much of your CPU, but you're using a moderately significant amount of memory, too...  I have a fairly similar system to yours (Core 2 Duo 2GHz, 2GB memory), and even though I'm running several programs at once (e.g. Firefox with multiple tabs, Amarok, Deluge, a terminal, a couple of Nautilus windows) and a lot of Compiz plugins, I'm using a fraction of the system resources you are.

---

### Post by r2d2klapa on 2008-08-23
i have a gnome cutom them now but the problem ocurred when i had the default theme too .... 
i have "ridiculous" settings but it works great until i open the terminal

---

### Post by r2d2klapa on 2008-08-23
```
top - 14:17:31 up 51 min,  2 users,  load average: 0.63, 0.33, 0.17
Tasks: 128 total,   2 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s): 30.0%us,  0.5%sy,  0.0%ni, 69.5%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3106796k total,  1526308k used,  1580488k free,   414060k buffers
Swap:   976552k total,        0k used,   976552k free,   713944k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND          
 7373 root      20   0  429m  69m 8168 R   58  2.3   2:15.83 Xorg             
 7722 oscar     20   0  126m  47m  19m S    1  1.6   0:05.50 firefox          
 7570 oscar     20   0 64228  24m  13m S    0  0.8   0:00.69 nautilus         
 7567 oscar     20   0 43356  22m  15m S    0  0.7   0:01.64 gnome-panel      
 7868 oscar     20   0 78344  20m  11m S    0  0.7   0:00.44 gnome-terminal   
 7639 oscar     20   0 26872  18m 6988 S    0  0.6   0:03.60 compiz.real      
 7700 oscar     20   0 48512  14m 9.8m S    0  0.5   0:00.20 mixer_applet2    
 7654 oscar     20   0 26516  14m 8640 S    0  0.5   0:00.14 python           
 7393 oscar     20   0 38792  13m 9512 S    0  0.5   0:00.30 x-session-manag  
 7644 oscar     20   0 29916  13m 9220 S    0  0.5   0:00.20 update-notifier  
 7703 oscar     20   0 30488  13m 8960 S    0  0.4   0:00.18 fast-user-switc  
 7670 oscar     20   0 24476  12m 7252 S    0  0.4   0:00.12 python           
 7710 oscar     20   0 21268  11m 7232 S    0  0.4   0:00.20 gtk-window-deco  
 7667 oscar     20   0 28400  11m 8108 S    0  0.4   0:00.36 nm-applet        
 7653 oscar     20   0 28296  11m 8380 S    0  0.4   0:00.18 trashapplet      
 7659 oscar     39  19 30688  10m 2324 S    0  0.3   0:00.04 trackerd         
 7500 oscar     20   0 40380  10m 8284 S    0  0.3   0:00.28 gnome-settings-  


```
that's when i type ">"

---

### Post by Rich78 on 2008-08-23
Try typing:

sudo gedit /etc/X11/xorg.conf

and post the results.

---

### Post by Nepherte on 2008-08-23
A reboot doesn't help? So let me get this clear: you only have this as soon as you open up the terminal? 

You are running compiz btw (compiz.real in your top list).

---

### Post by r2d2klapa on 2008-08-23
reboot and relog help....  i only have this as sonn as i open up the terminal

here's xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

---

### Post by mb_webguy on 2008-08-23
I notice you're not using any restricted drivers...  What kind of video card do you have?

---

### Post by r2d2klapa on 2008-08-23
it's intel

---

### Post by Rich78 on 2008-08-23
I think it's definitely a video driver issue. 

Try editing the Section "Device" to read the following:

Section "Device"
	Identifier	"Configured Video Device"
        Driver "intel"
EndSection

You'll need to at least reboot the XORG in order to see the changes.  CTRL + ALT + BackSpace.  But it may be worth a fresh reboot.

---

### Post by Nepherte on 2008-08-24
I have a intel on board vga on my laptop and I don't have to specify Driver= "Intel". So I don't think that would solve anything. Trying won't harm of course if you backup your original one first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

---

