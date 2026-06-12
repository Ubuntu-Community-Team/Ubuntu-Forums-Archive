---
title: "[SOLVED] how to properly use the kill command"
date: 2008-09-23
forum: General Help
---

### Post by Kain000 on 2008-09-23
hello everyone i'm trying to write a script for someone on the forum that wants to stop compiz, and start a game without manually stoping compiz.

so far all I have is 

```
#script for shutting down compiz and starting _____(game 'o' choice)
#!/bin/bash

kill #(process Id of compiz)
#insert the games command (most likely found in /usr/bin)
gamecommand

stop
```

BUT.....   It doesnt make since to use the process ID as you would have to look up the process Id each time to kill it, and edit the script, by witch time you could have manually stopped compiz manualy.   So...  i'm not sure how else to stop a process other than kill ....... process id.

So is there any way to stop compiz (or any other process for that matter) by using it's name or somthing constant rather than it's process ID that changes each time it's started?

thankyou
-sean

---

### Post by ghostdog74 on 2008-09-23
look up man pkill. it can kill by name.

---

### Post by RequinB4 on 2008-09-23
```

#!/bin/sh
metacity --replace
uberpwnagegame
compiz --replace

```

---

### Post by skralljt on 2008-09-23
Likely the older solutions are more appropriate but I find the killall programname command to be indispensable and it sounds like it would do what you want.

---

### Post by Kain000 on 2008-09-25
Thanks everyone for your help,

> **RequinB4 said:**
> ```

#!/bin/sh
metacity --replace
uberpwnagegame
compiz --replace

```

Question, on your above script I run it as is replacing the middle line with a game command ofcourse, and I get as far as metacity --replace, and the program stops.

when run allone in the terminal the replace command doesnt finish.  what do I need to do to make it finish?   
I've tried the wait command after the metacity replace command witch should wait until the previous command finishes before starting the game command, however it never gets that far.

any ideas?

---

### Post by Kain000 on 2008-09-25
> **ghostdog74 said:**
> look up man pkill. it can kill by name.
That seems like it would work and finish, but wouldnt I need a window manager active for the time between kill and start?

---

### Post by RequinB4 on 2008-09-25
> **Kain000 said:**
> Thanks everyone for your help,



Question, on your above script I run it as is replacing the middle line with a game command ofcourse, and I get as far as metacity --replace, and the program stops.

when run allone in the terminal the replace command doesnt finish.  what do I need to do to make it finish?   
I've tried the wait command after the metacity replace command witch should wait until the previous command finishes before starting the game command, however it never gets that far.

any ideas?

MY BAD: you need to use this instead:

```

#!/bin/sh
metacity --replace &
uberpwnagegame
compiz --replace &

```

---

