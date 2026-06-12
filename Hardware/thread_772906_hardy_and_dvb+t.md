---
title: "hardy and dvb+t"
date: 2008-04-28
forum: Hardware
---

### Post by mazy haze on 2008-04-28
I've got a haupauge nova-t usb stick for watching dvb-t. I bought that one some weeks ago and got it running under gutsy in about no time (there are lots of tutorials around here that end up to be all the same - get v4l-dvb source, make, make install, copy firmware, done). So today I upgraded to hardy and the dvb card is no longer recognized. So, I checked for the firmware, it's still there. It was even copied from /lib/firmware/2.6.22* to /lib/firmware/2.6.24*. So I recompiled v4l-dvb. Still no changes. Than I downloaded the firmware, again. And again, no changes. So that's pretty annoying. If someone has got a good advice, I would be very thankful.

dmesg (this should be something else):
```
[  387.719253] usb 7-2: new high speed USB device using ehci_hcd and address 5
[  387.808670] usb 7-2: configuration #1 chosen from 1 choice
```

lsusb:
```
Bus 007 Device 005: ID 2040:7070 Hauppauge

```

---

### Post by mazy haze on 2008-04-28
make distclean did the trick.

---

### Post by tqft on 2008-04-28
This sounds like exactly my problem - make distclean where?

I haven't check this "/lib/firmware/2.6.22* to /lib/firmware/2.6.24*. "

I followed these directions (which worked under gutsy 2 weeks ago) again:
[http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/](http://www.itee.uq.edu.au/~chrisp/Linux-DVB/DVICO/)

I reinstalled the (kernel?) drivers under hardy and lsmod is showing the entries.  I am getting some errors on reboot - I figured with the card kernel drivers back in restarting the machine will get the firmware reloaded (yes I know there is another way without restarting - link please - but restart is dead simple and hard to argue with).

recopy the firmware and make distclean in /lib/firmware ?

I will double check the firmware is where it should be when I get home.

---

### Post by tqft on 2008-05-02
This post is mostly for reference by me in case it stuffs up again and for anyone else out there with the same porblem.

Did make dist distclean on the xc-test (aka v4l-dvb source for my tuner and installed).  No luck.

On boot Hardy-generic was complaining about registers not being there when going through

after I compiled my own kernel and did make distclean again and reinstalled for new kernel - working.

At a guess looking at the errors and such (I can grab the errors from syslog if anyone cares) - the v4l-dvb only saw the x386 kernel even though it should have a seen an x686 kernel.  Curiously "uname -r" was reporting an SMP kernel (I remember that).

Possibly related to upgrade not going smoothly.
Next up - audio (of the pulse type I suspect).

---

