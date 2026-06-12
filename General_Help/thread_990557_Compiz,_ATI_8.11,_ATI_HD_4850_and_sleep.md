---
title: "Compiz, ATI 8.11, ATI HD 4850 and sleep"
date: 2008-11-22
forum: General Help
---

### Post by keypox on 2008-11-22
Can you get sleep to work with Compiz?  I am running the newest ati driver installed via the ATI installer, nothing special.  

Sleep works great with effects disabled but not with effects on.  Anyway to fix this? 

Running ubuntu 8.04

---

### Post by DagMan on 2008-12-01
I did something like the this.

change /usr/lib/pm-utils/sleep.d/00clear to look like this
```
#!/bin/sh
# Ensure we eare in text mode by switching to an unused vt.
# Also avoids lots of ghastly suspend/resume errors due to trying
# to suspend/resume while running in X.

. "${PM_FUNCTIONS}"

case "$1" in
	hibernate|suspend)
                     killall compiz compiz.real
		fgconsole |savestate console
		chvt 63
		;;
	thaw|resume) 
		state_exists console || exit 1
		chvt $(restorestate console) 
		deallocvt 63
                     killall compiz-sleep
		;;
	*)
		;;
esac

```
I've indented what I added in the above.

Then
```
cd /usr/local/bin
sudo ln -s `which sleep` compiz-sleep
sudo nano -w compiz-wakeup
```

and paste this in
```
#!/bin/bash

compiz-sleep 500d

compiz & disown

compiz-wakeup & disown

```

Edit, sorry:
```
chmod +x compiz-wakeup
```

Then you'lle need to add **compiz-wakeup** to start at login.

It kills compiz first thing on suspend, then the roundabout way of restarting it ensures that it isn't running as root (as long as compiz-wakeup isn't started as root initially) and that it doesn't get confused about which message bus to use in case its an issue.  I don't know if it is, and I'm sure there's an easier way to restart it even if it was one, but I don't know what it is.  This has worked well for me... or did until the driver updates didn't really let me suspend reliably anymore ;)

---

### Post by keypox on 2009-02-01
thanks man i will try this...

---

