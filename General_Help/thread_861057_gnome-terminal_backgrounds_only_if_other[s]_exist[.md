---
title: "gnome-terminal backgrounds only if other[s] exist[s]"
date: 2008-07-16
forum: General Help
---

### Post by gfixler on 2008-07-16
I just made a handy CCSM+Devil's Pie combination that lets me hit Shift+Ctrl+Alt+b to pop up 3 shells with the *-t name*, naming them shellA, shellB, and shellC. I have a devilspie .ds file that finds these windows by title, and fullscreens them to each of my 3 displays. It's neat to go full-terminals on a particular desktop, and the 'above' command in the devilspie expression ensures they stay even above the panels always.

However, I've noticed an interesting characteristic. If I have a shell open anywhere - current, or other desktop - then all 3 will pop up. If I don't have any other gnome-terminals anywhere, then it will wait on the first one, until I kill it, at which point the second will pop up. Once I kill *it*, the third will pop up. I can kill them all, pop up a terminal, and then run my hotkey again, and all will pop up.

Anyone know exactly why this is? I can hack around it, I'm sure, but I'd rather have a somewhat elegant solution. Maybe I'm missing a flag, or something obvious? Thanks!

---

### Post by pauper on 2008-07-18
The latest Devil's Pie version:

[http://www.burtonini.com/computing/devilspie-0.22.tar.gz](http://www.burtonini.com/computing/devilspie-0.22.tar.gz)

GUI editor for Devil's Pie:

[http://code.google.com/p/gdevilspie/downloads/list](http://code.google.com/p/gdevilspie/downloads/list)

Make Devil's Pie daemon run at startup.

System--Preferences--Sessions--Startup Programs

Add new entry:

Name: devilspie
Command: devilspie -a

Mine xterm.ds config:

```
$ cat $HOME/.devilspie/xterm.ds
; generated_rule xterm
( if 
( and 
( is ( application_name ) "xterm" )
) 
( begin 
( undecorate )
( focus )
( maximize )
( set_workspace 3 )
( println "match" )
)
)
```

Now start xterm on Desk 3 and switch there. I find the best practice is to
bind this command to a key sequence, such as Shift+Alt+x.

```
xterm & wmctrl -s 2
```

Note: You will have to install wmctrl first.

If I need [color=red]another[/color] xterm I could press Shift+Alt+x again or use "screen"
instead (read "man screen") with my custom .screenrc, where I defined to
launch several other programs at startup:

```
$ cat $HOME/.screenrc | head
screen -t man 0 bash

screen -t bash 1 bash

screen -t bash 2 bash

screen -t vim 3 vim

screen -t cmus 4 cmus
```

---

