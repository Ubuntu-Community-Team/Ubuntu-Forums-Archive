---
title: "Compaq Netbook mini 702EA, USB mice broken."
date: 2010-01-21
forum: Hardware
---

### Post by ezebe on 2010-01-21
I was really happy with Karmic on my Compaq Mini 702EA - all working fine with speaker bugs fixed in the update and wireless never a problem.  

After an update sometime around Christmas 2009, my USB mouse started became unusable - after ~30 secs of being plugged in, working normally, became really intermittently responsive, moving across the screen only in small jerks, more happy to move horizontally, and almost impossible to move down.  Clicks would work only occasionally. Reboot gives another 30 secs grace only. 

Tried another USB mouse (this one wireless), initially would connect well, work well for 10 secs then stop completely, after a few tries now cannot connect at all. 

Other USB functions like flashdisks, scanner, printer work well.  Touchpad works flawlessly. Have tried selecting different kernels on bootup, but the earliest ones neither touchpad nor mouse work, more recent ones show same prob.  Have tried fiddling with mouse settings GUI to no effect.

Would really appreciate some help with this as it's my main machine and I hate using the touchpad all the time.

Thanks!

Zac

---

### Post by ezebe on 2010-01-21
lsusb gives

> zac@cityfox:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 10f1:1a08  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 007: ID 062a:6301 Creative Labs 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13d3:3249 IMC Networks 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
zac@cityfox:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 10f1:1a08  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 008: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13d3:3249 IMC Networks 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The top one being for the wireless mouse that doesn't work at all, the bottom for the wired one that is unusable but can (just) move the pointer.  Nothing else is plugged in and the machine has only 2 USB sockets.

I don't know what else to try, and am losing hope that the next update will fix everything...
Z

---

### Post by ezebe on 2010-01-21
I had a look at some log files, but have no idea what they mean.  Kern.log is doing a lot, I've summarised what seem to be exciting bits but can post the whole file if needed...
Z

---

### Post by ezebe on 2010-01-21
here's another relevant-looking log...

---

### Post by ezebe on 2010-01-26
Success - after some updates, the wireless one started working again - the wired is still playing up, but is likely a problem with the mouse itself i think...

---

