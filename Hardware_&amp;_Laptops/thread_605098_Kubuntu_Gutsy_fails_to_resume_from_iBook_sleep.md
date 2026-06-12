---
title: "Kubuntu Gutsy fails to resume from iBook sleep"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by jettlogic on 2007-11-06
After I upgraded Kubuntu Feisty to Gutsy, the iBook G4 would not come back from sleep (but not quite like 
[http://ohioloco.ubuntuforums.org/showthread.php?t=30247](http://ohioloco.ubuntuforums.org/showthread.php?t=30247))

I close the lid (or do pbbuttonsd "pbbcmd sleep", or "/usr/lib/hal/hal-system-power-pmu sleep")  It takes a second to go to sleep, and the sleep light comes on.  I open the lid, the hard drive spins up, and *POOF* -- blackness (it *should* make a few more noises and give me a locked screen prompt).   

However, resuming works find in the console, so the problem has a relation to X.

Update: the bug appears to be here:  
[https://bugs.launchpad.net/ubuntu/+bug/144305](https://bugs.launchpad.net/ubuntu/+bug/144305)

However, the patch by John Steel *does not work for me* either when closing the lid, or by calling /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux directly, which means that its failing to change the console.

Adding Benjamin Herrenschmidt's scripts however did work:

- console-switch-out (in suspend.d):

#!/bin/sh

# And remember which console we're on
fgconsole >/tmp/saved-fg-console

# Change away from X, otherwise it'll blow up when we POST the video interface
chvt 12

- console-switch-in (in resume.d):

#!/bin/sh

CONSOLE=`cat /tmp/saved-fg-console`
rm /tmp/saved-fg-console
chvt $CONSOLE

---

