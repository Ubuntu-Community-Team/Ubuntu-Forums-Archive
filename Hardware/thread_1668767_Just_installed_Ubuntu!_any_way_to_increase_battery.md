---
title: "Just installed Ubuntu! any way to increase battery life?"
date: 2011-01-16
forum: Hardware
---

### Post by elmonkey009 on 2011-01-16
OKay I installed ubuntu because I wanted a laptop that can play games in class! Lol. like solitaire or tetris. because in windows i get tempted to play league of legends or dota and involves way too much clicking. I get distracted easier too. Okay for some reason i get about 2hr 15min on battery life with ubuntu, but with windows 7 i get 2hours and 34 min. Any way of getting more battery life on this laptop.

Specs
MSI GX720
T9600
9600m gt
232gb 7200rpm
4gb ddr2 800mhz
gn-ws30n-rh wireless

---

### Post by ronnielsen1 on 2011-01-16
> 
1) In power management reduce display backlight time and inactive time before sleep to low settings.

2) Edit your screensaver and power management settings so that screensavers do not run when on battery power, or perhaps run for only a minute or so. Some of them are surprisingly CPU intensive. 

3) As root edit the file /etc/default/acpi-support and change the line
ENABLE_LAPTOP_MODE=false to ENABLE_LAPTOP_MODE=true. As the comments suggest, if you experience hangs/freezes/similar problems after this you may need to change it back to false.

4) Depending on your work habits and typical usage, you may want to reduce the hd spindown time below default in the same file.
[http://ubuntuforums.org/archive/index.php/t-1031523.html](http://ubuntuforums.org/archive/index.php/t-1031523.html)

---

### Post by elmonkey009 on 2011-01-16
thanks for the reply. The first one is the first thing i did when installing ubuntu.
for enabling laptop mode it says in mine.
Note: to enable "laptop mode" install the laptop-mode-tools package and configure
it in etc/laptop-mode/laptop-mode.conf
so i have it installed i go to that
and from there on i have no idea what to do.
and for some reason everything opens as read only.

---

### Post by ronnielsen1 on 2011-01-16
You would have to configure it in etc/laptop-mode/laptop-mode.conf by opening a terminal and typing in gksudo gedit /etc/laptop-mode/laptop-mode.conf

I'm on a laptop that's not capable of Ubuntu right now (Old - so I can't double check this) but this should work.Give it a try.

---

### Post by elmonkey009 on 2011-01-16
is that how you edit everyfile by putting gksudo gedit/whereitslocated?

edit:this is pretty hard/and good im having a little fun doing this lol.

---

### Post by ronnielsen1 on 2011-01-17
>  		is that how you edit everyfile by putting gksudo gedit/whereitslocated?

There's other ways too but this way works. 

> You should **never** use normal sudo to start graphical applications as Root. You should use gksudo (kdesudo on *Kubuntu*) to run such programs.  gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by Root. (AFAICT, this is all that's special about the environment of the started process with gksudo vs. sudo). 

gedit is one of many text editors



Any Luck?

---

### Post by elmonkey009 on 2011-01-17
> **ronnielsen1 said:**
> There's other ways too but this way works. 



gedit is one of many text editors



Any Luck?

nope no luck. i did somehow did something last night that gave me 2hr and 40-50min forgot what i did either way everything got deleted on what i  did cause i turned on today and now it randomly drops to about 2hours.

---

