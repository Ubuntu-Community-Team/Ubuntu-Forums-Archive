---
title: "Bash script - stopped working=["
date: 2008-08-18
forum: General Help
---

### Post by markeee on 2008-08-18
Hi,

couldn't see anywhere else better suited for this:


```
#!/bin/bash
export DISPLAY=":3"
/usr/bin/firefox -no-remote --display :3 "$1" > /dev/null 2> /dev/null &
/bin/sleep 25

/usr/bin/import -window root -display :3 "$2"

killall firefox-bin
```

24507 pts/0    S      0:00 Xrealvnc :3 


vnc running on :3


mark@dimension:~$ echo $DISPLAY
:3
mark@dimension:~$


The script worked before, i haven't changed anything?!


```
mark@dimension:~$ ./test.sh www.google.co.uk
./test.sh: line 4: 25670 Aborted                 (core dumped) /usr/bin/firefox -no-remote --display :3 "$1" > /dev/null 2> /dev/null
firefox-bin: no process killed
mark@dimension:~$

```

Thanks

---

### Post by markeee on 2008-08-18
someone must have an idea??

---

### Post by amitkher on 2008-08-18
Firefox is crashing. It has nothing to do with your script. Just run the firefox command in isolation to know what is wrong. Remove the /dev/null redirection so you know what firefox is complaining about.

```

/usr/bin/firefox -no-remote --display :3 'www.google.co.uk'

```

---

