---
title: "scripting: run command on process termination"
date: 2008-11-16
forum: General Help
---

### Post by stealthc on 2008-11-16
Hi, I'm trying to deactivate the screen saver,
then run a piece of software (stepmania, because the screen saver screws it up it must be deactivated),
then reactivate the screen saver when I'm done with it.

how can I do this?

Here is the script which I am using:
#!/bin/bash

gnome-screensaver-command --exit
cd /
cd StepMania
./stepmania
gnome-screensaver

---

### Post by stealthc on 2008-11-16
Found an article after trying a different search so I have a new script... I'll let people know if this works fully.  It seems to but I don't know if stepmania will still freeze up or not....

#!/bin/bash

echo Stopping screen saver...
gnome-screensaver-command --exit
cd /
cd StepMania
echo Running StepMania...
./stepmania
CMDNAME='stepmania'
RESTARTCMD='gnome-screensaver'
RESTARTCMDA='exit'
SLEEPTIME=5
while test 1
do
OUTPUT=`ps ax | grep $CMDNAME | grep -v grep`
if ! echo $OUTPUT | grep $CMDNAME 1>/dev/null ; then
echo Restarting screen saver...
$RESTARTCMD
$RESTARTCMDA
fi
sleep $SLEEPTIME
done

---

### Post by stealthc on 2008-11-16
works likes a charm -->I'm gunna post that little script over on stepmania forums for people should help them out with that glitch I was annoyed with where the keys would suddenly stop working (excluding tab).

---

