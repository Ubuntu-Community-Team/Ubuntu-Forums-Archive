---
title: "ctrl+alt+del"
date: 2008-07-30
forum: General Help
---

### Post by tejaka on 2008-07-30
Hi

what are the ctrl+alt+del equivalent of linux?

or how can we force to kill frozen applications?....

Thanks...

---

### Post by perlluver on 2008-07-30
To kill an application just hit the exit button a couple of times, and it will ask if you want to terminate the program.

Or you can open up system monitor, and find the application and kill it.

---

### Post by kerryhall on 2008-07-30
To do a quick reboot of X, you can use ctrl+alt+backspace. However, a word of warning: this will kill any applications you have open, and won't ask you if you want to save your work!

---

### Post by wcunkefe on 2008-07-30
does ctrl+alt+backspace reboot X or just kill it?  It is my experience that you are left with a terminal and you would actually have to type something like: 
```
sudo killall gdm
sudo /etc/init.d/gdm start
```

---

### Post by geirha on 2008-07-30
> **wcunkefe said:**
> does ctrl+alt+backspace reboot X or just kill it?  It is my experience that you are left with a terminal and you would actually have to type something like: 
```
sudo killall gdm
sudo /etc/init.d/gdm start
```

It should kill X and gdm, and a new gdm should be spawned automagically. If this doesn't happen for you, then I would suggest reporting it as a bug on launchpad (if there isn't one allready)

---

### Post by drs305 on 2008-07-30
For a gui equivalent, you can add a "Force Quit" shortcut to the panel - right click on the Panel, Add, Force Quit. You then click the icon and the next thing you click on is killed.

---

### Post by Ataris on 2008-07-30
If you just want to shut down or log off instead, you can just hit the power button. :P

---

### Post by bks on 2008-07-30
If it is a single application that crashed and you want to close it try
```

sudo xkill

```

and then just click any where inside the applications window. It works fabulously!

---

### Post by Separ on 2008-07-30
For the command line method to find a process and kill it
```
ps -A
kill -9 PID
```
Where PID is the process ID from the list :)

Ctrl+Alt+BkSp restarts X and gdm.

If you want to restart the gdm by command line
```
sudo /etc/init.d/gdm restart
```

---

### Post by tejaka on 2008-08-01
ok

Thank you guys...

can we assign a short cut for system monitor...it monitor far better than win task manager... 

does that require advance procedure?, if yes, better to stay in here...:D...lol....

Thanks in advance...

---

### Post by gjoellee on 2008-08-01
the CTRL+ALT+DEL in Ubuntu gives you the Shut Down windows where you can select logout restart, shutdown, hibernate etc...

---

