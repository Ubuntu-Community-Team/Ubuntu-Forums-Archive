---
title: "xscreensaver: Unable to lock screen during suspend"
date: 2010-11-14
forum: Hardware
---

### Post by akshayas1986 on 2010-11-14
Hey guys

I removed gnome-screensaver and I am running only xscreensaver. xscreensaver does not have an option to lock screen after suspend. It has an option to lock screen after X minutes but not to lock for suspend and resume. Any fixes for this?

I have tried to use this script sleep.sh in /etc/pm/sleep.d/
```

#!/bin/bash
if [ -n "$1" ] && ([ "$1" = "resume" ] || [ "$1" = "thaw" ]); then
        /usr/bin/xscreensaver-command --lock &
fi

```

I know this script is executed and so is the "if-fi" condition but somehow the screen lock command seems to be overwritten and I get my desktop on resume without being asked for username and password.

Any suggestions?

---

