---
title: "Syndaemon dies after resume"
date: 2015-03-09
forum: Hardware
---

### Post by frytek on 2015-03-09
I have syndaemon -i 1 -d among startup programs to disable touchpad when I type. 

However, after hibernate / resume it is either gone or not doing the job. I have to kill / restart it every time to make it work. 

Any ideas why this happens?

Edit: I just found a solution. 

Create a file in /etc/pm/sleep.d and make it executable (chmod +x) 

Paste this into it. REPLACE **USERNAME** WITH YOUR ACTUAL USER NAME.

```
#!/bin/sh
resume_syndaemon()
{
    if [ ! "$( pidof syndaemon )" ]; then
 export DISPLAY=:0.0
 sudo -u **USERNAME** syndaemon -d -t -i 2
    fi
}

case "$1" in
 thaw|resume)
  resume_syndaemon
  ;;
 *) exit $NA
  ;;
esac
exit 0
```

---

