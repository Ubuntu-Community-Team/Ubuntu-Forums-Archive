---
title: "Ubuntu 8.10 hangs out on shut down"
date: 2008-10-31
forum: General Help
---

### Post by jpmelos on 2008-10-31
Hi. I downloaded Ubuntu 8.10 and installed it. It's fully updated and hangs out on Shut Down and Restart procedure (haven't tested the others). First, it comes in a blank screen with a blinking cursor (after the orange bar when down about 40%), and when I hit the power button, it goes back to the orange bar, full, and begins again, but shows in screen:

Saving clock time...
Turning off firewall:          [ OK ]
Shutting down ALSA:            _

Or something like that... And hangs there for ever.

Any help, please?

Thank you. Bye.

---

### Post by kd420 on 2008-10-31
Hi,

    I had the same problem with 8.10, and have found a workaround/fix using this thread:

[https://bugs.launchpad.net/ubuntu/+bug/274995](https://bugs.launchpad.net/ubuntu/+bug/274995)

I simply edited this file:

/etc/init.d/alsa-utils

and added the lines:

ifconfig wlan0 down
ifconfig eth0 down

after "stop)" in the file (around line 353), so it looks like this:


stop)
	ifconfig wlan0 down
	ifconfig eth0 down
	EXITSTATUS=0


etc...

This worked fine for me, but you might have to change it depending on what internet devices you use. If you have problems/want more clarification I'd look into that bug report because this fix did not work for everyone.

---

### Post by jpmelos on 2008-10-31
Thank you very much! I'll test it tomorrow and I'll report back. :)

---

### Post by dootzky on 2008-11-01
dude!! it works!! :)

I had the exact same problem, when shutting down - it just freezes on "ALSA", but now with the instructions which "kd420" gave us - IT'S SHUTTING DOWN NORMALLY AGAIN!!! :) :) :)

thanks a million mate!!
cheers,
dootzky

---

### Post by alfoso on 2008-11-03
Thanks, this fix worked for me.
I had the same problem running Ubuntu 8.10 in a VM using VMware Fusion 2.0 on a Macbook Pro.

---

### Post by Jim_in_Germany on 2008-11-13
Worked for me too. Thanks a lot!!

---

### Post by dmacdonald on 2008-12-02
Confirmed:  Fixed a handful of PCs running the latest distro/kernel by adding the above suggested changes.  Much appreciated.

---

