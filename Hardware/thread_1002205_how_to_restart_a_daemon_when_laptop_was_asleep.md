---
title: "how to restart a daemon when laptop was asleep"
date: 2008-12-04
forum: Hardware
---

### Post by phorminx on 2008-12-04
I like to use syndaemon to deactivate the touchpad when I am writing. Yet when I put the laptop asleep and wake it up again, syndaemon is gone. Is this a bug? If yes of what? If it's normal that such a daemon dies, how can I restart it automatically when the laptop wakes up?

Thanks

---

### Post by sdennie on 2008-12-04
I don't know if it's a bug or not but, try using the following script:

```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    thaw|resume)
        DISPLAY=:0.0 su **your_username** -c **"whatever_command_you_want_to_run"**
    ;;
esac

exit 

```

Call it 01-syndaemon and install it with:

```

sudo install 01-syndaemon /etc/pm/sleep.d/

```

I have no way to test that but, it should run the command you want when the make wakes up.

---

### Post by phorminx on 2008-12-04
I see, thanks a lot. -- I am still in the process of familarizing myself with setting up such things. With your approach, I will have two pieces of code for syndaemon, one for starting it initially at the beginning of an X session, and a second piece for restarting it when the laptop wakes up. Is it also possible to use one script for both?

Currently I am simply using the gnome session preferences tool to start syndaemon initially. But I guess that more complex tasks of that kind are better handled by means of a script in /etc/init.d/. So my question is really about the relation between scripts in /etc/init.d/ and /etc/pm/.

Ooops, I guess there is actually a difference between scripts in /etc/inint.d (run when the computer reaches a certain run level) and using the gnome session preferences tool which will run my code when I start the X session while the X server is already running. Is that right?

Thanks!

---

