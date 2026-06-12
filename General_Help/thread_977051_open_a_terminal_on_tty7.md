---
title: "open a terminal on tty7"
date: 2008-11-09
forum: General Help
---

### Post by tropicflite on 2008-11-09
I let my son use my Ubuntu computer using my sign-in when I'm at work.  Sometimes I want to pop up a terminal on his tty7 so that I can use "write" to send him a message.  I can ssh into the home computer, but I can't figure out how to pop up the terminal so that he gets the message.

Does anyone else know?

TIA

---

### Post by -Zeus- on 2008-11-09
> **tropicflite said:**
> I let my son use my Ubuntu computer using my sign-in when I'm at work.  Sometimes I want to pop up a terminal on his tty7 so that I can use "write" to send him a message.  I can ssh into the home computer, but I can't figure out how to pop up the terminal so that he gets the message.

Does anyone else know?

TIA

well, for starters, writing to tty7 won't show up.  You need to use something like pts/1.  to start a terminal, just typing gnome-terminal & should start one on his end if x11 forwarding is off.

---

### Post by tropicflite on 2008-11-09
> **-Zeus- said:**
> well, for starters, writing to tty7 won't show up.  You need to use something like pts/1.  to start a terminal, just typing gnome-terminal & should start one on his end if x11 forwarding is off.

Thanks for the reply.  I tried what you said, and I got:

dad@ubuntu:~$ gnome-terminal &
Cannot open display: 
[1] 12907
dad@ubuntu:~$ Run 'gnome-terminal --help' to see a full list of available command line options.

I looked through the options but I didn't see anything helpful.  Any other ideas?

---

### Post by bodhi.zazen on 2008-11-09
See if either of these threads help :

[http://ubuntuforums.org/showthread.php?&t=411622](http://ubuntuforums.org/showthread.php?&t=411622)

		See also [http://ubuntuforums.org/showthread.php?t=504351](http://ubuntuforums.org/showthread.php?t=504351)

If so, use xmessage or zenity instead of write.

ex:

```
xmessage " This is a test"
```

---

### Post by tropicflite on 2008-11-09
OK, following your links, I made a script named forward.sh which looks like this:

#!/bin/bash
XAUTHORITY=/home/dad/.Xauthority
export XAUTHORITY
DISPLAY=:0
export DISPLAY
$1

I did a chmod +x on it, and now when I ssh into my home box, I can start pidgin like this:

./forward.sh pidgin

and that does just what I want.

Thanks for your help!  That was quick!

---

### Post by tropicflite on 2008-11-10
.

---

### Post by bucsaradu on 2010-03-16
#!/bin/bash
XAUTHORITY=/home/dad/.Xauthority
export XAUTHORITY
DISPLAY=:0
export DISPLAY
$1

Works for me too. Thank you all.

---

### Post by FracturedMind on 2011-07-08
if anybody is still paying attention to this post

when i do this, i have to open another terminal and ssh in again in order to run any further commands as the terminal waits for the command to finish. is there any way to get it to not do this.

ie:
me@my-netbook:~$ ssh me@my-desktop
me@my-desktop:~$ ./forward.sh gnome-terminal
 (and then it waits for ^C)

---

### Post by bodhi.zazen on 2011-07-08
> **FracturedMind said:**
> if anybody is still paying attention to this post

when i do this, i have to open another terminal and ssh in again in order to run any further commands as the terminal waits for the command to finish. is there any way to get it to not do this.

ie:
me@my-netbook:~$ ssh me@my-desktop
me@my-desktop:~$ ./forward.sh gnome-terminal
 (and then it waits for ^C)

This is an old thread. In the future you really should start your own new thread rather then hijacking an old one ;)

use a & at the end ;)

command 1 &
command 2 &

You may also want to look at applications like screen and using nohup ;)

(nohup command 1 &)

See also man ssh as there are several options for ssh .

---

