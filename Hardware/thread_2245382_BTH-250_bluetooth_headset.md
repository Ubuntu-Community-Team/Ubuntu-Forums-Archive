---
title: "BTH-250 bluetooth headset"
date: 2014-09-23
forum: Hardware
---

### Post by kjetil-fleten on 2014-09-23
I have a problem with a bluetooth headset that pairs fine, but does not show up in the sound system.

The headset is a BTH-250. I don't know if this headset uses A2DP or not, but if it is, then this is probably the bug:
[https://bugs.launchpad.net/ubuntu/+bug/1283003](https://bugs.launchpad.net/ubuntu/+bug/1283003)

Anyway, there is a workaround: If I run 
```
pactl load-module module-bluetooth-discover
```
after the desktop is loaded, then everything works fine.

It's a bit annoying to open a terminal window to run this command, so I would like this to be done by invoking a script after the desktop has been launched. I tried to put a little script in startup programs, but that did not help. Maybe it launch to early compared to blueman, I don't know.

Is there any other good workarounds to automate the launch of the module ? Even with a small delay perhaps ?

---

