---
title: "Microtouch Serial Touchscreen Works But...."
date: 2012-01-21
forum: Hardware
---

### Post by mightybuddha on 2012-01-21
Hi Chaps,

I'm using a microtouch serial touchscreen with Ubuntu 11.10 + Gnome3 on a laptop with a generic type II pc card serial adapter.  

First I tried getting them to work on earlier versions though had problems, but the newest kernel recognises them automatically and so no problem :)

(for anyone interested here is a vid of it running)
[http://www.youtube.com/watch?v=ofLZkkrR-Ws](http://www.youtube.com/watch?v=ofLZkkrR-Ws)

It was easy to get the touchscreen working once I identified the serial port.  All that was needed was to enter

```
sudo inputattach -mtouch /dev/ttyS4
```into the terminal, then to get it to run on startup I entered

```
inputattach -mtouch /dev/ttyS4
```into /etc/rc.local

Only problem is, the touchscreen only runs if I am touching the screen during boot!  If I'm not touching the screen then even entering the command into the terminal later doesn't start it.  just says something like device not recognised.

Not sure what the problem is here.  I can live with it, but would be nice if there was a fix :)

any ideas?

Cheers!

---

### Post by mightybuddha on 2012-01-24
been doing a bit of scouting around and it seems the problem may be related to inputattach.

There was (what should be) an old bug in inputattach that would cause the device to fail upon a suspend/resume cycle.  This should have been fixed in the most recent version of inputattach, though I can confirm that my touchscreen also fails on suspend/resume.

Any ideas where to go from here?

Cheers!

---

### Post by mightybuddha on 2012-01-24
partially solved.

I found the rc.local file is loaded too early and so the inputattach command doesn't take effect.

To fix this I changed my line in rc.local to

```
sleep 10 && inputattach -mtouch /dev/ttyS4
```and now the touchscreen works automatically at startup. :D :D :D

But still doesn't work after sleep/resume :(

any help in this area would be much appreciated!

---

### Post by mightybuddha on 2012-01-26
SOLVED!

I added this script to an empty file marked as allow as executable in /etc/pm/sleep.d

> #!/bin/bash 

#suspend_inputattach() {
#    inputattach automatically stops on suspend, so no need
#    usr/sbin/inputattach
#}
 resume_inputattach() {
# restart input attach program
[COLOR=#FF0000]sleep 10s && inputattach -mtouch /dev/ttyS4 &[/COLOR]
}
 case &#8220;$1&#8243; in
thaw|resume)
resume_inputattach
;;
*)
;;
esac
 exit $?


---

