---
title: "Help With Gnu Screen"
date: 2008-09-21
forum: General Help
---

### Post by ceno-byte on 2008-09-21
Im wondering if anyone can help me that has Knowledge of GNU screen. I am trying to configure GNU screen to start with 5 programs i use most in the command-line but whenever i start GNU screen only 3 of the 5 programs start im not sure why screen is doing this any and all help will be appreciated im not sure if this will help but i am running debian 4.0 "etch"

here is my .screenrc file

startup_message off
chdir
autodetach on
hardstatus alwayslastline
hardstatus string '%{= kG}[ %{G}%H %{g}][%=%{=kw}%?%-Lw%?%{r}(%{W}%n*%f%t%?(%u)%?%{r})%{w}%?%+Lw%?%?%= %{g}][%{B}%Y-%m-%d %{W}%c %{g}]'
screen -t shell0   0
screen -t links2   1 /usr/bin/links2
screen -t naim     2 /usr/bin/naim
screen -t rtorrent 3 /usr/bin/rtorrent
screen -t cmus     4 /usr/bin/cmus
screen -t MC       5 /usr/bin/mc

---

### Post by ceno-byte on 2008-09-22
UPDATE:: i managed to fix the problem i install finch and all is well now i guess for some reason naim would not play nice with screen so go ahead and delete this thread

---

