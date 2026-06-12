---
title: "multiple instances of conky?"
date: 2008-08-10
forum: General Help
---

### Post by wirelessfree on 2008-08-10
Hello

I have one instance of conky set up and running on my desktop with which I'm very happy.  

I would like to run another with a calendar and clock in another location.  Looking this up I found the following thread:

**thefatmoop**
February 11th, 2008, 05:24 PM
So i have a conky pre-written script that i remade... but it's taking up a good deal of space, is it possible to have another conky area that will be in a different corner of my screen?

i want to display a part of
tail -f /var/log/syslog
obviously i'll truncate it in the conky config

**notwen**
February 11th, 2008, 05:35 PM
create your conky configs

ie. conkyrc1 & conkyrc2

then simply start them using:

conky -c conkyrc1
conky -c conkyrc2


However, when I follow this instruction although I do get two instances of conky they don't stay on the desktop at the same time.  One is visible for a few seconds and then disappears while the other one reappears.

I have tried giving both instances separate locations but that seems to make no difference.


Hope somebody can help.
Thanks

---

### Post by oni5115 on 2008-08-10
hmmm try:
conky -c conkyrc1 &
conky -c conkyrc2 &

or:
conky -dc conkyrc1 
conky -dc conkyrc2 

or both at once:
conky -dc conkyrc1 &
conky -dc conkyrc2 &


The -d should daemonize it, make it run in the background.  The & should do the same thing, at least in a shell script. (I think!)  Either should work if you're using a shell script to start conky up on session load.

---

### Post by DocYoung on 2008-08-10
I have mine run on startup with a .sh.

Called dual_conky.sh
```

#!/bin/bash

sleep 9 &&
conky -d -c /home/odin/.conkyrc &
sleep 9 &&
conky -d -c /home/odin/scripts/conky_two &
exit


```
(BTW it waits 9 seconds before starting (sleep 9))
I have my logs tailed with these lines

```

${color #e9c703}System Logs

${color #e9c703}Messages
$color${execi 30 /usr/bin/tail -n 5 /var/log/messages | cut -c 23-}

${color #e9c703}Security
$color${execi 30 /usr/bin/tail -n 5 /var/log/auth.log | cut -c 23-}

${color #e9c703}System
$color${execi 30 /usr/bin/tail -n 5 /var/log/syslog | cut -c 23-}

```

I'm by no means a code ninja so someone else may have a better way of doing things.

---

### Post by wirelessfree on 2008-08-11
Hi

Thanks for responding.

But unfortunately neither of these things worked for me. I tried adding the -d switch (with or without &) didn't work.

**DocYoung** I copied your script and amended it for my own setup.  It launched two instances of conky but again I still have the same problem.

They both launch.  One instance will be visible for a few seconds then disappear, at which point the other instance will appear for a few seconds.  They are never on screen together.


I tried changing the update intervals to see if made any difference, it didn't.


As another thought, at the moment they are both set to:

own_window no

So that means they are drawing directly to the desktop, doesn't it?  Would it make any difference if they both appeared in their own window?

Thanks

---

### Post by DocYoung on 2008-08-11
Both of mine are set to own_window yes.

---

### Post by bionnaki on 2008-11-03
any luck?

---

### Post by j.scott.gwin on 2010-06-02
you don't need two instances of conky.  you just need to use ${voffset 12345} to make another column.  google for conky hardcore; there are plenty of examples.

---

### Post by stinkeye on 2010-06-02
```
own_window no
```
is your problem

---

