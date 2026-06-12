---
title: "Touchpad of Toshiba NB305 not working"
date: 2011-05-29
forum: Hardware
---

### Post by uthier on 2011-05-29
Hi,

I'm using a Toshiba NB305 with Ubuntu 11.04. At least 50% of the times I start it up, the touchpad does not work [and doesn't even show up in the System->Preferences->Mouse]. The external mouse works always. When the touchpad does work, I can see the Touchpad tab in the System->Preferences->Mouse..

I don't want to have to carry with me an external mouse, but then I'd have to boot several times, and hope that the touchpad will show up..

Thanks for any help I can get.

---

### Post by webofunni on 2011-05-29
Are you able to see touch pad in cat /proc/bus/input/devices when it is not working ?

---

### Post by uthier on 2011-05-29
No. It's not there. And, of course, it is when it's working.. :-(

---

### Post by webofunni on 2011-05-29
try 

[https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection)

---

### Post by uthier on 2011-05-29
Thanks, I'll check it out right now.

---

### Post by uthier on 2011-06-03
I don't know how to file a problem report. Is there a form to fill-out? Where?

I'm not trying to create a team, or a project. I don't even know if this is a bug, or just a setup problem.

All I know is that on this Toshiba NB305 [I have no idea who is the touchpad manufacturer, probably someone in China..] some of the times I boot up, the touchpad works fine, and continues to do so as long as I'm not shutting the system down. Other times, about 50% of the times it seems, the touchpad is not working at all, and I see no indication [e.g., in /var/log/kern.log] that the system has ever seen it.. :-(

---

### Post by red03golf on 2011-06-03
[COLOR="Silver"]I looked on the synaptics site and found this page:

[http://www.synaptics.com/support/consumer-tips](http://www.synaptics.com/support/consumer-tips)

at the bottom of the page it mentions that linux drivers are available at the two following sites:

[http://compass.com/synaptics/](http://compass.com/synaptics/)
or
[http://www.pdos.lcs.mit.edu/~cananian/Synaptics/](http://www.pdos.lcs.mit.edu/~cananian/Synaptics/)

Hopefully that will provide assistance to some.[/COLOR]

**EDIT:**
These links appear to be dead and useless now - compass.com is parked with no content.

pdos.lcs.mit.edu has dropped the synaptics project.

This is the working link to the last work on the project:
[http://cscott.net/Projects/Synaptics/](http://cscott.net/Projects/Synaptics/)

---

### Post by uthier on 2011-06-03
You think that it is going to be more up to date that what is in 11.04?

---

