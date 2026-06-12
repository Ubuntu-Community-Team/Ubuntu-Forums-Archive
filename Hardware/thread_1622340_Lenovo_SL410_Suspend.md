---
title: "Lenovo SL410 Suspend"
date: 2010-11-15
forum: Hardware
---

### Post by FAJALOU on 2010-11-15
Hello all, 
I recently purchased a Lenovo SL410, and installed 10.04.
I am able to suspend about half of the time, but the other half of the time, suspend fails to work, and the screen only blacks out.  There is no beep, and the computer doesn't effectively enter into suspend mode.  
I have noticed that if I turn of the laptop and turn it back on, sometimes I am able to again enter into a suspended state, and sometimes it will 'just work,' but I don't know how to diagnose it further.  I have tried to see if my internet browser affects the suspend, but it would seem ironic to have to close everything down just in order to suspend (it would kind of defeat the purpose).
To suspend I use the following script 

```
#!/bin/bash/
gnome-screensaver-command --lock
pmi action suspend
```

And linked below is the suspend log, messages, and a log from when I just tried to suspend (Nov. 15th,) and it failed to correctly suspend.  If anything else is needed, I will gladly provide!  I will shortly be adding a suspend success log from pm-suspend.log also.

messages:
[http://paste.ubuntu.com/532454/](http://paste.ubuntu.com/532454/)

pm-suspend.log:
[http://paste.ubuntu.com/532455/](http://paste.ubuntu.com/532455/)

suspend-fail.log:
[http://paste.ubuntu.com/532456/](http://paste.ubuntu.com/532456/)

---

### Post by FAJALOU on 2010-11-15
After a reboot, I tried suspending, and success
pm-suspend.log:
[http://paste.ubuntu.com/532461/](http://paste.ubuntu.com/532461/)

messages:
[http://paste.ubuntu.com/532463/](http://paste.ubuntu.com/532463/)

And another success, with Chromium open (which I thought may be a culprit):
pm-suspend.log:
[http://paste.ubuntu.com/532467/](http://paste.ubuntu.com/532467/)

messages:
[http://paste.ubuntu.com/532468/](http://paste.ubuntu.com/532468/)

syslog:
[http://paste.ubuntu.com/532469/](http://paste.ubuntu.com/532469/)

---

### Post by FAJALOU on 2010-11-27
After the latest round of updates, I attempted to suspend, and same problem as before:

Linux lrc-laptop 2.6.32-26-generic #47-Ubuntu SMP Wed Nov 17 15:59:05 UTC 2010 i686 GNU/Linux

messages:
[http://paste.ubuntu.com/536987/](http://paste.ubuntu.com/536987/)

suspend:
[http://paste.ubuntu.com/536988/](http://paste.ubuntu.com/536988/)

Bump/help?

---

