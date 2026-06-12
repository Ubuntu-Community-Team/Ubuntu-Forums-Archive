---
title: "Fn keys doesn't work immediatelly"
date: 2012-07-31
forum: Hardware
---

### Post by icegood on 2012-07-31
There is an interval between key pressing and acpi_listen showing/actually working, that takes
> 3sec, could be even more. What could it be? In which queue those keys are standed?

---

### Post by icegood on 2012-07-31
Which actually runlevel started after i press acpi button? Or it isn't runlevel question at all? 
Cannot understant services events/dependencies . Is init in kubuntu event-based or dependency-based?
man init(8) says that it's an event-based...
Simply found that in
```

case "$1" in
    start)
        start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
    sleep 60 # probably enough time for desktop login

```ondemand doesn't seem to work only on login event. So 60 sec wait possible after.

For now light up/down both have ~16sec latency. Screen off/on takes 12/28 sec respectivetly.

---

### Post by icegood on 2012-07-31
damn still noone? Noone has same issue?

---

### Post by icegood on 2012-08-06
Found that after suspending my laptop via pm-suspend in command line and resuming with any key everything works great.

---

