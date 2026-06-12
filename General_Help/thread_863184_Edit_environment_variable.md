---
title: "Edit environment variable"
date: 2008-07-18
forum: General Help
---

### Post by soorjithp on 2008-07-18
Dear All,

Anyone know how to edit the environment variable?

```
soorjith@core:~$ env
SSH_AGENT_PID=2814
TERM=xterm
DESKTOP_STARTUP_ID=
SHELL=/bin/bash
GTK_RC_FILES=/etc/gtk/gtkrc:/home/soorjith/.gtkrc-1.2-gnome2
WINDOWID=39845989
OLDPWD=/home/soorjith/test
USER=soorjith
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.ogg=01;35:*.mp3=01;35:*.wav=01;35::*.py=01;42:
GNOME_KEYRING_SOCKET=/tmp/keyring-APtGRv/socket
SSH_AUTH_SOCK=/tmp/ssh-YejjeV2769/agent.2769
SESSION_MANAGER=local/core.com:/tmp/.ICE-unix/2769
USERNAME=soorjith
XPSERVERLIST=
DESKTOP_SESSION=default
PATH=~/bin:~/bin:/usr/local/bin:/usr/bin:/bin:/usr/bin/X11:/usr/games
GDM_XSERVER_LOCATION=local
PWD=/home/soorjith
LANG=en_US
GDMSESSION=default
HOME=/home/soorjith
SHLVL=1
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=soorjith
DISPLAY=:0.0
COLORTERM=gnome-terminal
XAUTHORITY=/home/soorjith/.Xauthority
_=/usr/bin/env

```


I tried to add a seperate color for all .py files by applying the command LS_COLORS="${LS_COLORS}:*.py=01;42:", but it will work only in that terminal where we execute the command.

Then I tried to edit .bashrc by adding this command, then after in all terminal, .py files list as a seperate color.

I would like to know any other ways to edit the environment variables (either by using any command or by editing any files)?

Thankin you
Soorjith P

---

### Post by ghostdog74 on 2008-07-18
just assign a new value to it, what's wrong?
```

SHELL=/bin/tcsh

```

---

### Post by pauper on 2008-07-18
Did you use "export" before variable in .bashrc?

```
echo "export LS_COLORS="${LS_COLORS}:*.py=01;42:"" >> ~/.bashrc

```

Run this command afterwards to make bash reread configs.

```
bash
```

---

### Post by soorjithp on 2008-07-18
> **pauper said:**
> Did you use "export" before variable in .bashrc?

```
echo "export LS_COLORS="${LS_COLORS}:*.py=01;42:"" >> ~/.bashrc

```

Run this command afterwards to make bash reread configs.

```
bash
```

I have edited the .bashrc file by appending this line last (using vi) and then execute the command
 
```
. .bashrc
```

---

