---
title: "No control in desktop"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by chmosbrook on 2009-01-11
I just did a clean install on a compaq f730us. after I boot, the desktop appears frozen. I am able to switch to shell by hitting alt f6 and use the key board. When I switch back, I have no control.

Every thing functions with livecd.

Any ideas?
Thanks

---

### Post by ajmorris on 2009-01-12
hi there,
First, before a debug of your issue, a test to see if the whole of your Xorg freezes... when it freezes, can you issue ctrl+alt+backspace to restart X, and go back to your login manager?

Also, after the freeze, can you switch to a TTY session, and get the output of dmesg, then paste it to a reply once back in an xsession. The easiest way to accomplish this, is to run:
```
sudo dmesg > dmesg
```
This will send the output from the dmesg command to a file called 'dmesg' in the directory from which you issued the command.
When pasting the output from dmesg, please use [code] envelops around the output, as it will be very long.


AJ

---

